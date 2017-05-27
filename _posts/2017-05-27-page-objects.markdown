---
layout: post
title:  "Page Objects"
date:   2017-05-27 18:00:00 +0100
categories: Testing
---

# Page object pattern

We've been using the excellent F# [Canopy](http://lefthandedgoat.github.io/canopy/) web testing framework at work to ensure our user journeys continue to work. To keep the tests maintainable we have been using the page object pattern.

A page object encapsulates the selectors and functionality of a web page or a web component. This separates the test code from the page specific code, improves readability and keeps page selectors and functionality in one place.

An example of where a page object has made the work easier is for the payment section, instead of writing

```fsharp
"He enters his payment details" &&& fun _ ->
  "#credit-card-number" << "4111111111111111"
  "#expiration-month"   << "01"
  "#expiration-year"    << "20"
  "#cvv"                << "111"
  "#postcode"           << "M1 1AA"
```

we can shield our test from these details and write something that expresses what a user is doing at that point of their journey

```fsharp
"He enters his payment details" &&& fun _ ->
  PagePayment.enterValidPaymentDetails()
```

If the selectors change then we only need to make a change to the page object instead of finding all the tests that use the selector.

## Further reading

[Selenium HQ Wiki](https://github.com/SeleniumHQ/selenium/wiki/PageObjects)

[Martin Fowler's article](https://martinfowler.com/bliki/PageObject.html)