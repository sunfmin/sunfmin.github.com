---
layout: post
title: Use popover step by step
---

1. Create a project

	![image](/images/use-pop-over/p1.png)

1. Drop Popover and View Controller to Objects in Interface Builder 

	![image](/images/use-pop-over/p2.png)

1. Ctrl+N to Create a ViewController named `PopoverViewController`

	![image](/images/use-pop-over/p3.png)

1. Check the `PopoverViewController.xib` File's Owner to be `PopoverViewController`

	![image](/images/use-pop-over/p4.png)

1. Change the `MainMenu.xib` Popover View Controller object's Custom Class to be `PopoverViewController`

	![image](/images/use-pop-over/p5.png)

1. Ctrl Drag `Popover` Object to `Popover View Controller` Object to make `Popover` Object's delegate to be `Popover View Controller`

	![image](/images/use-pop-over/p6.png)

1. Set `Popover View Controller` object of `MainMenu.xib` 's Nib Name to `PopoverViewController`

	![image](/images/use-pop-over/p7.png)


1. Ctrl Drag `Pop` button to link an Action in `AppDelegate.m`

	![image](/images/use-pop-over/p8.png)

1. Ctrl Drag `Popover` object to `AppDelegate.h` to make an Outlet

	![image](/images/use-pop-over/p9.png)

1. Finish the Button Action to pop up work

		- (IBAction)popup:(id)sender {
		   [_popover showRelativeToRect:[sender bounds] ofView:sender preferredEdge:CGRectMinXEdge];
		}

1. Build and Run

	![image](/images/use-pop-over/p10.png)

