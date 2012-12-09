KLHorizontalSelect
=======

<img src="https://raw.github.com/KieranLafferty/KLHorizontalSelect/master/KLHorizontalSelect/iPhoneScreenshot.png" width="50%"/>

Scroll left and right on the section scroller to make a selection. Inspiration for this project came from 8tracks iPhone application

Note: KLHorizontalSelect is intended for use with portrait orientation on iPhone/iPad/iPod Touch.

[Check out the Demo](http://www.youtube.com/watch?v=uzWZG99SAF0&feature=youtube_gdata_player) *Excuse the graphics glitches and lag due to my slow computer.*

## Installation ##

Drag the included <code>KLHorizontalSelect.h, KLHorizontalSelect.m</code> files into your project. Then, include the following frameworks under *Link Binary With Libraries*:

* QuartzCore.framework

## Usage ##

Import the required file and declare your controller to conform to the KLHorizontalSelect delegate to recieve callbacks

	#import "KLHorizontalSelect.h"
	@interface KLViewController : UIViewController <KLHorizontalSelectDelegate>
	@property (nonatomic, strong) KLHorizontalSelect* horizontalSelect;
	@end

Initialize the control and set the table data with an array of dictionaries (See provided Plist for sample protocol)

	- (void)viewDidLoad
	{
	    [super viewDidLoad];
	    // Do any additional setup after loading the view.
	    [self.navigationController.navigationBar setTintColor:[UIColor colorWithRed:10/255.0 green:37/255.0 blue:70/255.0 alpha:1]];
    
	    //Initialize the informtion to feed the control
	    NSString* plistPath = [[NSBundle mainBundle] pathForResource: @"SectionData"
	                                                          ofType: @"plist"];
	    // Build the array from the plist
	    NSArray* controlData = [[NSArray alloc] initWithContentsOfFile:plistPath];
    
		// Do any additional setup after loading the view, typically from a nib.
	    self.horizontalSelect = [[KLHorizontalSelect alloc] initWithFrame: self.view.bounds];
	    [self.horizontalSelect setTableData: controlData];
	    [self.view addSubview: self.horizontalSelect];
    
	}

Implement the optional delegate method to be notified when a new item is selected

	- (void) horizontalSelect:(id)horizontalSelect didSelectCell:(KLHorizontalSelectCell *)cell {
	    NSLog(@"Selected Cell: %@", cell.label.text);
	}

## Config ##
The visual appearance can be tweaked by changing the constants in <code>KLHorizontalSelect.m</code>:

	#define kDefaultCellWidth 80.0
	#define kDefaultCellHeight 90
	#define kDefaultGradientTopColor  [UIColor colorWithRed: 242/255.0 green: 243/255.0 blue: 246/255.0 alpha: 1]
	#define kDefaultGradientBottomColor  [UIColor colorWithRed: 197/255.0 green: 201/255.0 blue: 204/255.0 alpha: 1]
	#define kHeaderArrowWidth 25.0
	#define kDefaultLabelHeight 20.0
	#define kDefaultImageHeight 60.0

## Contact ##

* [@kieran_lafferty](https://twitter.com/kieran_lafferty) on Twitter
* [@kieranlafferty](https://github.com/kieranlafferty) on Github
* <a href="mailTo:kieran.lafferty@gmail.com">kieran.lafferty [at] gmail [dot] com</a>

## License ##

Copyright (c) 2012 Kieran Lafferty

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