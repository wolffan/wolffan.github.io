---
layout: post
title:  "Hands on @3x assets"
date:   2014-09-24
categories: iOS assets iOS8 UI screens
---

The new iOS is just around the corner. So a lot of teams are rushing their iOS8 features.
Some of them, even had already updated their apps to iOS8 only.
But... why almost no one has their apps with the proper screen sizes :-(.

I'll try to explain my pain last week migrating assets to @3x (and also to iPhone6 screen).

###Ignoring the new screens

If you literally ignore the screens everything will be smooth.
Ignore means, no logos and no launching images with new sizes.

The iPhone will launch and you'll se a small gap (between your current launch and the device resolution). It won't last,
the OS will resize the screen to 6 or 6+. The same will happen with all your screens. It may not be good, but
it won't be painful.

###Hands on @3x

But you know... we're good... let's do this so we have the best experience.
Having your new assets won't make the screen not zoom. Check this <a href="http://www.shinobicontrols.com/blog/posts/2014/09/17/ios8-day-by-day-day-27-launch-images">amazing article</a> from <a href="http://www.shinobicontrols.com/">ShinobiControls</a> on that.
Basically when you update launch image, you'll get the magic no-zoom.

###How do you lay out your views?

<ul>
  <li> layoutSubviews </li>
  <li> layoutSubviews + Autolayout </li>
  <li> xib files </li>
  <li> xib + Autolayout </li>
</ul>

After the app starts using new screen sizes you'll realise (as in my case) that maybe the app was not as prepared for new screen sizes as you thought.

So... time to start revisiting your apps screens just in case for the next release :-).
