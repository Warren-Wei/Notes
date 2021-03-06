# Notes for [<CSS: The Definitive Guide>](https://www.amazon.com/gp/product/1449393195/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1449393195&linkCode=as2&tag=285975600-20&linkId=319482acbe5fb41c5f68365d080b328c)

- Author: Eric A. Meyer, Estelle Weyl
- Version: 4th Edition 2017

## **Ch. 1 CSS and Documents**

### 1.1 A Brief History of (Web) Style

### 1.2 Elements

- 1.2.1 Replaced and Nonreplaced Elements
    - *Replaced elements* are those where the element's content is replaced by something that is not directly represented by document content. For example, The img element is replaced by an image file external to the document itself
    - *Nonreplaced elements* are those whose content is presented by the user agent (generally a browser) inside a box generated by the element itself
- 1.2.2 Element Display Roles
    - *Block-level elements*: generate an element box that fills its parent element's content area and cannot have other elements at its sides
    - *Inline-level elements*: generate an element box within a line of text and do not break up the flow of that line
    - CSS Property: `display` eg. `display: inline;` `display: block;`

### 1.3 Bringing CSS and HTML Together

- 1.3.1 The `<link>` Tag
- 1.3.2 The `<style>` Element
- 1.3.3 The `@import` Directive
    - Just like `<link>`, `@import` can be used to direct the web browser to load an external stylesheet and use its styles in the rendering of the HTML document. The only major difference is in the syntax and placement of the command. As you can see, `@import` is found inside the style container. It must be placed before the other CSS rules or it won't work at all

        ```
        <style type="text/css">
          @import url(style.css);
          h1 {color: gray}
        </style>
        ```

    - Like `<link>`, there can be more than one `@import` statement in a document
    - Unlike `<link>`, the stylesheets of every `@import` directive will be loaded and used
- 1.3.4 HTTP Linking
- 1.3.5 Inline Styles

### 1.4 Stylesheet Contents

- 1.4.1 Markup
- 1.4.2 Rule Structure
- 1.4.3 Vendor prefixing
- 1.4.4 Whitespace Handling
- 1.4.5 CSS Comments

### 1.5 Media Queries

- 1.5.1 Usage
- 1.5.2 Simple Media Queries
- 1.5.3 Media Types
- 1.5.4 Media Descriptors
- 1.5.5 Media Feature Descriptors and Value Types

### 1.6 Feature Queries

### 1.7 Summary

## **Ch. 2 Selectors**

### 2.1 Basic Style Rules

- 2.1.1 Element Selectors
- 2.1.2 Declarations and Keywords

### 2.2 Grouping

- 2.2.1 Grouping Selectors
- 2.2.2 Grouping Declarations
    - Although it is not technically necessary to follow the last declaration of a rule with a semicolon in CSS, it is generally good practice to do so. First, it will keep you in the habit of terminating your declarations with semicolons, the lack of which is one of the most common causes of rendering errors. Second, if you decide to add another declaration to a rule, you won’t have to worry about forgetting to insert an extra semicolon. Third, if you ever use a preprocessor like Sass, trailing semicolons are often required for all declarations. Avoid all these problems—always follow a declaration with a semicolon, wherever the rule appears.
- 2.2.3 Grouping Everything
- 2.2.4 New Elements in Old Browsers

### 2.3 Class and ID Selectors

- 2.3.1 Class Selectors
- 2.3.2 Multiple Classes
- 2.3.3 ID Selectors
- 2.3.4 Deciding Between Class and ID
    - In the real world, browsers don’t always check for the uniqueness of IDs in HTML. That means that if you sprinkle an HTML document with several elements, all of which have the same value for their ID attributes, you’ll probably get the same styles applied to each. This is incorrect behavior, but it happens anyway. Having more than one of the same ID value in a document also makes DOM scripting more difficult, since functions like getElementById() depend on there being one, and only one, element with a given ID value.

### 2.4 Attribute Selectors

