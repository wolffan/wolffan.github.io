---
layout: post
title:  "Working with git and bad merges"
date:   2014-07-23
categories: iOS CleanCode Git
---

Sometimes when you hit:
{% highlight Objective-C %}
 $ git merge master
{% endhighlight %}
on one of your branches.
You get a nice message from git, telling you that we was not able to merge.

You have multiple options:
  <ul>
      <li> As for $"git mergetool" and merge manually </li>
      <li> Hit $"git reset --hard" and merge your branch into master first </li>
  </ul>

I've discovered that sometimes, specially with Xcode, the worst part of the merge is the file .xcodeproj.
It gets so messy, specially if you modify or create the same files in different branches (which is likely to happen).

You avoid that you may (as you may know): merge often master into your branch (I'd do that for every new branch merged into master).

But sometimes (as was my case today) you have been working in too many other things, it just won't work nicely.

When .xcodeproj is too bad I discovered that the best solution for me is:
{% highlight Objective-C %}
 "Open Xcode -> Go to target -> build phases -> search file".
{% endhighlight %}

Best solution so far for me, more clear what is going on with the project files (red color for missing), much safer when you have to merge back.

May be not the best solution, tell me yours!
