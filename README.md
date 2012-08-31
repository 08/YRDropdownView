# YRDropdownView

## Overview

YRDropdownView is a view library for displaying stylish alerts, warnings, and errors. Based on Tweetbot's implementation, [MKInfoPanel](https://github.com/MugunthKumar/MKInfoPanelDemo) by Mugunth Kumar, [MBProgressHUD](https://github.com/jdg/MBProgressHUD) by Matej Bukovinski and [DSActivityView](https://github.com/joycodes/DSActivityView) by David Sinclair, among other influences. Its API has been hashed out to make the code easily implemented and very versatile.

## Fork Information

This repo is forked from [Danielgindi/YRDropdownView](https://github.com/Danielgindi/YRDropdownView) which forked from [onemightyroar/YRDropdownView](https://github.com/onemightyroar/YRDropdownView). 

### Changes

- Add ability to toggle queuing behavior
- Use accessoryView instead of accessoryImageView, so can use not only `UIImageView` as accessory. i.e., `UIActivityIndicatorView`. To use this ability, call

    ``` objective-c
    + (YRDropdownView *)showDropdownInView:(UIView *)view
                                 title:(NSString *)title
                                detail:(NSString *)detail
						 accessoryView:(UIView *)accessoryView
                              animated:(BOOL)animated
                             hideAfter:(float)delay;
    ```

### Known Bugs

Please refer to the [issue tracker](https://github.com/gregwym/YRDropdownView/issues)


## Installation

To use YRDropdownView:

1. Copy over the `YRDropdownView` folder to your project folder. <del>(Note: currently, the background is being drawn using a stretchable image, `bg-yellow.png`. Should you choose to supply your own background, you only need the `YRDropdownView.h\.m` files)</del> The background is now been drew by code. 
2. Enjoy!

## Usage

Wherever you want to use YRDropdownView, import the header file as follows:

``` objective-c
#import "YRDropdownView.h"
```

### Basic
You can create your dropdown by calling the singleton method:

``` objective-c
[YRDropdownView showDropdownInView:self.view
                             title:@"Warning"
                            detail:@"Danger Will Robinson. You cannot do that."];
```

By default, calling the above method will only dismiss when clicked on. To dismiss, then call:

``` objective-c
[YRDropdownView hideDropdownInView:self.view];
```

### Customizing
There are many different ways to customize the alert by calling different singleton methods:

``` objective-c
+ (YRDropdownView *)showDropdownInView:(UIView *)view
                                 title:(NSString *)title;

+ (YRDropdownView *)showDropdownInView:(UIView *)view
                                 title:(NSString *)title
                                detail:(NSString *)detail;

+ (YRDropdownView *)showDropdownInView:(UIView *)view
                                 title:(NSString *)title
                                detail:(NSString *)detail
                              animated:(BOOL)animated;

+ (YRDropdownView *)showDropdownInView:(UIView *)view
                                 title:(NSString *)title
                                detail:(NSString *)detail
                                 image:(UIImage *)image
                              animated:(BOOL)animated;

+ (YRDropdownView *)showDropdownInView:(UIView *)view
                                 title:(NSString *)title
                                detail:(NSString *)detail
                                 image:(UIImage *)image
                              animated:(BOOL)animated
                             hideAfter:(float)delay;

+ (YRDropdownView *)showDropdownInView:(UIView *)view
                                 title:(NSString *)title
                                detail:(NSString *)detail
						 accessoryView:(UIView *)accessoryView
                              animated:(BOOL)animated
                             hideAfter:(float)delay;
                             
+ (BOOL)hideDropdownInView:(UIView *)view;
+ (BOOL)hideDropdownInView:(UIView *)view animated:(BOOL)animated;
```

### Toggling the Dropdown's behavior

``` objective-c
+ (void)toggleRtl:(BOOL)rtl;
+ (void)toggleQueuing:(BOOL)queuing;
```

When `toggleRtl:YES` is called, the order of elements in view will be reversed. i.e., accessoryView locates on the right of the labels. 

When `toggleQueuing:YES` is called, the Dropdowns will be queued. New Dropdown will not show until the last one disappears. 

## Notes

### Automatic Reference Counting (ARC) support
<del>ARC support has been neglected in part for now. Your contributions are more than welcome, however. If you want to use YRDropdownView in an ARC project, just add the [add the 
``` objective-c
-fno-objc-arc
```
compiler flag](http://stackoverflow.com/questions/6646052/how-can-i-disable-arc-for-a-single-file-in-a-project) to all YRDropdownView files in your project.</del>

ARC is now fully supported. Thanks Danielgindi's awesome work. 

## Origin Author's Contact

- http://github.com/eliperkins
- http://twitter.com/e_perkins1
- eli@onemightyroar.com


## License

### MIT License

Copyright (c) 2012 One Mighty Roar (http://onemightyroar.com)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