- 2.4.1 Simple Attribute Selectors
- 2.4.2 Selection Based on Exact Attribute Value
    - this format requires an exact match for the attribute’s value. Matching becomes an issue when the selector form encounters values that can in turn contain a space-separated list of values (e.g., the HTML attribute class). For example, consider the following markup fragment: `<planet type="barren rocky">Mercury</planet>` The only way to match this element based on its exact attribute value is to write: `planet[type="barren rocky"] {font-weight: bold;}` If you were to write planet[type="barren"], the rule would not match the example markup and thus would fail. This is true even for the class attribute in HTML. Consider the following: `<p class="urgent warning">When handling plutonium, care must be taken to avoid the formation of a critical mass.</p>` To select this element based on its exact attribute value, you would have to write:`p[class="urgent warning"] {font-weight: bold;}` This is not equivalent to the dot-class notation covered earlier, as we will see in the next section. Instead, it selects any p element whose class attribute has exactly the value "urgent warning", with the words in that order and a single space between them. It’s effectively an exact string match.
- 2.4.3 Selection Based on Partial Attribute Values
- 2.4.4 A Particular Attribute Selection Type
    - You may have noticed that I’ve quoted all the attribute values in the attribute selectors. Quoting is required if the value includes any special characters, begins with a dash or digit, or is otherwise invalid as an identifier and needs to be quoted as a string. To be safe, I recommend always quoting attribute values in attribute selectors, even though it is only required to makes strings out of invalid identifiers.
- 2.4.5 The Case Insensitivity Identifier

### 2.5 Using Document Structure

- 2.5.1 Understanding the Parent-Child Relationship
- 2.5.2 Descendant Selectors
- 2.5.3 Selecting Children
- 2.5.4 Selecting Adjacent Sibling Elements
- 2.5.5 Selecting Following Siblings

### 2.6 Pseudo-Class Selectors

- 2.6.1 Combining Pseudo-Classes
- 2.6.2 Structural Pseudo-Classes
    - 2.6.2.1 Selecting the root element `:root`
    - 2.6.2.2 Selecting empty elements `:empty`
    - 2.6.2.3 Selecting unique children `:only-child` `:only-of-type`
    - 2.6.2.4 Selecting first and last children `:first-child` `:last-child`
    - 2.6.2.5 Selecting first and last of a type `:first-of-type` `:last-of-type`
    - 2.6.2.6 Selecting every nth child `:nth-child(n)` `:nth-child(3n+1)` `:nth-last-child(odd)`
    - 2.6.2.7 Selecting every nth of a type `:nth-of-type(even)`
- 2.6.3 Dynamic Pseudo-Classes
    - 2.6.3.1 Hyperlink pseudo-classes
        - `:link` Refers to any anchor that is a hyperlink (i.e., has and href attribute) and points to an address that has not been visited
        - `:visited` Refers to any anchor that is a hyperlink to an already visited address. For security reasons, the styles that can be applied to visited links are severely limited
        - Styled visited links enables visitors to know where they have been and what they have yet to visit. This is especially important on large websites where it may be difficult to remember, especially for those with cognitive disabilities, which pages have been visited. Not only is highlighting visited links one of the W3C Web Content Accessibility Guidelines, but it makes searching for content faster, more efficient, and less stressful for everyone.
    - 2.6.3.2 User action pseudo-classes
        - `:focus` Refers to any element that currently has the input focus—i.e., can accept keyboard input or be activated in some way.
        - `:hover` Refers to any element over which the mouse pointer is placed—e.g., a hyperlink over which the mouse pointer is hovering.
        - `:active` Refers to any element that has been activated by user input—e.g., a hyperlink on which a user clicks during the time the mouse button is held down.
        - While you can style elements with :focus any way you like, do not remove all styling from focused elements. Differentiating which element currently has focus is vital for accessibility, especially for those navigating your site or application with a keyboard
    - 2.6.3.3 Real-world issues with dynamic styling
- 2.6.4 UI-State Pseudo-Classes
    - `:enabled` Refers to user-interface elements (such as form elements) that are enabled; that is, available for input.
    - `:disabled` Refers to user-interface elements (such as form elements) that are disabled; that is, not available for input.
    - `:checked` Refers to radio buttons or checkboxes that have been selected, either by the user or by defaults within the document itself.
    - `:indeterminate` Refers to radio buttons or checkboxes that are neither checked nor unchecked; this state can only be set via DOM scripting, and not due to user input.
    - `:default` Refers to the radio button, checkbox, or option that was selected by default.
    - `:valid` Refers to a user input that meets all of its data validity semantics
    - `:invalid` Refers to a user input that does not meet all of its data validity semantics
    - `:in-range` Refers to a user input whose value is between the minimum and maximum values
    - `:out-of-range` Refers to a user input whose value is below the minimum or above the maximum values allowed by the control
    - `:required` Refers to a user input that must have a value set
    - `:optional` Refers to a user input that does not need to have a value set
    - `:read-write` Refers to a user input that is editable by the user
    - `:read-only` Refers to a user input that is not editable by the user
    - 2.6.4.1 Enabled and disabled UI elements
    - 2.6.4.2 Check states
    - 2.6.4.3 Default option pesudo-class
    - 2.6.4.4 Optionality pseudo-classes
