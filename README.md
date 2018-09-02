# README.md


***
## References 
1. How to Use Constraints And Size Classes in Xcode8 : https://youtu.be/7iT9fueKCJM
2. 14 Auto Layout Best Practices for Xcode 9 and iOS 11 : https://youtu.be/nqO11vmzapg
3. Introduction to Auto Layout in iOS: Editing Constraints in Interface Builder - raywenderlich.com : https://www.youtube.com/watch?v=DKP4oiRYSUE&feature=share
4. Understanding Auto Layout in Xcode 9: https://hackernoon.com/understanding-auto-layout-in-xcode-9-2719710f0706
5. Auto Layout UI Examples : https://hackernoon.com/auto-layout-ui-examples-2517c7efca25
6. Understanding Auto Layout : https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/index.html

***

## Size type

i.e. Main.storyboard > Choice phone type >  view as : iPhone 8 Plus (w: R, h: C)

1. Regular - Regular 
    iPad
    - Portrait
    - Landscape

2. Regular - Compact 
    iPhone
    - Portrait

 3. Compact - Regular
    iPhone 6+
    - Landscape

4. Compact - Compact
    iPhone
    - Landscape


## Constraint Math


### case 1

<label>Search</label>
<input type ="text" />

attribute1 = multiplier * attribute2 + constant

textfield.leading = 1.0 * label.trainling + 8.0

### case 2

attribute1 = multiplier * attribute2 + constant
topView.height = 0.5 * view.height + 0.0


## What is Auto Layout?
Auto Layout dynamically calculates the size and position of all the views in your view hierarchy. It's an Xcode feature that you must know when it comes to building the user interface for your next iOS project. With the proper use of constraints, you will make your app responsive to any iPhone size that currently exists. 

In this tutorial, I will explain the Auto Layout constraints and how to properlyapply them. First of all, I want to mention that you can work with constraints both programmatically or from the Interface Builder. In most cases, you should focus on working with the second approach. 

## Constraints

I am sure you have already seen this bar above the console area. This is the place where all the magic happens. On the right side, you will see 3 tabs that are enabled. That's everything that you might ever need when working with constraints. 

## 1. Add New Constraints

I will start with the middle tab because it's the most important one. From here, we can add constaints that we need for the selected view. Basically, you can add both poisition and size type of constraints. 

## Position Constraints

If you can see from the above screenshot, there are 4 red lines at the top of the window. Each line represents a side that we want the selected view to follow. The numbers next to each line, represent how much margin space we want to leave between the selected view and the superview or some other child view. It will connect with anything that is on the specified side. 

* Leading - a constraint that follows the left side.
* Top - a constraint that follows the top side.
* Bottom - a constaint that follows the bottom side.
* Trailing - a constraint that follows the right side. 

For example, if you want to view to always be in the top left corner, you will need to add leading and top constraints. 

## Size Constrains

Below the position constraints, we can see the size constraints. They define how big the view will be. 

* Width = adds static width to the selected view.
* Height = adds static height to the selected view.
* Equal Width = adds width to the selected view that is equal to another view width.
* Equal Height = adds height to the selected view that is equal to another view height. 
* Aspect Ratio = If you need your view always to be squared and have dynamic size, you need to add an aspect ratio constraint with the value 1:1. 

## 2. Add Align Constraints

From the first tab, you can add alignment constraints to your selected view. In most cases, you will need just the enabled ones. From here, you can center the view. in the superview either horizontally, vertically or both. 

For example, select both Horizontally in Container and Vertically in Container in order to center your selected view in the superview.

## 3. Resolve Auto Layout issues

Auto Layout provides us with a help section that can resolve our constraint issues fast. There are two types, (1) resolve issues on the selected views, (2) resolve issues on all the views inside the view controller. 

* Add Missing Constraints - Xcode will monitor your constraints and give you an option to add the missing constaints. Note that these constraints are suggestions. It doesn't means that they will adapt to your situation.

* Reset to Suggested Constaints - this option will remove all your constraints and apply its own set of constraints. This is also a suggestion.

* Clear Constraints - it will erase all your constraints.

To be honest, I am ignoring this feature and always try to create the constraints by myself.I only use the Clear Constraints option when it's necessary. That's the only way to mastering Auto Layout. 

 
---

Working properly with Auto Layout is really important if you want to become a good iOS Developer. That's why I want to write another story where I will show you some UI scenarios and how to handle them with the Auto Layout constraints. I am aware that there are tons of different situations, but I will cover a few common ones. 


## UI Examples

I will start simple. Let's say you need to create a UILabel with dynamic height that will follow the length of the next. 

In order to achieve this scenario, we will need just 3 constraints. Leading,Trailing and Top. Also, don't forget to set the number of lines property to 0 if you want your UILabel to have unlimited lines. We don't need to set any height constraint to the component because that way we are telling it to define its own height based on its content. 

