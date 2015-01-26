---
layout: post
title:  "Testing Protocols through test subclassing"
date:   2015-01-25
categories: iOS testing repository data protocols architecture
---

Last Friday I was developing a new screen on Lyst (try the app if you haven't yet).
The screen was not new, rather a new endpoint with very similar data to the old one.
Nothing fancy, new ViewController and new Repository.

We use an architecture based on Repositories, they handle the data and the network fetching for the each screen, and then they become the natural Data Source. <a href="https://twitter.com/Chilvman">Tim Chilvers</a> explains them in his <a href="http://vimeopro.com/user20904333/nslondon/video/98274951">NSLondon talk</> very well.

###Repositories and Protocols

Repositories rely on a "fixed" architecture that makes them really easy to use. Specially on screens like Tables or Collections. They fetch new data, more data, they return an element or the total number of elements (pretty much what a Data Source does). Therefore we rely on something called @Protocols for implementing the Repositories.

Protocols are contracts. And when your class implements a Protocol, it must implement the @required methods to conform to that Protocol (Xcode will mark the class as an error if you don't). That's really powerfull when you create a structure of views that subclass a common behaviour for data fetch & display. Changing the repository, will change the way the screen looks (because data will be different).

###Testing

Testing is a very good practice to avoid regression or to help you improve your codebase quality.
For me, 2014 was basically the year I learned how to properly test.

We use basically 3 levels of testing: Unit testing (classes), Integration Testing (UI) & Smoke testing (API).

On Friday I discovered a bug on the screen I was developing. It was not easy to spot, the API test gave me the hint. It was when we where trying to fetch the second page of data, nothing too crazy, but something basic that Repositories do all the time.

If we write our classes on a way that we could reuse the most common patterns (like fetching a page, and then another) why can't we do the same with tests?

My idea was as crazy as detect all classes that implemented a protocol and run the same tests agains them. Which goes against the basics of testing, but it was a way for me to generate "new tests" when a new implementation of a Protocol was created, therefore ensure some minimum quality.

My colleague was unsure about it, therefore I tweeted the most trusty person I know on tests, <a href="https://twitter.com/qcoding">Jon Reid</a>, and he was kind enough to <a href="https://twitter.com/qcoding/status/558699636479623168">tweet back</a>.

###Conclusions and experiments

I didn't know that subclasses of tests would also run the tests of the superclass, that's a very nice way to not repeat the same tests again. And on an architecture with multiple implementations of the same Protocol, that would happen.

Therefore I tried that myself in this project: <a href="https://github.com/wolffan/subclassTesting">subclass Tests</a>.

The conclusions are: if you run subclassed tests, the superclass tests will also run.

Still I'm unsure how to "automatically" test new implementations without writing new tests.