- 2.6.5 The :target Pseudo-Classes
- 2.6.6 The :lang Pseudo-Classes
- 2.6.7 The Negation Pseudo-Classes

### 2.7 Pseudo-Element Selectors

- 2.7.1 Styling the First Letter
- 2.7.2 Styling the First Line
- 2.7.3 Restrictions on ::first-letter and ::first-line
- 2.7.4 Styling (or Creating) Content Before and After Elements

### 2.8 Summary

## Ch. 3 Specificity and the Cascade

## Ch. 4 Values and Units

### 4.1 Keywords, Strings, and Other Text Values

- 4.1.1 Keywords
- 4.1.2 Strings
- 4.1.3 URLs
- 4.1.4 Images
- 4.1.5 Identifiers

### 4.2 Numbers and Percentages

- 4.2.1 Integers
- 4.2.2 Numbers
- 4.2.3 Percentages
- 4.2.4 Fractions

### 4.3 Distances

- 4.3.1 Absolute Length Units
- 4.3.2 Resolution Units
- 4.3.3 Relative Length Units

### 4.4 Calculation values

### 4.5 Attribute Values

### 4.6 Color

- 4.6.1 Named Colors
- 4.6.2 Colors by RGB and RGBa
- 4.6.3 Colors by HSL and HSLa
- 4.6.4 Color Keywords

### 4.7 Angles

### 4.8 Time and Frequeny

### 4.9 Position

### 4.10 Custom Values

## Ch. 5 Fonts

### 5.1 Font Families

- 5.1.1 Using Generic Font Families
- 5.1.2 Specifying a Font Family

### 5.2 Using `@font-face`

- 5.2.1 Required Descriptors
- 5.2.2 Other Font Descriptors
- 5.2.3 Combining Descriptors

### 5.3 Font Weights

- 5.3.1 How Weights Work
- 5.3.2 Getting Bolder
- 5.3.3 Lightening Weights
- 5.3.4 The font-weight descriptor

### 5.4 Font Size

- 5.4.1 Absolute Sizes
- 5.4.2 Relative Sizes
- 5.4.3 Percentages and Sizes
- 5.4.4 Font Size and Inheritance
- 5.4.5 Using Length Units
- 5.4.6 Automatically Adjusting Size

### 5.5 Font Style

- 5.5.1 The font-style Descriptor

### 5.6 Font Stretching

- 5.6.1 The font-stretch Descriptor

### 5.7 Font Kerning

### 5.8 Font Variants

### 5.9 Font Features

- 5.9.1 The font-feature-settings Descriptor

### 5.10 Font Synthesis

### 5.11 The font Property

- 5.11.1 Adding the Line Height
- 5.11.2 Using Shorthands Properly
- 5.11.3 Using System Fonts

### 5.12 Font Matching

### 5.13 Summary

## Ch. 6 Text Properties

### 6.1 Indentation and Inline Alignment

- 6.1.1 Indenting Text
- 6.1.2 Text Alignment
- 6.1.3 Aligning the Last Line

### 6.2 Inline Alignment

- 6.2.1 The Height of Lines
- 6.2.2 Vertically Aligning Text

### 6.3 Word Spacing and Letter Spacing

- 6.3.1 Word Spacing
- 6.3.2 Letter Spacing
- 6.3.3 Spacing and Alignment

### 6.4 Text Transformation

### 6.5 Text Decoration

- 6.5.1 Weird Decorations

### 6.6 Text Rendering

### 6.7 Text Shadows

### 6.8 Handling Whitespace

- 6.8.1 Setting Tab Sizes

### 6.9 Wrapping and Hyphenation

- 6.9.1 Wrapping Text

### 6.10 Writing Modes

- 6.10.1 Setting Writing Modes
- 6.10.2 Changing Text Orientation
- 6.10.3 Declaring Direction

### 6.11 Summary

## Ch. 7 Basic Visual Formatting

### 7.1 Basic Boxes

- 7.1.1 A quick Refresher
- 7.1.2 The Containing Block

### 7.2 Altering Element Display