2. How about having two view components next to each other with equal width and height?

In order to achieve this common scenario, I would like to introduce you first with proportinal size. 

## Proportional Size

By defining proportional size, we are telling the component to take an exact percentage of the view we are targeting. For example, in our case, the Pink View will contain 44% width from the width of Superview. That means,that view will always occupy 44% width (on any screen size). We can also apply proportional size on height. 

To add a proportional size, press CTRL and drag from your custom view towards the superview. The following menu will appear, and you can add Equal Widths or Heights.

Upon selection, click on the created constraint and set the multiplier to be 0.44. The multiplier defines how much percentage should the First Item take from the Second Item. If you are using proportional size, always make sure to leave Constant 0 and Priority 1000.

Now when you know what proportional size is, let's get back to adding all the required to the Pink and Blue View. 

### Pink View

1. Top and Leading constraints to define the position.
2. Static Height constraint.
3. Proportional Width to Superview constaint with a multiplier of 44%.

### Blue View
1. Top and Trailing constaints to define the position.
2. Equal Height to Pink View. 
3. Equal Width to Pink View.

On the Blue View, we are setting the size to be equal to the size of the Pink View. In this case, the multiplier should stay 1,because we want to get 100% exact width and height as the Pink View. 

3. Creating a dynamic height on UITableViewCell, based on the content in each cell. 
I think this one is a really exciting example because, with the help of Auto Layout and almost no coding at all, you can tell the UITableView to calculate the height automatically. 

Those of you who are working in Xcode before Auto Layout came out, will understand the pain. It was required a lot of effort to create a cell with a dynamic height. 

As I mentioned above, this is really simple to be achieved with Auto Layout. I have a UITableViewCell with 2 UILabels one below another, and they are both set to follow its content size. 

* On the top label, you should add Leading, Trailing and Top constraints.
* On the bottom label, you should add Leading, Trailling, Top and Bottom constraints. 

Always rememeber to connect each component with the one above it, and also add a Bottom constaint to the last component at the end of the cell. This componets chain is really important because that's how the cell gets "pushed" by them and calculates the total height. 

### UITableViewDelegate

We should also write some code, that will trigger the UITableView to calculate cells height automatically. 

```
func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath0 -> CGFloat {
	return UITableViewAutomaticDimension
} 

func tableView(_ tableView: UITableView, estimatedHeightForRowAt indexPath: IndexPath) -> CGFloat {
	return 75
}
```

Add `UITableViewAutomaticDimension` in `heightForRowAt` delegate method, and also add a height that you expect the cells to start within `estimatedHeightForRowAt`. I always add the current cell height that is set in the Interface Builder. 

4. Doing constaint animations in AutoLayout with the help of NSLayoutConstraints.

Start by connecting an NSLayoutConstraint outlet for the constraint that you want to animate. For exmaple, let's say you need to animate the position of some view.

```
@IBOutlet fileprivate var topConstaint: NSLayoutConstraint!
@IBOutlet fileprivate var customView: UIView!
```

Now,to animate the constraint we need to use the native UIView method `animate()`.

```
UIView.animate(withDuration: 0.5) {
	self.topContraint.constant = 100
	self.customView.layoutIfNeeded()
}
```

What happens here is that we are assigning a new value to the constaint whare we want it to go, and after that we are making the view reload its content by using `layoutIfNeeded`.


***

## Understanding Auto Layout by Apple Developer

Auto Layout dynamically calculates the size and position of all the views in your view hierarchy, based on constraints placed on those views. For example, you can constrain a button so that it is horizontally centered with an Image view and so that the button's top edge always remains 8 points below the image's bottom. If the image view's size or position changes, the button's position automatically adjusts to match. 

This constraint-based approach to design allows you to build user interfaces that dynamically respond to both internal and exteranl changes. 

### External Changes

External changes occur when the size or shape of your superview changes. With each change, you must update the layout of your view hierarchy to best use the available space. Here are some common sources of external change:

* The user resizes the window (OS X).
* The user enters or leaves Split View on an iPad (iOS).
* The device rotates (iOS).
* The active call and audio recording bars appear or disappear (iOS).
* You want to support different size clasess.
* You want to support different screen sizes.

Most of changes can occur at runtime, and they require a dynamic response from your app. Others, like support for different screen sizes, represent the app adapting to different environments. Even though the screen size won't typically change at runtime, creating an adaptive interface lets your app run equally well on an iPhone 4S, an iPhone 6 plus, or even an iPad. Auto Layout is also a key component for supporting Slide Over and Split views on the iPad.

### Internal Changes

Internal changes occur when the size of the views or controls in your user interface change.

Here are some common sources of internal change:

* The content displayed by the app changes.
* The app supports internationalization.
* The app supports Dynamic Type (iOS).

