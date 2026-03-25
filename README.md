# Front-End-Notes

## HTML
Hyper Text Markup Language (本来の意味：Hyperlink to other + markup like bold/italic/underline)

### Semantic
The word 'semantic' refers to the study of meaning in language, and HTML has its own semantics. 
At the most basic level, tags like **img** for images, **p** for paragraphs, and **form** for forms    
clearly describe the content they represent, making the code more intuitive for developers.     
This simplicity aids in both remembering and writing code efficiently.

・**Code Readability**: Using meaningful tags (e.g., **section**, **article**) makes your code easier to understand and maintain, saving you time when revisiting or editing it.  
・**Search Engine Optimization (SEO)**: Proper semantic tags help search engines better interpret and rank your content, which can boost your website’s visibility.  
・**Accessibility**: Semantic HTML improves accessibility by assisting technologies like screen readers in interpreting content and enhancing keyboard navigation for users with disabilities.  

Some other points to consider:  
・**Future-Proofing**: Semantic HTML is based on web standards that are less likely to become obsolete, ensuring your site remains compatible with future browsers and technologies.  
・**Consistency Across Browsers**: Following semantic HTML practices results in better consistency in how your website appears across different browsers.  
・**Easier Collaboration**: When working with a team, semantic HTML makes it easier for others to understand the structure of your code, speeding up collaboration and development.  

### Void Element
Forbidden to input any content such as tags **hr**, **br**

### List Element
ul li for unordered list + list item  
ol li for ordered list + list item  
if need to start ol from five > ol start=5   

### File Path
./ Same folder  
../ Up 1 folder

### HTML Boilerplate
Doctype html head body    

<hr>
  
## CSS
### CSS Positioning
Every HTML element has a position property. Understanding how to manipulate these properties is key to controlling a website’s layout. 

1. position: static   
   -This is the default position for most elements.   
   -Elements are positioned according to the normal document flow, meaning they appear where they would in the HTML without any adjustments.
2. position: relative   
   -The element is positioned relative to its normal position in the document flow.   
   -You can adjust its position using top, right, bottom, or left properties. These values shift the element from where it would normally be.
3. position: absolute   
   The element is positioned relative to its nearest positioned ancestor (i.e., an ancestor element with a position other than static), or to the initial containing block if no such ancestor exists.   
   It removes the element from the document flow, meaning it doesn’t take up space and other elements will behave as if it doesn’t exist.
4. fixed   
   The element is positioned relative to the viewport (the visible area of the browser window).   
   It stays in place even when the user scrolls the page, which is useful for things like sticky headers or navigation bars.
5. positio: sticky   
   The element is initially positioned according to the normal document flow (like relative), but when you scroll past a certain point, it becomes fixed in place (like fixed).
   This is often used for sticky headers or sidebars.

   .element {
  position: sticky;
  top: 0;
}
These position properties allow for precise control over the layout and behavior of elements on your web pages.
7. position: float
     The float property in CSS is used to position an element to the left or right of its container, allowing other content to wrap around it.
    It removes the element from the normal document flow, which can be helpful for creating multi-column layouts and complex designs.
   float: left: Floats the element to the left, allowing content to wrap around the right side.
   float: right: Floats the element to the right, allowing content to wrap around the left side.
   Floats can be used to position elements side by side, such as in a two-column layout, by floating the left and right columns.
   Non-floating elements that come after a floated element will flow around it.

.column-left {
  float: left;
  width: 45%;
}

.column-right {
  float: right;
  width: 45%;
}
Difference from inline elements: Floated elements are removed from the normal document flow, unlike inline elements, which still respect the flow and dimensions of surrounding elements. In the browser’s Developer Tools, you can see how floated elements sit outside of the normal flow.

However, floating elements can lead to layout issues:

When floating elements are used inside a parent container, the parent’s height doesn’t automatically adjust to accommodate the floated children.
Example: A parent div with two floated child divs will have zero height, as the float property removes them from the document flow, causing layout issues.
12. Clear property
To fix the issue of a parent element collapsing when using floated children, we use the clear property.

clear: both: Clears both left and right floated elements, ensuring that the element is placed below any floated elements.
Fixing the collapse issue: Applying clear: both to a subsequent element will ensure the parent container wraps around its floated children correctly.
.clearfix {
  clear: both;
}
The clearfix technique:    
A common method to fix floated elements within their parent is to apply the clearfix hack, which can be done by adding an element with the clearfix class, ensuring the parent container properly wraps around its floated children.
.clearfix:after {
  content: "";
  display: table;
  clear: both;
}

<hr>
### Flexbox
The Flexbox (Flexible Box) layout system is a CSS module designed to lay out items in a container in a flexible way.   
It provides a more efficient method for aligning and distributing space among items, even when their sizes are unknown or dynamic.   
Flexbox allows you to create complex layouts with ease, making it an essential tool for responsive web design.

