---
layout: post
title: "Accessing attributes from has_many :through join models"
guid: "accessing-attributes-from-has-many-through-join-models"
category:
tags: ['rails', 'activerecord']
---
{% include JB/setup %}

I've been trying to help out a bit in the Rails section on [Stack Overflow](http://stackoverflow.com) lately and have noticed a question that has come [up](http://stackoverflow.com/questions/9355458/nested-has-many-through-attributes) [several](http://stackoverflow.com/questions/9290100/making-activerecord-join-model-attributes-available-in-query-results) [times](http://stackoverflow.com/questions/8874702/need-data-from-rails-join-table-has-many-through) lately.

Accessing an attribute from the join model on a has_many :through relationship. For the basics, check out the [Rails guide](http://guides.rubyonrails.org/association_basics.html#the-has_many-through-association) on the subject.

Here's a pretty standard application of this in my awesome Library SAAS app:

{% highlight ruby %}
class Reader < ActiveRecord::Base
  has_many :book_loans
  has_many :books, :through => :book_loans
end

class Book < ActiveRecord::Base
  has_many :book_loans
  has_many :readers, :through => :book_loans
end

class BookLoan < ActiveRecord::Base
  belongs_to :book
  belongs_to :reader
end

class BookController < ApplicationController
  def show
    @book = Book.includes(:readers).find(params[:id])
  end
end
{% endhighlight %}

And on the books#show page we want to show all the people who have checked out a particular book.

{% highlight erb %}
  <%= @book.name %>
  Readers:
  <ul>
    <% @book.readers.each do |reader| %>
      <li><%= reader.name %></li>
    <% end %>
  </ul>
{% endhighlight %}

Now what if I want to add the librarian who checked out the book to them to the page. This is stored as the `librarian` column on the BookLoan model, which we don't actually have access to in the view at the moment.

This is my current solution to the problem, it involves a bit of SQL which might be a little scary for beginners, please leave a comment if you've got a better idea, I may even look into seeing if it's achievable with ARel sometime soon.

{% highlight ruby %}
  class Book < ActiveRecord::Base
    has_many :readers, :through => :book_loans,
             :select => "readers.*, book_loans.book_loan_librarian AS book_loan_librarian"
  end
{% endhighlight %}
{% highlight erb %}
  <% @book.readers.each do |reader| %>
    <li><%= reader.name %> by <%= reader.book_loan_librarian %></li>
  <% end %>
{% endhighlight %}

If anyone has any questions/suggestions feel free to leave a comment or hit me up on Twitter.

**N.B.** I was originally going to use `book_loan.created_at` but ActiveRecord doesn't automatically typecast the extra columns returned which would be a bit out of the scope of this post.

EDIT: In Rails 4+ it would look like this 

{% highlight ruby %}
   has_many :readers, -> { select("readers.*, book_loans.book_loan_librarian AS book_loan_librarian") },
            :through => :book_loans
{% endhighlight %}