When your app's content changes, the new content may require a different layout than the old. This commonly occurs in apps that display text or images. For examples,a news app needs to adjust its layout based on the size of the individual news articles. Similarly, a photo collage must handle a wide range of image sizes and aspect ratios.

Internaltionalization is the process of making your app able to adapt to different languages, regions, and cultures. The layout of an interationalizaed app must take these differnces into account and appear correctly in all the languages and regions that the app supports. 

Interanationalization has three main effects on layout. First, when you translate your user interface into a different language,the labels require a differnt amount of space. 
German, for example, typically requires considerably more space than English.  Japanese frequently requires much less. 

Second, the format used to represent dates and numbers can change from region to region, even if the language does not change. Although these changes are typically more subtle than the language changes, the user interface still needs to adapt to the slight variation in size.

Third, changing the language can affect not just the size of the text, but the organization of the layout as well. Different languages use different layout dirctions. English, for example, uses a left-to-right layout direction, and Arabic and Hebrew use a right-to-left layout direction. In general, the order of the user interface elements should match the layout direction. If a button is in the bottom-right corner of the view in English, it should be in the bottom left in Arabic. 

Finally, if your iOS app supports dynamic type, the user can change the font size used in your app. This can change both the height and the width of any textual elements in your user interface. If the user changes the font size while your app is running, both the fonts and the layout must adapt. 


### Auto Layout Versus Frame-Based Layout

There are three main approaches to laying out a user interface. You can programmatically lay out the user interface. You can use autoresizing masks to automate some of the response to exteral change, or you can use Auto Layout. 

Traditionally, apps laid out their user interface by programmtically setting the frame for each view in a view hierachy. The frame defined the view's origin, height, and width in the superview's coordinate system. 

To lay out your user interface, you had to calculate the size and position for every view in your view hierarchy. then, if a change occurred, you had to recalculate the frame for all the effected views. 

In many ways, programmatically defining a view's frame provides the most flexibility and power. When a change occurs, you can literally make any change you want. Yet because you must also manage all the changes yourself, laying out a simple user interface requires a considerable amount of effort to design, debug, and maintain. Creating a truly adaptive user interface increases the difficulty by an order of magnitude. 

You can use autoresizing masks to help alleviate some of this effort. An autoresizing mask defines how a view's frame changes when its superview's frame changes. This simplifies the creation of layouts that adapt to external changes. 

However, autoresizing masks support a relavtively small subset of possible layouts. For complex user interfaces, you typically need to augment the autoresizing masks with your own programmatic changes. Additionally, autoresizing masks adapt only to exteranl changes. They do not support internal changes. 

Although autoresizing masks are just an iterative improvement on programmatic layouts, Auto Layout represents an entirely new paradigm. Instead of thinking about a view's frame, you think about its relationships. 

Auto Layout defines your user interface using a series of constraints. Constraint typically represent a relationship between two views. Auto Layout then calculates the size and location of each view based on these constraints. This produces layouts that dynamically respond to both internal and external changes. 

The logic used to design a set of constraints to create specific behaviors is very different from the logic used to write procedural or object-oriented code. Forfunately, mastering Auto Layout is no different mastering any other programming task. There are two basic steps: First you need to understand the logic behind constraint-based layouts, and then you need to learn the API. You've successfully performed these steps when learning other programming tasks. Auto layout is no exception. 

The rest of this guide is designed to help ease your transition to Auto Layout. The Auto Layout Without Constraints chapter describes a high-level abstraction that simplifies the creation of Auto Layout backed user interfaces. The Anatomy of a Cosntraint chapter provides the background theory you need to understand to succussfully interact with AutoLayout on your own. Working with Constraints in Interface Builder describes the tools for designing Auto Layout, and the Programmatically Creating Cosstraints and Auto Layout Cookbook chapters describe the API in detail. Finally, the Auto Layout Cookbook presents a wide range of sample layouts of varying levels of complexity, you can study and use in your own projects, and Debugging Auto Layout offers advice and tools for fixing things if anything goes wrong. 


### Auto Layout Without Constaints

Stack views provide an easy way to leverage the power of Auto Layout without introducing the complexity of constraints. A single stack view defines a row or column of user interface elements. The stack viw arranges these elements based on its properties.

* axis (UIStackView only) defines the stack view's orientation, either vertical or horizontal. 
* orientation (NSStackView only) defines the stack view's orientation, either vertical or horizontal.
* distribution : defines the layout of the views along the axis. 
* alignment: defines the layout of the views perpendicular to the stack views' axis
* spacing: defines the space between adjacent views.

To use a stack view, in Interface Builder drag either a vertical or horizontal stack view onto the canvas. Then drag out the content and drop it into the stack. 

To further fine-tune the layout, you can modify the stack view's properties using the Atrributes inspector. For example, the following example uses a 8-point spacing and a Fills Equally distribution. 

