---
layout: post
title: Pxpay - Payment Express for Rails
guid: pxpay-payment-express-for-rails
category:
tagline:
tags: ['rails', 'pxpay']
---

Building websites in NZ invariably leads to integrating our most popular Payment Solution, Payment Express (DPS) over and over again.

Payment Express has two major options when it comes to online payments, the self-hosted version PxPost and the DPS-hosted version PxPay.

If you want to deal with credit card payments yourself using PxPost, the brilliant [ActiveMerchant](http://www.activemerchant.org) has the PxPost gateway built into it.

However, for DPS-hosted payments, I couldn't find any Ruby implementation, so I put one together myself.

I've put together the [Pxpay](http://www.github.com/bradleypriest/pxpay) gem.

Obviously, dealing with payment data is something that has serious repercussions if something goes wrong, so be careful.

With that out of the way let's take a look at how it works.

First things first, make sure you set up a development account with Payment Express [https://www.paymentexpress.com/pxmi/apply](https://www.paymentexpress.com/pxmi/apply)

With that out of the way install the gem and generate the config

This installs the gem and a pxpay.rb initializer to your config folder.

    gem install pxpay
    rails generate pxpay:install

Firstly, make sure you update the initializer file with your credentials and optionally add the success and failure URLs for your app.

PxPay currently requires the `nokogiri` and `rest-client` gems.

    >>require 'nokogiri'
    >>require 'pxpay'

    >>request = Pxpay::Request.new( 1, 12.00 )
      =>#<Pxpay::Request:0x00000101c9a840>

    >>request.url
      => "https://sec2.paymentexpress.com/pxpay/pxpay.aspx?userid=Fake_Dev&amp;request=xxxxxxxxxx"

The Pxpay::Request object takes a unique ID, a price and an optional hash of arguments.

The important options are :url_success and :url_failure.

Other options include :merchant_reference, :currency and :email address.

Check the [documentation](http://http://rubydoc.info/gems/pxpay/frames) for all the options.

In a rails app pass the arguments into PxPay::Request and redirect the customer to the returned URL.

*order.rb*

    def url
      @url = Pxpay::Request.new( id , price, {
        :email => user.email,
        :url_success => "http://example.com/orders/#{id}/success",
        :url_failure => "http://example.com/orders/#{id}/failure"
      })
    end

Payment Express will process the payments then redirect the customer back to either the success or failure URL.

*orders_controller.rb*

    def success
      response = Pxpay::Response.new(params).response
      hash = response.to_hash
      ## Do something with the results hash
    end

N.B. There is a minor caveat here: Payment Express includes a system called fail-proof result notification where as soon as the customer has finished the transaction they will send a background request.

This means your success/failure URL will be hit at least twice for each transaction, so you must allow for this in your code. See [here](http://www.paymentexpress.com/technical_resources/ecommerce_hosted/pxpay.html#ResultNotification%20) for details.

That's pretty much it. Any questions/problems hit me up on [Github](http://github.com/bradleypriest)
