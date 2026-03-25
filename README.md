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

### Media Queries

### Responsive Web Design

### Mobile-First Design



Why Do We Need CSS Methodologies?
Let’s start with the core issue: CSS is globally scoped. This means that styles declared in a single stylesheet are accessible throughout your entire project. While this global nature allows for flexibility, it also introduces some serious challenges:

The Cascade Effect: CSS stands for "Cascading Style Sheets." Any change made within your stylesheet can cascade throughout your entire codebase, affecting elements you didn’t intend to modify. For small projects, this is manageable, but as your CSS grows to hundreds or even thousands of lines, the cascading effect can lead to unintended consequences.
Lack of Organization: As styles accumulate, a single CSS file can become bloated and difficult to navigate. Without proper organization, finding and updating styles becomes time-consuming.
Naming Conflicts: Because CSS has no built-in scoping mechanism, class and ID names can easily conflict, leading to unpredictable behavior. High specificity can further complicate things, making it harder to override styles when needed.
Maintainability Issues: When projects scale up, maintaining a single global CSS file becomes a daunting task. It becomes harder to add new features without breaking existing styles or introducing redundancy.