The stack view also bases its layout on the arranged views' content-hugging and compression-resistance priorities. You can modify these using the Size inspector. 

> Note : You can further modify the layout by adding constraints directly to the arranged views; however, you want to avoid any possible conflicts: As a general rule of thumb, if a view's size defaults back to its intrinsic content size for a given dimension, you can safely add a constaint for that dimension. For more information on confilicting constrationts, see Unsatisfiable Layouts.

Additionally, you can nest stack views inside other stack views to build more complex layouts. 

In general, use stack views to manage as much of your layout as possible. Resort to creating constraints only when you cannot achieve your goals with stack views alone. 


***

## Anatomy of a Constraint

The layout of your view hierarchy is defined as a series of linear equations. Each constraint represents a single equation. Your goal is to declare a series of equations that has one and only possible solution.

A sample equation is shown below. 

This constraint states that the red view's leading edge must be 8.0 points after the blue view's trailing edge. Its equation has a number of parts:

RedView.Leading        =             1.0 *       BlueView.trailing +     8.0
[item1] [Attribute1] [Relationship] [Multiplier] [item2]  [Attribute2]  [Constant]   

* Item 1. The first item in the equation - in this case, the red view. The item must be either a view or a layout guide.
* Attribute 1. The attribute to be constrained on the first item-in this case,the red view's leading edge.
* Relationship. The relationship between the left and right sides. The relationship can have one of three values: equal, greater than or equal, or less than or equal. In this case, the left and right side are equal.
* Multiplier. The value of attribute 2 is multiplied by this floating point number. In this case, the multiplier is 1.0
* Item 2. The second item in the equation-in this case, the blue view. Unlike the first item, this can be left blank. 
* Attribute 2. The attribute to be constrained on the second item-in this case, the blue view's trailing edge. If the second item is left blank, this must be Not an Attribute.
* Constant. A constant, floating-point offset-in this case, 8.0. This value is added to the value of attribute 2.

Most constraints define a relationship between two items in our user interface. These items can represent either views or layout guides. Constraints can also define the relationship between two different attributes of a single item, for example, setting an aspect ratio between an item's height and width. You can also assign constant values to an item's height or width. When working with constant values, the second item is left blank, the second attribute is set to Not an Attribute, and the multiplier is set to 0.0.

## Auto Layout Attributes

In Auto Layout, the attributes define a feature that can be constrained. In general, this includes the four edges(leading, trailing, top, and bottom), as well as the height, width, and vertical and horizontal centers. Text items also have one or more baseline attributes.

For the complete list of attributes, see the NSLayoutAttributes enum. 

> Note : Although both OS X and iOS use the NSLayoutAttribute enum, they define slightly different sets of values. To see the full list of attributes, be sure you are looking at the correct platform's documentation.

## Sample Equations

The wide range of parameters and attributes available to these equations lets you create many different types of constraints. You can define the space between views, align the edge of views, define the relative size of two views, or even define a view's aspect ratio. However, not all attributes are compatible.

There are two basic types of attributes. Size attributes (for example, Height and Width) and location attributes (for example, Leading, Left, and Top). Size attributes are used to specify how large an item is, without any indication of its location. Location attributes are used to specify the location of an item relative to something else. However, they carry to indication of the item's size.

With these differences in mind, the following rules apply:

* You cannot constrain a size attribute to a location attribute.
* You cannot assign constant values to location attributes.
* You cannot use a nonidentity multiplier (a value other than 1.0) with location attributes. 
* For location attributes, you cannot constrain vertical attributes to horizontal attributes.
* For location attributes, you cannot constrain Leading or Trailing attributes to Left or Right attributes.

For example, setting an item's Top to the constant value 20.0 has no meaning without additional context. You must always define an item's location attributes in relation to other items, for example, 20.0 points below the superview's Top. However, setting an item's Height to 20.0 is perfectly valid. For more information, see Interpreting Values.

Listing 3-1 Sample equations for common constraints

```
// Setting a constant height
View.height = 0.0 * NotAnAttribute + 40.0

// Setting a fixed distance between two buttons
Button_2.leading  = 1.0 * Button_1.trailing + 8.0

// Aligning the leading edge of two buttons
Button_1.leading = 1.0 * Button_2.leading + 0.0

// Give two buttons the same width
Button_1.width = 1.0 * Button_2.width + 0.0

// Center a view in its superview
View.centerX = 1.0 * Superview.centerX + 0.0
View.centerY = 1.0 * Superview.centerY + 0.0

// Give a view a constant aspect ratio
View.height = 2.0 * View.width + 0.0
```

### Equality, NOt Assginment
It's important to note that equations shown in Note represent equality, not assignment. 

When Auto Layout solves these equations, it does not just assign the value of the right side to the left. Instead, it calculates the value for both attribute 1 and attribute 2 that makes the relationship true. This means we can often freely reorder the items in the equation. For example, the equation in Listing 3-2 are indentical to their conuterparts in Note.