- 7.2.1 Changing Roles
- 7.2.2 Block Boxes
- 7.2.3 Horizontal Formatting
- 7.2.4 Horizontal Properties
- 7.2.5 Using auto
- 7.2.6 More Than One auto
- 7.2.7 Negative Margins
- 7.2.8 Percentage Heights
- 7.2.9 Auto Heights
- 7.2.10 Collapsing Vertical Margins
- 7.2.11 Negative Margins and Collapsing
- 7.2.12 List Items

### 7.3 Inline Elements

- 7.3.1 Line Layout
- 7.3.2 Basic Terms and Concepts
- 7.3.3 Inline Formatting
- 7.3.4 Inline Nonreplaced Elements
- 7.3.5 Building the Boxes
- 7.3.6 Vertical Alignment
- 7.3.7 Managing the line-height
- 7.3.8 Scaling Line Heights
- 7.3.9 Adding Box Properties
- 7.3.10 Changing Breaking Behavior
- 7.3.11 Glyphs Versus Content Area
- 7.3.12 Inline Replaced Elements
- 7.3.13 Adding Box Properties
- 7.3.14 Replaced Elements and the Baseline
- 7.3.15 Inline-Block Elements
- 7.3.16 Flow Display
- 7.3.17 Contents Display
- 7.3.18 Other Display Values
- 7.3.19 Computed Values

### 7.4 Summary

## Ch. 8 Padding, Borders, Outlines, and Margins

### 8.1 Basic Element Boxes

- 8.1.1 Width and Height

### 8.2 Padding

- 8.2.1 Replicating Values
- 8.2.2 Single-Side Padding
- 8.2.3 Percentage Values and Padding
- 8.2.4 Padding and Inline Elements
- 8.2.5 Padding and Replaced Elements

### 8.3 Borders

- 8.3.1 Borders with Style
- 8.3.2 Border Widths
- 8.3.3 Border Colors
- 8.3.4 Shorthand Border Properties
- 8.3.5 Global Borders
- 8.3.6 Borders and Inline Elements
- 8.3.7 Rounding Border Corners
- 8.3.8 Image Borders

### 8.4 Outlines

- 8.4.1 Outline Styles
- 8.4.2 Outline Width
- 8.4.3 Outline Color
- 8.4.4 How They Are Different

### 8.5 Marigins

- 8.5.1 Length Values and Margins
- 8.5.2 Percentages and Margins
- 8.5.3 Single-Side Margin Properties
- 8.5.4 Margin Collapsing
- 8.5.5 Negative Margins
- 8.5.6 Margins and Inline Elements

### 8.6 Summary

## Ch. 9 Colors, Backgrounds, and Gradients

### 9.1 Colors

- 9.1.1 Foreground Colors
- 9.1.2 Affecting Borders
- 9.1.3 Affecting Form Elements
- 9.1.4 Inheriting Color

### 9.2 Backgrounds

- 9.2.1 Background Colors
- 9.2.2 Clipping the Background
- 9.2.3 Background Images
- 9.2.4 Background Positioning
- 9.2.5 Changing the Positioning Box
- 9.2.6 Background Repeating (or Lack Thereof)
- 9.2.7 Getting Attached
- 9.2.8 Sizing Background Images
- 9.2.9 Bringing It All Together
- 9.2.10 Multiple Backgrounds

### 9.3 Gradients

- 9.3.1 Linear Gradients
- 9.3.2 Radial Gradients
- 9.3.3 Manipulating Gradient Images
- 9.3.4 Repeating Gradients

### 9.4 Box Shadows

### 9.5 Summary

## Ch. 10 Floating and Shapes

### 10.1 Floating

- 10.1.1 Floated Elements
- 10.1.2 Floating: The Details
- 10.1.3 Applied Behavior
- 10.1.4 Floats, Content, and Overlapping

### 10.2 Clearing

### 10.3 Float Shapes

- 10.3.1 Creating a Shape
- 10.3.2 Shaping with Image Transparency
- 10.3.3 Adding a Shape Margin

### 10.4 Summary

## Ch. 11 Positioning

### 11.1 Basic Concepts

- 11.1.1 Types of Positioning
- 11.1.2 The Containing Block

### 11.2 Offset Properties

### 11.3 Width and Height

- 11.3.1 Setting Width and Height
- 11.3.2 Limiting Width and Height

### 11.4 Content Overflow and Clipping

- 11.4.1 Overflow

