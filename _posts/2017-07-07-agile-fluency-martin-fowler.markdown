---
layout: post
title:  "Agile Fluency with Martin Fowler and Manasi Kulkarni talk - Manchester, UK"
date:   2017-07-08 19:00:00 +0100
categories: Testing
---

# Martin Fowler and Manasi Kulkarni in Manchester

I was lucky enough to get a ticket to a talk by Martin Fowler and Manasi Kulkarni in Manchester on Tuesday. I'm a big fan of Martin's technical writing so was looking forward to hear him speak.

The title was a bit vague **Software Design in the 21st Century**, but Martin explained that he uses this title so he can talk about anything that is relevant at time of the talk. 
[The video is available on Facebook](https://www.facebook.com/ThoughtWorks/videos/1597160533640865/)

## Agile Fluency

The actual topic focused around the [Agile Fluency](https://martinfowler.com/articles/agileFluency.html) model by Diana Larsen and James Shore. It consists of levels ranging from 1 to 4; with the team's level determined by the way they act when under pressure. The team normally passes through the levels in order:

* Level 1 (*) - Team focus on business value using methods such as Scrum and Kanban
* Level 2 (**) - Team ships at market cadence by being able to ship when the market is ready, by utilising Extreme Programming techniques such as continuous integration and test-driven development
* Level 3 (***) - Team provide concrete business metrics by understanding market needs, business needs and how to fulfil both
* Level 4 (****) - Team reports how its actions impact the organisation - they will work with other teams and managers to maximise value to the organisation supporting the product/task that will produce the most value

## Unit testing - Classical vs Mockist

An additional topic discussed was **classical** vs **mockist** unit testing techniques. **Classical** is where fakes are only used when the collaborator would make the test slow or complicated, such as a database or external API; with the actual implementation of the collaborating units used in the test most of the time. **Mockist's** on the other-hand prefer to mock out any collaborating units from the unit under test. Martin uses the classical technique whilst Manasi uses a mixture of the two.

## Generative testing

I was encouraged to see that Manasi used Clojure for demo of **Generative Testing** as it's a language that I find very interesting. Manasi explained that the generated values had produced test cases that were not taken into account for the original unit tests. The example went by quickly and watching the video did not jog my memory of the exact details; I'll have to give this a try and write about it afterwards.

## Summary

Leaving the venue I didn't think I had gotten anything new from the talk but after reviewing the content it has made me think about my team, my role and my unit testing approach and that I'm going to have to give generative testing a try.

## Further reading

### Agile fluency

[The original article](https://martinfowler.com/articles/agileFluency.html)

[A nice summary by Pietro Di Bello](https://gist.github.com/xpepper/7e8486d527a64db71de87036c67d3a39)

### Classical vs mockist unit testing

[A nice comparison by Jonathan Rasmusson](https://agilewarrior.wordpress.com/2015/04/18/classical-vs-mockist-testing/)

[Ian Cooper's take](http://codebetter.com/iancooper/2008/02/04/classicist-vs-mockist-test-driven-development/)

[Martin Fowler's take](https://martinfowler.com/articles/mocksArentStubs.html)