Listing 3-2 Inverted equations

```
//Setting a fixed distance between two buttons
Button_1.trailing = 1.0 * Button_2.leading - 8.0

//Aligning the leading edge of two buttons
Button_2.leading = 1.0 * Button_1.leading + 0.0

// Give two buttons the same width
Button_2.width = 1.0 * Button.width + 0.0

// Center a view in its superView
Superview.centerX = 1.0 * View.centerX + 0.0
Superview.cneterY = 1.0 * View.centerY + 0.0

// Give a view a constant aspect ratio
View.width = 0.5 * View.height + 0.0

```

> Note: When reordering the items, make sure you invert the multiplier and the constant. For example, a constant of 8.0 becomes -8.0. A multiplier of 2.0 becomes 0.5. Constants of 0.0 and multipliers of 1.0 remain unchanged.


You will find that Auto Layout frequently provides multiple ways to solve the same problem. Ideally, you should choose the solution that most clearly describes your intent. However, different developers will undoubtedly disagree about which solution is best. Here, being consistent is better than being right. You will experience fewer problems in the long run if you choose an approach and always stick with it. For example, this guide uses the following rules of thumb:

1. Whole number multipliers are favored over fractional multipliers.
2. Positive constants are favored over negative constants.
3. Wherever possible, views should appear in layout order: leading to trailing, top to bottom.

## Creating Nonambiguous, Satisfiable Layouts

When using Auto Layout, the goal is to provide a series of equations that have one and only one possible solution. Ambiguous constraints have more than one possible solution. Unsatisfiable constraints don't have valid solutions.

In general, the constraints must define both the size and the position of each view. Assuming the superview's size is already set (for example, the root view of a scene in iOS), a nonambiguous, satisfiable layout requires two constraints per viwe dimension (not counting the superview). However, you have a wide range of options when it comes to choosing which constraints you want to use. For example, the following three layouts all produce nonambiguous, satisfiable layouts (only the horizontal constraints are shown):

* The first layout constraints the view's leading edge relative to its superview's leading edge. It also gives the view a fixed width. The position of the trailing edge can then be calculated based on the superview's size and the other constraints.

* The second layout constraints the view's leading edge relative to its superview's leading edge. It also constrains the view's trailing edge relative to the superview's trailing edge. The view's width can then be calculated based on the superview's size and the other constraints.

* The third layout constraints the view's leading edge relative to its superview's leading edge. It also center aligns the view and superview. Both the width and trailing edge's position can then be calculated based on the superview's size and the other constraints.

Notice that each layout has one view and two horizontal constraints. In each case, the constraints fully define both the width and the horizontal position of the view. That means all of the layouts produce a nonambiguous, satisfiable layout along the horizontal axis. However, these layouts are not equally useful. Consider what happens when the superview's width changes.

In the first layout, the view's width does not change. Most of the time, this is not what you want. In fact, as a general rule, you should avoid assigning constant sizes to views. Auto Layout is designed to create layouts that dynamically adapt to their environment. Whenever you give a view a fixed size, you short circuiting that ability. 

It may not be obvious, but the second and third layouts produce identical behaviors: They both maintain a fixed between the view and its superview as the superview's width changes. However, they are not necessarily equal. In general, the second example is easier to understand, but the third example may be more useful, especially when you are center aligning a number of items. As always, choose the best approach for your particular layout. 

Now consider somthing a little more complicated. Imagine you want to display two views, side by side, on an iPhone. You want to make sure that they have a nice margin on all sides and that they always have the same width. They should also correctly resize as the device rotates. 

The following illustrations show the views, in portrait and landscape orientation: 

So what should these constraints look like? The following illustration shows one straightforward solution:

The above solution uses the following constraints: 

```
// Vertical Cosntraints
Red.top = 1.0 * Superview.top +  20.0
Superview.bottom = 1.0 * Red.bottom + 20.0
Blue.top = 1.0 * Superview.top + 20.0
Superview.bottom = 1.0 * Blue.bottom + 20.0

// Horizontal Constraints
Red.leading = 1.0 * Superview.leading + 20.0
Blue.leading = 1.0 * Red.trailing + 8.0
Superview.trailing = 1.0 * Blue.trailing + 20.0
Red.width = 1.0 * Blue.width + 0.0

```

Following the earlier rule of thumb, this layout has two views, four horizontal constraints, and four vertical constraints. While this isn't an infalible guide, it is a quick indication that you're on the right track. More importantly, the constraints uniquely specify both the size and the location of both of the views, producing a nonambiguous, satisfiable layout. Remove any of these constraints, and the layout becomes ambiguous. Add additional constraints, and you risk introducing conflicts.

Still, this is not the only possible solution. Here is an equally valid approach: 