### 11.5 Element Visibility

### 11.6 Absolute Positioning

- 11.6.1 Containing Blocks and Absolutely Positional Elements
- 11.6.2 Placement and Sizing of Absolutely Positioned Elements
- 11.6.3 Auto-edges
- 11.6.4 Placing and Sizing Nonreplaced Elements
- 11.6.5 Placement on the Z-Axis

### 11.7 Fixed Positioning

### 11.8 Relative Positioning

### 11.9 Sticky Positioning

### 11.10 Summary

## Ch. 12 Flexible Box Layout

### 12.1 Flexbox Fundamentals

- 12.1.1 A Simple Example

### 12.2 Flex Containers

- 12.2.1 The flex-direction Property
- 12.2.2 Other Writing Directions
- 12.2.3 Wrapping Flex Lines
- 12.2.4 Defining Flexible Flows
- 12.2.5 flex-wrap Continued

### 12.3 Arranging Flex Items

### 12.4 Flex Container

### 12.5 Justifying Content

- 12.5.1 justify-content Examples

### 12.6 Aligning Items

- 12.6.1 Start, End, and Center Alignment
- 12.6.2 Baseline Alignment
- 12.6.3 Additional Notes

### 12.7 The align-self Property

### 12.8 Aligning Content

### 12.9 Flex Items

- 12.9.1 What Are Flex Items?
- 12.9.2 Flex Item Features
- 12.9.3 Minimum Widths

### 12.10 Flex-Item-Specific Properties

### 12.11 The flex Property

### 12.12 The flex-grow Property

- 12.12.1 Growth Factors and the flex Property

### 12.13 The flex-shrink Property

- 12.13.1 Proportional Shrinkage Based on Width and Shrink Factor
- 12.13.2 Differing Bases
- 12.13.3 Responsive Flexing

### 12.14 The flex-basis Property

- 12.14.1 The content Keyword
- 12.14.2 Automatic Flex Basis
- 12.14.3 Default Values
- 12.14.4 Length Units
- 12.14.5 Zero Basis

### 12.15 The flex Shorthand

- 12.15.1 Common Flex Values

### 12.16 The order property

- 12.15.2 Tabbed Navigation Revisited

## Ch. 13 Grid Layout

### 13.1 Creating a Grid Container

### 13.2 Basic Grid Terminology

### 13.3 Placing Grid Lines

- 13.3.1 Fixed-Width Grid Tracks
- 13.3.2 Flexible Grid Tracks
- 13.3.3 Fitting Track Contents
- 13.3.4 Repeating Grid Lines
- 13.3.5 Grid Areas

### 13.4 Attaching Elements to the Grid

- 13.4.1 Using Column and Row Lines
- 13.4.2 Row and Column Shorthands
- 13.4.3 The Implicit Grid
- 13.4.4 Error Handling
- 13.4.5 Using Areas
- 13.4.6 Grid Item Overlap

### 13.5 Grid Flow

### 13.6 Automatic Grid Lines

### 13.7 The grid Shorthand

- 13.7.1 Subgrids

### 13.8 Opening Grid Spaces

- 13.8.1 Grid Gutters (or Gaps)
- 13.8.2 Grid Items and the Box Model

### 13.9 Aligning the Grids

- 13.9.1 Aligning and Justifying Individual Items
- 13.9.2 Aligning and Justifying All Items

### 13.10 Layering and Ordering

### 13.11 Summary

## Ch. 14 Table Layout in CSS

### 14.1 Table Formatting

- 14.1.1 Visually Arranging a Table
- 14.1.2 Table Display Values
- 14.1.3 Anonymous Table Objects
- 14.1.4 Table Layers
- 14.1.5 Captions

### 14.2 Table Cell Borders

- 14.2.1 Separated Cell Borders
- 14.2.2 Collapsing Cell Borders

### 14.3 Table Sizing

- 14.3.1 Width
- 14.3.2 Height
- 14.3.3 Alignment

### 14.4 Summary

## Ch. 15 Lists and Generated Content

### 15.1 Lists

- 15.1.1 Types of Lists
- 15.1.2 List Item Images
- 15.1.3 List-Marker Positions
- 15.1.4 List Style in Shorthand
- 15.1.5 List Layout

### 15.2 Generated Content

- 15.2.1 Inserting Generated Content
- 15.2.2 Specifying Content
- 15.2.3 Counters

### 15.3 Defining Counting Patterns