#### Key Terminology
Flex Container: The parent element that holds the flex items and controls their behavior.   
Flex Items: The child elements inside the flex container that are arranged according to the flex properties.     
Main Axis: The primary axis along which flex items are aligned (default: left to right).   
Cross Axis: The axis perpendicular to the main axis (default: top to bottom).   
The direction of these axes can be adjusted using flex properties.    
#### Display Modes
flex: The flex container behaves as a block-level element, meaning it takes up the full width of its parent (most commonly used).    
inline-flex: The flex container behaves like an inline element, fitting into the flow of other inline content.    
##### Flexbox Properties
justify-content: Aligns flex items along the main axis.   
.container {
  display: flex;
  justify-content: center;
}
gap: Specifies the space between flex items.
.container {
  display: flex;
  gap: 20px;
}
align-items: Aligns flex items along the cross axis.
.container {
  display: flex;
  align-items: center;
}
Flexbox offers a more intuitive and flexible way to arrange elements in a layout, particularly when dealing with responsive design challenges.
Overflow & Vertical Alignment
The Flexbox module provides excellent control over the arrangement of items, especially in a horizontal row. However, it also offers features for managing vertical alignment and handling overflow when there are too many items to fit within a container. Let's explore how to handle these situations.

Managing Overflow
When the number of flex items exceeds the available space within a flex container, the items can overflow. One way to handle this is by using the overflow property, which controls how excess content is displayed.

overflow: scroll: Adds scrollbars to the container, allowing the user to scroll through the content.
.container {
  display: flex;
  overflow: scroll;
}
Note: The overflow property is not exclusive to Flexbox and can be used with any container that has overflowed content.

Wrapping Items
Flexbox allows items to wrap onto multiple lines if they don't fit in a single row. This is done using the flex-wrap property.

flex-wrap: Allows flex items to wrap onto multiple lines when necessary.
.container {
  display: flex;
  flex-wrap: wrap;
}
Changing the Direction of Items
The default direction of flex items is horizontal (left to right). However, Flexbox also allows for vertical alignment using the flex-direction property.

flex-direction: Specifies the direction of the flex container's items. Options include:
row (default): Main axis flows horizontally from left to right.
column: Main axis flows vertically from top to bottom.
row-reverse: Main axis flows horizontally from right to left.
column-reverse: Main axis flows vertically from bottom to top.
.container {
  display: flex;
  flex-direction: column;
}
Shorthand: flex-flow
The flex-flow property is a shorthand for setting both flex-direction and flex-wrap at the same time.

flex-flow: Combines flex-direction and flex-wrap into a single declaration.
.container {
  display: flex;
  flex-flow: row wrap;
}
These Flexbox properties provide a robust and flexible way to handle content overflow, vertical alignment, and the arrangement of items in a container.


### Grid
The CSS Grid layout allows us to control the positioning of child elements along both axes. The element with display: grid is called the grid container, and its child elements are known as grid items.

By default, when display: grid is applied, the items are arranged in a single column, with each grid item placed in its own cell. This layout differs from the default block layout, where elements stack vertically.

Grid Template
The grid-template- properties allow us to control the size and arrangement of columns in a grid layout.

grid-template-columns defines the number and size of columns. Values can be space-separated, such as "auto", to automatically size the columns. For example, four "auto" values create four automatically sized columns.

If the columns are uniform in size, we can use the repeat() function, which simplifies the declaration by specifying the number of columns and their size. This reduces redundancy when all columns are the same size.

The fr (fractional unit) is useful for defining columns that take up a proportion of available space. For example, 1fr makes a column take up 1 fraction of the available space.

.grid-container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
}
This example will create a grid with three columns. The first and third columns each take up 1 fraction of the available space, while the second column takes up 2 fractions, making it twice as wide.

Grid Flow
By default, the grid fills out from left to right, row by row. However, we can modify this flow using the grid-auto-flow property. Declaring grid-auto-flow: column will make the grid flow from top to bottom, filling the first column first, then moving onto the next column.