Instead of pinning the top and bottom of the blue box to its superview, you align the top of the blue box with the top of the red box. Similary, you align the bottom of the blue box with the bottom of the red box. The constraints are shown below. 

```
//Vertical constraints
 Red.top = 1.0 * Superview.top + 20.0
Superview.bottom = 1.0 * Red.bottom + 20.0
Red.top = 1.0 * Blue.top + 0.0
Red.bottom = 1.0 * Blue.bottom + 0.0

// Horizontal Constraints
Red.leading = 1.0 *  Superview.leading + 20.0
Blue.leading = 1.0 * Red.trailing + 8.0
Superview.trailing = 1.0 * Blue.trailing + 20.0
Red.width = 1.0 * Blue.width + 0.0

```


The example still has two views, four horizontal constraints, and four vertical constraints. It still produces a nonambiguous, satisfiable layout. 

> But which is better? These solutions both produce valid layouts. So which is better? Unfortunately, it is virtually impossible to objectively prove that one approach is strictly superior to the other. Each has its own strengths and weaknesses. The first solution is more robust when a view is removed. Removing a view from the view hierarchy also removes all the constraints that reference that view. So, if you remove the red view, the blue view is left with three cosntraints holding it in place. You need to add only a single constraint and you have a valid layout again. In the second solution, removing the red view would leave the blue view with only a single cosntraint. On the other hand, in the first solution, I you want the top and bottom of the views to align, you must make sure their top and bottom constraints use the same constant value. If you change one constant, you must remember to change the other as well. 

## Constraint Inequalities

So far, all of the samples have shown constaints as equalities, but this is only part of the story. Constraints can represent inequalities as well. Specifically, the constraint's relationship can be equal to, greater than or equal to, or less than or equal to. 

For example, you can use constraints to define the minimum or maximum size for a view (Listing 3-3).

Listing 3-3. Assigning a minimum and maximum size

```
// Setting the minmum width
View.width >= 0.0 * NotAnAttribute + 40.0

// Setting the maximum width
View.width <= 0.0 * NotAnAttribute + 280.0

```

As soon as you start using inequalities, the two constraints per view per dimension rule breaks down. You can always replace a single equality relationship with two inequalities. In Listing 3-4, the single equal relationship and the pair of  inequalities produce the same behavior. 

Listing 3-4 Replacing a single equal relationship with two inequalities

```
// A single equal relationship
Blue.leading = 1.9 * Red.trailing + 8.0

// Can be replaced with two inequality relationships
Blue.leading >= 1.0 * Red.trailing + 8.0
Blue.leading <= 1.0 * Red.trailing + 8.0
```

The inverse is not always true, becuase two inequalities are not always equivalent to a single equals relationship. For example, the inequalities in Listing 3-3 limit the range of possible values for the view's width - but by themselves, they do not define the width. You still need additional horizontal constraints to define the view's position and size within this range. 

## Constraint Priorities

By default, all constraints are required. Auto Layout must calculate a solution that satisfies all the constraints. If it cannot, there is an error. Auto Layout prints information about the unsatisfiable constraints to the console, and chooses one of the constraints to break. It then recalculates the solution without the broken constraint. For more information, see Unsatisifable Layouts.

You can also create optional constraints. All constraints have a priority between 1 and 1000. Constraints with a priority of 1000 are required. All other constraints are optional. 
When calculationg solutions, Auto Layout attempts to satisfy all the constraints in priority order from highest to lowest. If it cannot satisfy an optional constraint, that constraint is skipped and it continues on to the next constraint. 

Event if an optional constraint cannot be satisfied, it can still influence the layout. If there is any ambiguity in the layout after skipping the constraint, the system selects the solution that comes closest to the constaint. In this way, unsatisfied optional constraints act as a force pulling views towards them.

Optional constraints and inequalities often work hand-in-hand. For example, in Listing 3-4 you can provide different priorities for the two inequalities. The greater-than-or-equal relationship could be required  (priority of 1000), and the less-than-or-equal relationship has a lower priority (priority 250). This means that the blue view cannot be closer than 8.0 points from the red. However, other constraints could pull it farther away. Still, the optional constraint pulls the blue view towards the red view, ensuring that it is as close as possible to the 8.0-point spacing, given the other constraints in the layout. 

> Note : Don't feel obligated to use all 1000 priority values. In fact, priorities should general cluster around the system-defined low (250), medium (500), high (750), and required (1000) priorities. You may need to make constraints that are one or two points higher or lower than these values, to help prevent ties. If you're going much beyond that, you probably want to reexamine your layout's logic. For a list of the predefined constraint constants on iOS. see the UILayoutPriority enum. For OS X, see the Layout Priorities cosntants. 


### Intrinsic Content Size

So far, all of the exmaples have used constraints to define both the view's position and its size. However, some views have a natural size given their current content. This is referred to as their intrinsic content size. For exmaple, a button's intrinsic content size is the size of its title plus a samll margin.  

