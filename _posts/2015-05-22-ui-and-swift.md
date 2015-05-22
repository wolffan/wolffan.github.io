---
layout: post
title:  "UI and swift"
date:   2015-05-22
categories: swift UI nib dev xib coding IB
---

It's been a long time (so fast!) since we got Swift, almost a year now. Till now I read a lot, and I've played with playgrounds.

Now it's time for a real app! And as for me, this time was a lot about UI. I've been a week working with swift and Interface Builder and there are some gotchas that I understand Apple could have fixed by now...

### So you like IB right ?

When a new .swift file is created it's contents are basically an empty file and an import:

	import Foundation
	
That's about it. Therefore first thing you'll do if you are working with UI is actually replace the line for:

	import UIKit
	
Then we can crate our subclass of ViewController to start coding and stuff.

	class MyViewController : UIViewController {
	}		
	
BUT, when we create our MyViewController.xib and launch simulator what's going to happen is that you'll find an empty screen.
Subclasses of controllers won't automatically reach for a .xib file with the same name on swift (like it happens on Objective-C) to load is as it's view.

### Load the view manually

From Apple Doc

	override func loadView() {
		NSBundle.mainBundle().loadNibNamed("MyViewController", owner:self, options:nil)
	}
This code will reach for the view contained on the .xib file and make it the main view.

This means loads of repeated code.
Creating an override for loadView in an extension would be great, unless apple does not allow override on extensions.

##### Storyboards ?

If you use Storyboards though, you need to communicate between ViewControllers (make the connections), in this case swift loads properly the specified type of controller (and view) when its loaded + presented.

###### And other UIView subclasses ?

As far as I experimented if you load UIView subclasses (like Cells) there's no need for further manual stuff.

### Wrap up

I guess apple really wants us to use Storyboards :/.
