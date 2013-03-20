---
layout: post
title: Use popover step by step
tags: main
---

## Correct Steps

1. Create a project

	![image](/images/use-popover/p1.png)

1. Drop Popover and View Controller to Objects in Interface Builder 

	![image](/images/use-popover/p2.png)

1. Ctrl+N to Create a ViewController named `PopoverViewController`

	![image](/images/use-popover/p3.png)

1. Check the `PopoverViewController.xib` File's Owner to be `PopoverViewController`

	![image](/images/use-popover/p4.png)

1. Change the `MainMenu.xib` Popover View Controller object's Custom Class to be `PopoverViewController`

	![image](/images/use-popover/p5.png)

1. Ctrl Drag `Popover` Object to `Popover View Controller` Object to make `Popover` Object's delegate to be `Popover View Controller`

	![image](/images/use-popover/p6.png)

1. Set `Popover View Controller` object of `MainMenu.xib` 's Nib Name to `PopoverViewController`

	![image](/images/use-popover/p7.png)


1. Ctrl Drag `Pop` button to link an Action in `AppDelegate.m`

	![image](/images/use-popover/p8.png)

1. Ctrl Drag `Popover` object to `AppDelegate.h` to make an Outlet

	![image](/images/use-popover/p9.png)

1. Finish the Button Action to pop up work

		- (IBAction)popup:(id)sender {
		   [_popover showRelativeToRect:[sender bounds] ofView:sender preferredEdge:CGRectMinXEdge];
		}

1. Build and Run

	![image](/images/use-popover/p10.png)


## Possible Problems

1. loaded the "PopoverViewController" nib but no view was set.

		2011-12-17 23:17:37.791 UsePopover[3355:707] -[NSViewController loadView] loaded the "PopoverViewController" nib but no view was set.
		2011-12-17 23:17:37.793 UsePopover[3355:707] (
			0   CoreFoundation                      0x00007fff924d6286 __exceptionPreprocess + 198
			1   libobjc.A.dylib                     0x00007fff8ab25d5e objc_exception_throw + 43
			2   CoreFoundation                      0x00007fff924d60ba +[NSException raise:format:arguments:] + 106
			3   CoreFoundation                      0x00007fff924d6044 +[NSException raise:format:] + 116
			4   AppKit                              0x00007fff8b6b9e21 -[NSViewController loadView] + 336
			5   AppKit                              0x00007fff8b6b5a8a -[NSViewController view] + 41
			6   AppKit                              0x00007fff8bdcd232 -[NSPopover showRelativeToRect:ofView:preferredEdge:] + 159
			7   UsePopover                          0x00000001000013db -[AppDelegate popup:] + 203
			8   CoreFoundation                      0x00007fff924c5a1d -[NSObject performSelector:withObject:] + 61
			9   AppKit                              0x00007fff8b68c710 -[NSApplication sendAction:to:from:] + 139
			10  AppKit                              0x00007fff8b68c642 -[NSControl sendAction:to:] + 88
			11  AppKit                              0x00007fff8b68c56d -[NSCell _sendActionFrom:] + 137
			12  AppKit                              0x00007fff8b68ba30 -[NSCell trackMouse:inRect:ofView:untilMouseUp:] + 2014
			13  AppKit                              0x00007fff8b70b8e0 -[NSButtonCell trackMouse:inRect:ofView:untilMouseUp:] + 489
			14  AppKit                              0x00007fff8b68a63a -[NSControl mouseDown:] + 786
			15  AppKit                              0x00007fff8b6550e0 -[NSWindow sendEvent:] + 6306
			16  AppKit                              0x00007fff8b5ed68f -[NSApplication sendEvent:] + 5593
			17  AppKit                              0x00007fff8b583682 -[NSApplication run] + 555
			18  AppKit                              0x00007fff8b80280c NSApplicationMain + 867
			19  UsePopover                          0x00000001000012d2 main + 34
			20  UsePopover                          0x00000001000012a4 start + 52
			21  ???                                 0x0000000000000003 0x0 + 3
		)

This is because `PopoverViewController.xib` File's Owner / Controller class `PopoverViewController` 's view property didn't connect to Interface Builder's Custom View, You can do so by this:

![image](/images/use-popover/p11.png)