Not all views have an intrinsic content size. For views that do, the intrinsic content size can define the view's height, its width, or both. Some examples are listed in Table 3-1. 

Table 3-1. Intrinsic content size for common controls

|View|intrinsic content size|
|--|--|
|UIView and NSView|No intrinsic content size.|
|Sliders|Defines only the width (iOS). \n Defines the width, the height, or both-depending on the slider's type (OS X).|
|Labels,buttons, switches, and text fields | Defines both the height and the width.|
|Text views and image views | Intrinsic content size can vary|

The intrinsic content size is based on the view's current. A label or button's intrinsic content size is based on the amount of text shown and the font used. For other views, the intrinsic content size is even more complex. For example, an empty image view does not have an instrinsic content size. As soon as you add an image, though, its intrinsic content size is set to the image's size.

A text view's intrinsic content size varies depending on the content, on whether or not it has scrolling enabled, and on the other constraints applied to the view. For example, with scrolling enabled, the view does not have an intrinsic content size. With scrolling disabled, by default the view's intrinsic content size is calculated based on the size of the text constraints to specify the view's width, the instrinsic content size defines the height required to display the text given its width.

Auto Layout represents a view's intrinsic content size using a pair of constraints for each dimension. The content hugging pulls the view inward so that it fits snugly around the content. The compression resistance pushes the view outward so that it does not clip the content. 

		Content
		compression
----->		TEXT      <------
Content hugging           Content hugging

These constraints are defined using the inequalities shown in Listing 3-5. Here, the IntrinsicHeight and IntrinsicWidth constants represent the height and width values from the view's intrinsic content size.

Listing 3-5 Compression-Resistance and Content-Hugging equations

```
//Compression Resistance
View.height >= 0.0 * NotAnAttribute + IntrinsicHeight
View.width >= 0.0 * NotAnAttribute + IntrinsicWidth

// Content Hugging
View.height <= 0.0 * NotAnAttribute + IntrisicHeight
View.width <= 0.0 * NotAnAttribute + IntrisicWidth

```

Each of these constraints can have its own priority. By default, views use a 250 priority for their content hugging, and a 750 priority for their compression resistance. Therefore, it's easier to stretch a view than it is to shrink it. For most controls, this is the desired behavior. For example, you can safety stretch a button larger then its intrinsic content size; however, if you shrink it, its content may become clipped. Note that Interface Builder may occasionally modify these priorities to help prevent ties. For more information, see Setting Content-Hugging and Compression-Resistance Priorities.

Whenever possible, use the view's intrinsic content size in your layout. It lets your layout dynamically adapt as the view's content changes.It also reduces the number of constraints you need to create a nonambiguous, nonconflicting layout, but you will need to manage the view's content-hugging and compression-resistance (CHCR) priorities. Here are some guidelines for handling intrinsic content sizes:

* When stretching a series of views to fill a space, if all the views have an identical content-hugging priority, the layout is ambiguous. Auto Layout doesn't know which view should be stretched. 
A common example is a label and text field pair. Typically, you want the text field to stretch to fill the extra space while the label remains at its intrinsic content size. To ensure this, make sure the text filed's horizontal content-hugging priority is lower than the label's.
In fact, this example is so common that Interface Builder automatically handles it for you, setting the content-hugging priority for all labels to 251. If you are programmatically creating the layout, you need to modify the content-hugging priority yourself. 

* Odd and unexpected layouts often occur when views with invisible backgrounds (like buttons or labels) are accidentally stretched beyound their their intrinsic content size. The actual problem may not be obvious, becuase the text simply appears in the wrong location. To prevent unwanted stretching, increase the content-hugging priority.

* Baseline constraints work only with views that are at their intrinsic content height. If a view is vertically stretched or compressed, the baseline constraints no longer align properly. 

* Some view, like swtiches, should always be displayed at their intrinsic content size. Increase their CHCR priorities as neeeded to prevent stretching or compressing. 

* Avoid giving views required CHCR priorities. It's usually better for a view to be the wrong size than for it to accidentally create a conflict. If a view should always be its intrinsic content size, consider using a very high priority (999) instead. This approach generally keeps the view from being stretched or compressed but still provides an emergency pressure valve, just in case your view is diplayed in an environment that is bigger or smaller than you expected.

### Intrinsic Content Size Versus Fitting Size

The intrinsic content size acts as an input to Auto Layout. When a view has an intrinsic content size, the system generates constraints to represent that size and the constraints are used to calculate the layout. 

The fitting size, on the other hand, is an output from the Auto Layout engine. It is the size calculated for a view based on the view's constraints. If the view lays out its subviews using Auto Layout, then the system may be able to calculate a fitting size for the view based on its content. 