- 15.3.1 Fixed Counting Patterns
- 15.3.2 Cyclic Counting Patterns
- 15.3.3 Symbolic Counting Patterns
- 15.3.4 Alphabetic Counting Patterns
- 15.3.5 Numeric Counting Patterns
- 15.3.6 Additive Counting Patterns
- 15.3.7 Extending Counting Patterns
- 15.3.8 Speaking Counting Patterns

### 15.4 Summary

## Ch. 16 Transforms

### 16.1 Coordinate Systems

### 16.2 Transforming

- 16.2.1 The Transform Functions

### 16.3 More Transform Properties

### 16.4 Summary

- 16.4.1 Moving the Origin
- 16.4.2 Choosing a 3D style
- 16.4.3 Changing Perspective
- 16.4.4 Dealing with Backfaces

## Ch. 17 Transitions

### 17.1 CSS Transitions

### 17.2 Transition Properties

- 17.2.1 Limiting Transition Effects by Property
- 17.2.2 Setting Transition Duration
- 17.2.3 Altering the Internal Timing of Transitions
- 17.2.4 Delaying Transitions
- 17.2.5 The transition Shorthand

### 17.3 In Reverse: Transitioning Back to Baseline

### 17.4 Animatable Properties and Values

- 17.4.1 How Property Values Are Interpolated

### 17.5 Fallbacks: Transitions Are Enhancements

### 17.6 Printing Transitions

## Ch. 18 Animation

### 18.1 Defining Keyframes

### 18.2 Setting Up Keyframe Animations

- 18.2.1 Naming Your Animation

### 18.3 Keyframe Selectors

- 18.3.1 Omitting from and to Values
- 18.3.2 Repeating Keyframe Properties
- 18.3.3 Animatable Properties
- 18.3.4 Nonanimatable Properties That Aren't Ignored
- 18.3.5 Scripting @keyframes Animations

### 18.4 Animating Elements

- 18.4.1 Naming Animations
- 18.4.2 Defining Animation Lengths
- 18.4.3 Declaring Animation Iterations
- 18.4.4 Setting an Animation Direction
- 18.4.5 Delaying Animations
- 18.4.6 Animation Events
- 18.4.7 Changing the Internal Timing of Animations
- 18.4.8 Setting the Animation Play State
- 18.4.9 Animation Fill Modes

### 18.5 Bringing It All Together

### 18.6 Animation, Specificity, and Precedence Order

- 18.6.1 Specifity and !important
- 18.6.2 Animation Order
- 18.6.3 Animation Iteration and `display: none;`
- 18.6.4 Animation and the UI Thread

### 18.7 Seizure and Bestibular Disorders

### 18.8 Animation Events and Prefixing

- 18.8.1 animationstart
- 18.8.2 animationend
- 18.8.3 animationiteration

### 18.9 Printing Animations

## Ch. 19 Filters, Blending, Clipping, and Masking

### 19.1 CSS Filters

- 19.1.1 Basic Filters
- 19.1.2 Color Filtering
- 19.1.3 Brightness, Contrast, and Saturation
- 19.1.4 SVG Filters

### 19.2 Compositing and Blending

- 19.2.1 Blending Elements
- 19.2.2 Darken, Lighten, Difference, and Exclusion
- 19.2.3 Multiply, Screen, and Overlay
- 19.2.4 Hard and Soft Light
- 19.2.5 Color Dodge and Burn
- 19.2.6 Hue, Saturation, Luminosity, and Color

### 19.3 Blending Backgrounds

- 19.3.1 Blending in Isolation

### 19.4 Clipping and Masking

- 19.4.1 Clipping
- 19.4.2 Clip Shapes
- 19.4.3 Clip Boxes
- 19.4.4 Clip Filling Rules

### 19.5 Masks

- 19.5.1 Defining a Mask
- 19.5.2 Changing the Mask's Mode
- 19.5.3 Sizing and repeating Masks
- 19.5.4 Positioning Masks
- 19.5.5 Clipping and Composition Masks
- 19.5.6 Bringing It All Together
- 19.5.7 Mask Types
- 19.5.8 Border-image Masking

### 19.6 Object Fitting and Positioning

## Ch. 20 Media-Dependent Styles

### 20.1 Defining Media-Dependent Styles

- 20.1.1 Basic Media Queries
- 20.1.2 Complex Media Queries

### 20.2 Paged Media

- 20.2.1 Print Styles

### 20.3 Summary