.grid-container {

Aligning Items
To control how items align within their grid cells, CSS Grid provides several properties:

justify-items aligns grid items horizontally within their cells.
align-items aligns grid items vertically within their cells.
justify-self allows for horizontal alignment on individual grid items.
align-self allows for vertical alignment on individual grid items.
These properties can be applied to either the entire grid or individual grid items, giving you flexibility in how each item is positioned.
### Media Queries
Basic Syntax of a Media Query
A media query begins with the @media rule, followed by the condition you want to check, such as max-width or min-width. Inside the curly braces, you place the CSS rules that will be applied if the condition is met.

@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
This rule will apply the background-color: lightblue; style only when the viewport is 600px wide or less.

Media Features
You can specify various conditions in your media queries, called media features. These features allow you to target specific properties of the viewport or device.

Width and Height
The most common media features you’ll use are width and height. You can target devices based on their minimum (min-width) or maximum (max-width) dimensions.

@media (min-width: 768px) {
  .container {
    width: 80%;
  }
}
This rule applies when the viewport is at least 768px wide.

Orientation
You can target devices based on their orientation—whether they are in portrait or landscape mode.

@media (orientation: landscape) {
  .header {
    font-size: 2rem;
  }
}
This rule will apply the larger font size only when the device is in landscape mode.

Applying Media Queries to Responsive Design
By using media queries, you can apply specific styles depending on the viewport's width or orientation. This allows you to create layouts that adjust for different screen sizes.

@media (max-width: 600px) {
  .header {
    font-size: 1rem;
  }
}

@media (min-width: 601px) and (max-width: 1024px) {
  .header {
    font-size: 1.5rem;
  }
}

@media (min-width: 1025px) {
  .header {
    font-size: 2rem;
  }
}
For small screens (max-width: 600px), the header font size is set to 1rem.
For medium screens (601px to 1024px), the header font size is 1.5rem.
For larger screens (1025px and above), the header font size is set to 2rem.
Order of Media Queries
The order in which media queries are declared in the CSS file matters. CSS follows a cascading order, meaning that the styles from the last declared rule take precedence.

@media (max-width: 1000px) {
  .container {
    width: 90%;
  }
}

@media (max-width: 700px) {
  .container {
    width: 100%;
  }
}
The first rule applies for viewports up to 1000px wide, setting the container width to 90%.
The second rule applies for viewports up to 700px wide, setting the container width to 100%. Since it's declared after the first rule, it will override the width for smaller devices.
Combining Media Features with Logical Operators
You can combine multiple conditions using logical operators such as and, or, and not to create more complex queries.

and: Both conditions must be true.

@media (min-width: 640px) and (orientation: portrait) {
  .sidebar {
    display: block;
  }
}
This rule will apply if the viewport is at least 640px wide and the device is in portrait mode.

or: Either condition must be true.

@media (min-width: 640px), (orientation: landscape) {
  .content {
    margin: 20px;
  }
}
This rule applies if the viewport is at least 640px wide or the device is in landscape mode.

not: Excludes a condition.

@media not (min-width: 1000px) {
  .header {
    background-color: red;
  }
}
This rule applies for all viewports except those that are at least 1000px wide.

Conclusion
CSS Media Queries are a powerful tool for making websites responsive. By targeting different media features like width, height, and orientation, you can apply different styles based on the user's device and screen size. Combining media features with logical operators allows for even more precise control over your designs. Remember to structure your queries carefully, as their order can affect which rules are applied.

Additional Media Features for Website Design
CSS Media Queries offer more than just width, height, and orientation. Below are a few additional media features that help enhance website design.

Aspect Ratio
Targets devices with specific width-to-height ratios, useful for maintaining aspect proportions (e.g., video containers).

@media (aspect-ratio: 16/9) {
  .video-container {
    padding: 56.25% 0 0 0;
  }
}
Resolution
Targets devices with a specific pixel density, useful for delivering high-DPI images (e.g., Retina displays).

@media (min-resolution: 192dpi) {
  .logo {
    background-image: url('logo-high-res.png');
  }
}
Hover and Pointer
Detects if a device supports hover (like a mouse) or the precision of the pointing device (e.g., fine-tuned pointer vs touchscreen).

@media (hover: hover) {
  .button {
    cursor: pointer;
  }
}

@media (pointer: fine) {
  .button {
    padding: 15px;
  }
}
Prefers Reduced Motion
Allows you to provide alternative styles for users who prefer reduced motion for accessibility reasons.

@media (prefers-reduced-motion: reduce) {
  .animated-element {
    animation: none;
    transition: none;
  }
}
These media features help you target specific device characteristics and improve the user experience with adaptive designs and accessibility considerations.


### Responsive Web Design

### Mobile-First Design



Why Do We Need CSS Methodologies?
Let’s start with the core issue: CSS is globally scoped. This means that styles declared in a single stylesheet are accessible throughout your entire project. While this global nature allows for flexibility, it also introduces some serious challenges:

The Cascade Effect: CSS stands for "Cascading Style Sheets." Any change made within your stylesheet can cascade throughout your entire codebase, affecting elements you didn’t intend to modify. For small projects, this is manageable, but as your CSS grows to hundreds or even thousands of lines, the cascading effect can lead to unintended consequences.
Lack of Organization: As styles accumulate, a single CSS file can become bloated and difficult to navigate. Without proper organization, finding and updating styles becomes time-consuming.
Naming Conflicts: Because CSS has no built-in scoping mechanism, class and ID names can easily conflict, leading to unpredictable behavior. High specificity can further complicate things, making it harder to override styles when needed.
Maintainability Issues: When projects scale up, maintaining a single global CSS file becomes a daunting task. It becomes harder to add new features without breaking existing styles or introducing redundancy.