The stack view is a good example. Barring any other constraints, the system calcuates the stack view's size based on its content and attributes. In many ways, the stack view acts as if it had an intrinsic content size: You can create a valid layout using only a single vertical and a single horizontal constraint to define its position. But its size is calculated by Auto Layout - it is not an input into Auto Layout. Setting the stack view's CHCR priorities has no effect, because the stack view does not have an intrinsic content size. 

If you need to adjust the stack view's fitting size relative to items outside the stack view, either create explicit constraints to capture those relationships or modify the CHCR priorities of the stack's contents relative to the items outside the stack. 

### Interpreting Values

Values in Auto Layout are always in points. However, the exact meaning of these measurements can vary depending on the attributes involved and the view's layout direction.

|Auto Layout Attributes|Value|Notes|
|--|--|--|
|Height,Width| The size of the view| These attributes can be assigned constant values or combined with other Height and Width attributes. These values cannot be negative|
|Top, Baseline, Bottom| The values increase as you move down the screen| These attributes can be combined only with Center Y, Top, Bottom, and Baseline attributes|
|Leading, Trailing| The values increases as you move towards the trailing edge. For a left-to-right layout directions, the values increase as you move to the right. For a right to left layout direction, the values increase as you move left| These attributes can be combined only with Leading, Trailing, or Center X attributes.|
|Left, Right | The values increase as you move to the right| These attributes can be combined only with Left, Right, and Center X attributes. Avoid using Left and Right attributes. Use Leading and Trailing instead. This allows the layout to adapt to the view's reading direction. By default the reading direction is determined based on the current language set by the user. However, you can override this where necessary. In iOS, set the semanticContentAttribute property on the view holding the constraint (the nearest common ancestor of all views affected by the constraint) to specify whether the content's layout should be flipped when switching between left-to-right and right-to-left languages.|
|Center X , Center Y| The interpretation is based on the other attribute in the equation.| Center X can be combined with Center X, Trailing, Right, and Left attributes. Center Y can be combined with Center Y,Top, Bottom, and Baseline attributes. |



## Working with Constraints in Interface Builder

There are three main options for setting up Auto Layout constaints in Interface Builder: You can control-drag between views, you can use the Pin and Align tools, and you can let Interface Builder set up the constraints for you  and then edit or modify the results.Each of these approaches has its own set of strengths and weaknesses. Most developers find that they prefer one approach over the others; however, being familiar with all three approaches lets you quickly switch between tools based on the task at hand.

For all three options, start by dragging your views and conrtrols from the Object library onto the scene.Resize and position them as needed. When you place a view on the own explicit constraints. Never ship an app with prototyping constrains. 

As soon as you create your first constraint, the system removes all the prototyping constraints from the views referred to by the constraint. Without the prototyping constrains, your layout no longer has enough constraints to uniquely size and position all the views. It becomes an ambiguous layout. The affected constraints suddenly appear in red, and Xcode generates a number of warnings. 

Don't panic. Just keep adding your constraints until your layout is complete. As soon as you add one constraint, you are responsible for adding all the constraints needed to create a nonambiguous, satisfiable layout. 

For more information on fixing layout warnings and errors, see Debugging Auto Layout.

### Control-Dragging Constraints

To create a constraint between two views, Control-click one of the views and drag to the other.

When you release the mouse, Interface Builder displays a HUD menu with a list of possible constaints.

Interface Builder intelligently selects the set of constraints based on the items you are constraining and the direction of your drag gesture. If you drag more or less horizontally, you get options to set the horizontal spacing between the views, and options to vertically align the views. If you drag more or less vertically, you get options to set the vertical spacing, and options to align the views horizontally. Both gestures may include other options (such as setting the view's relative size). 

> Note : You can use the Control-drag gesture both on items in the canvas and on icons in the scene's document outline. This is often useful when trying to draw constraints to hard-to-find items, like the top or bottom layout guides. When dragging to or from the document outline, Interface Builder does not filter the list of possible constraints based on the getsture's direction.

Interface Builder creates the constraints based on the views' current frames. Therefore, you need to position the views carfully before you draw the constraints. If you line up the views based on Interface Builder's guidelines, you should end up with a reasonable set of constraints. If necessary, you can always edit the constraints afterward. 

Control-dragging provides a very quick way to set a consrtriant; however, because the constraint's values are inferred from the scene's current layout, it is easy to end up off by a point. If you wnat finer control, review and edit the constraints after you create them, or use the Pin and Align tools.

### Using the Stack, Align, Pin and Resolve Tools

Interface Builder provides four Auto Layout tools in the bottom-right corner of the Editor window. These are the Stack, Align, Pin, and Resolve Auto Layout Issues tools. 

Use the Pin and Align tools when you want fine control when making constraints or when you wnat to make multiple constraints at once. As an added advantage, when you see these tools, you don't need to precisely place your views before creating the constraint. Instead, you can roughly set the relative positive of the views, add your constraints, and then update the frames. This lets Auto Layout calculate the correct positions for you.


