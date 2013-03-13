---
layout: post
title: NSKeyedUnarchiver decodeObjectForKey cannot decode object of class (QTMovieView)
---

Because I didn't add QTKit.framework to the project, I got the error:


    [Switching to process 59876 thread 0x0]
    2011-12-14 20:05:41.205 PPTime[59876:707] An uncaught exception was raised
    2011-12-14 20:05:41.206 PPTime[59876:707] *** -[NSKeyedUnarchiver decodeObjectForKey:]: cannot decode object of class (QTMovieView)
    2011-12-14 20:05:41.215 PPTime[59876:707] (
    	0   CoreFoundation                      0x00007fff924d6286 __exceptionPreprocess + 198
    	1   libobjc.A.dylib                     0x00007fff8ab25d5e objc_exception_throw + 43
    	2   CoreFoundation                      0x00007fff924d60ba +[NSException raise:format:arguments:] + 106
    	3   CoreFoundation                      0x00007fff924d6044 +[NSException raise:format:] + 116
    	4   Foundation                          0x00007fff936a67d9 _decodeObjectBinary + 2714
    	5   Foundation                          0x00007fff936a7a4a -[NSKeyedUnarchiver _decodeArrayOfObjectsForKey:] + 1193
    	6   Foundation                          0x00007fff9367e530 -[NSArray(NSArray) initWithCoder:] + 486
    	7   Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	8   Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	9   AppKit                              0x00007fff8b68d679 -[NSView initWithCoder:] + 1051
    	10  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	11  Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	12  AppKit                              0x00007fff8b77ecac -[NSWindowTemplate initWithCoder:] + 3998
    	13  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	14  Foundation                          0x00007fff936a7a4a -[NSKeyedUnarchiver _decodeArrayOfObjectsForKey:] + 1193
    	15  Foundation                          0x00007fff936a744b -[NSSet(NSSet) initWithCoder:] + 519
    	16  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	17  Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	18  AppKit                              0x00007fff8b58fe2d -[NSIBObjectData initWithCoder:] + 2099
    	19  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	20  Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	21  AppKit                              0x00007fff8b58f4d8 loadNib + 235
    	22  AppKit                              0x00007fff8b58ea28 +[NSBundle(NSNibLoading) _loadNibFile:nameTable:withZone:ownerBundle:] + 217
    	23  AppKit                              0x00007fff8b58e943 +[NSBundle(NSNibLoading) loadNibFile:externalNameTable:withZone:] + 141
    	24  AppKit                              0x00007fff8b58e886 +[NSBundle(NSNibLoading) loadNibNamed:owner:] + 364
    	25  AppKit                              0x00007fff8b802637 NSApplicationMain + 398
    	26  PPTime                              0x00000001000014b2 main + 34
    	27  PPTime                              0x0000000100001484 start + 52
    	28  ???                                 0x0000000000000003 0x0 + 3
    )
    2011-12-14 20:05:41.301 PPTime[59876:707] *** Terminating app due to uncaught exception 'NSInvalidUnarchiveOperationException', reason: '*** -[NSKeyedUnarchiver decodeObjectForKey:]: cannot decode object of class (QTMovieView)'
    *** First throw call stack:
    (
    	0   CoreFoundation                      0x00007fff924d6286 __exceptionPreprocess + 198
    	1   libobjc.A.dylib                     0x00007fff8ab25d5e objc_exception_throw + 43
    	2   CoreFoundation                      0x00007fff924d60ba +[NSException raise:format:arguments:] + 106
    	3   CoreFoundation                      0x00007fff924d6044 +[NSException raise:format:] + 116
    	4   Foundation                          0x00007fff936a67d9 _decodeObjectBinary + 2714
    	5   Foundation                          0x00007fff936a7a4a -[NSKeyedUnarchiver _decodeArrayOfObjectsForKey:] + 1193
    	6   Foundation                          0x00007fff9367e530 -[NSArray(NSArray) initWithCoder:] + 486
    	7   Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	8   Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	9   AppKit                              0x00007fff8b68d679 -[NSView initWithCoder:] + 1051
    	10  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	11  Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	12  AppKit                              0x00007fff8b77ecac -[NSWindowTemplate initWithCoder:] + 3998
    	13  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	14  Foundation                          0x00007fff936a7a4a -[NSKeyedUnarchiver _decodeArrayOfObjectsForKey:] + 1193
    	15  Foundation                          0x00007fff936a744b -[NSSet(NSSet) initWithCoder:] + 519
    	16  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	17  Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	18  AppKit                              0x00007fff8b58fe2d -[NSIBObjectData initWithCoder:] + 2099
    	19  Foundation                          0x00007fff936a686b _decodeObjectBinary + 2860
    	20  Foundation                          0x00007fff936a5b86 _decodeObject + 201
    	21  AppKit                              0x00007fff8b58f4d8 loadNib + 235
    	22  AppKit                              0x00007fff8b58ea28 +[NSBundle(NSNibLoading) _loadNibFile:nameTable:withZone:ownerBundle:] + 217
    	23  AppKit                              0x00007fff8b58e943 +[NSBundle(NSNibLoading) loadNibFile:externalNameTable:withZone:] + 141
    	24  AppKit                              0x00007fff8b58e886 +[NSBundle(NSNibLoading) loadNibNamed:owner:] + 364
    	25  AppKit                              0x00007fff8b802637 NSApplicationMain + 398
    	26  PPTime                              0x00000001000014b2 main + 34
    	27  PPTime                              0x0000000100001484 start + 52
    	28  ???                                 0x0000000000000003 0x0 + 3
    )
    terminate called throwing an exceptionsharedlibrary apply-load-rules all
