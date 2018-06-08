# sfadmin-training-javascript13
## Hour 13
## Introducing CSS3

What You’ll Learn in This Hour:

    Some of the new abilities CSS3 brings to CSS
    Using vendor-specific prefixes and extensions
    Cross-browser setting of CSS3 properties
    Setting CSS3 properties efficiently in JavaScript

Using CSS3 you can easily achieve plenty of cool new effects without having to use lots of JavaScript code and/or external graphics applications such as Photoshop. You can create rounded borders, add shadows to boxes, use an image as a border, and more. CSS3 contains several new background properties that give you more control over background elements, including multiple background images, while CSS3 gradients let you display smooth transitions between two or more specified colors. New text features include text shadows and word wrap, as well as easy use of web fonts. And CSS3 lets you easily build really cool transitions, transformations, and animations.

In this hour you’ll get a flavor of what CSS3 can do for your web pages, and you’ll see how to effectively control CSS3’s capabilities using JavaScript.
### Vendor-Specific Properties and Prefixes

CSS vendor prefixes are a way for the browser companies to add support for new or experimental CSS features before they become part of the formal CSS3 specification, or to implement features of a specification that hasn’t yet been finalized. In due course, these prefixes usually become unnecessary as the features become fully supported via their standard CSS3 nomenclature. To make sure that your pages render as you want them to in the maximum number of browsers, though, it pays to use prefixes.

The CSS3 browser prefixes you’re likely to need appear in Table 13.1.
Image

TABLE 13.1 Vendor Prefixes for CSS3

In most cases, where a prefix is necessary you take the CSS3 property as listed in the CSS3 specification and add the relevant prefix from Table 13.1 for the browser in use. For example, later in this hour you’ll read about CSS3 transitions. There you’ll see that, if you want to add a CSS3 transition to your page, you use the transition property with the prefixes added first:

Tip

At the time of writing there’s a really useful roundup of which feature/browser combinations require a prefix at http://shouldiprefix.com/.

For a frequently updated list of which features are supported by a particular browser and version, visit
http://www.w3schools.com/cssref/css3_browsersupport.asp.

-webkit-transition: background 0.5s ease;
-moz-transition: background 0.5s ease;
-o-transition: background 0.5s ease;
transition: background 0.5s ease;

The user’s browser will respond to whichever version of the transition feature it understands, ignoring the rest.

Thankfully, browser manufacturers are working hard at fully implementing all of the CSS3 features, and for most modern browsers the number of properties requiring a prefix is falling quickly.
### CSS3 Borders

CSS3 lets you do some really cool things with borders that were only previously possible with lots of ugly, hard-to-maintain code hacks.

In this section we’ll look at two examples: box shadows and rounded corners.
Create Box Shadows

The box-shadow property lets you add drop shadows to your page’s box elements. As Table 13.2 shows, you can separately specify values for color, size, blur, and offset:
Image

TABLE 13.2 Parameters for the box-shadow Property

Here’s an example using a 10px-wide shadow heading down and to the right, blurred across its full width, and colored mid-grey:

#div1 {
background-color: #8080ff;
width: 400px;
height: 250px;
box-shadow: 10px 10px 10px #808080;
-webkit-box-shadow: 10px 10px 10px #808080;
-moz-box-shadow: 10px 10px 10px #808080;
}

In Figure 13.1 you can see an example of this style applied to a <div> element in a web page.
Image

FIGURE 13.1 A CSS3 box shadow
#### Rounding Corners with the border-radius property

The border-radius property lets you add rounded corners to your page elements without the need for specially created corner images, and is perhaps one of the most popular features new to CSS3.

The border-radius property already has widespread browser support, though Mozilla Firefox required the -moz- prefix for a little longer than some of its rivals; therefore, if you need to support Firefox back several versions you should consider including the prefixed version too:

#div1 {
-moz-border-radius: 25px;
border-radius: 25px;
}

In Figure 13.2 you can see an example of a <div> element styled with radiused corners.
Image

FIGURE 13.2 A CSS3 border radius

Rounded corners can be specified independently using the individual properties border-bottom-left-radius, border-top-left-radius, border-bottom-right-radius, and border-bottom-right-radius, or for all four corners in one statement by using the border-radius property, as we’ve done here.

Caution

The prefixed version of a property might not always be exactly the same as the property as described in the CSS3 specification.

Even though vendor-specific extensions usually avoid conflicts (as each vendor has a unique prefix), please remember that such extensions may also be subject to change by the vendor, as they do not form part of the CSS3 specifications, even though they try to behave like the forthcoming CSS3 properties.

Remember, too, that the vendor-specific extensions will almost certainly fail CSS validation.
### CSS3 Backgrounds

CSS3 contains several new background properties that allow more control of the background element.

In this section you’ll learn about the background-size and background-origin properties, as well as how to use multiple background images.
#### The background-size Property

The background-size property adds a new feature to CSS that allows you to set the size of your background images using lengths, percentages, or either of two keywords, contain or cover.

Specifying the background size using lengths and percentages behaves as you might expect. For each background image, two lengths or percentages can be supplied, relating to the width and height, respectively. (When you use percentages, these relate to the space available for the background, not to the width and height of the background image.)

The auto keyword can be used in place of either the width or the height value. If you specify only one value for background-size, this will be assumed to be the width. The height will then default to auto.

#div1 {
background-size: 400px;
background-image: url(lake.png);
width: 400px;
height: 250px;
border-radius: 25px;
}

Here I’ve set the background width equal to the size of the <div> element (I’ve also rounded the corners for good measure). The result is shown in Figure 13.3.
Image

FIGURE 13.3 Setting background size in CSS3
#### The background-origin Property

The background-origin property is used to set how the position of a background in a box is calculated.

It takes one of three values: padding-box, border-box, or content-box.

When you supply a value of padding-box, the position is relative to the upper-left corner of the padding edge. With border-box it’s relative to the upper-left corner of the border, and content-box means the background is positioned relative to the upper-left corner of the content.
#### Multiple Background Images

CSS3 lets you use multiple background images for box elements, simply by employing a comma-separated list. The order of the list is important, with the first value supplied representing the layer closest to the user, and subsequent entries in the list being rendered as layers successively further behind it. Here’s an example:

#div1 {
width: 600px;
height: 350px;
background-image: url(boat.png), url(lake.png);
background-position: center bottom, left top;
background-repeat: no-repeat;
}

Here, boat.png is a drawing of a yacht upon a transparent background, while lake.png is a photograph. In Figure 13.4 you can see the result when applied to a <div> element within a web page.
Image

FIGURE 13.4 Using multiple images in CSS3 backgrounds

Browser support for the multiple backgrounds feature is already quite established, with Mozilla Firefox (3.6+), Safari/Chrome (1.0/1.3+), Opera (10.5+), and Internet Explorer (9.0+) offering support.
### CSS3 Gradients

CSS3 gradients allow you to generate smooth transitions between two or more specified colors, where previously you had to employ images to achieve these effects. With CSS3 gradients you can reduce the download time, cache memory, and bandwidth usage that these images would have cost. CSS3 gradients perform better when zoomed, too.

CSS3 offers two types of gradient: Linear Gradients, directed down/up/left/right/diagonally, and Radial Gradients, directed outwards from a defined center.
#### Linear Gradients

To create a linear gradient in CSS3, you must define at least two colors to serve as the end points of the gradient. You can also define a starting point and a direction (that is, top to bottom, left to right, or an angle) for the gradient effect.

#div1 {
  width: 600px;
  height: 350px;
  background: -webkit-linear-gradient(red, #6699cc);
  background: -o-linear-gradient(red, #6699cc);
  background: -moz-linear-gradient(red, #6699cc);
  background: linear-gradient(red, #6699cc);
}

Here I’ve mixed the ways the colors are defined, using both color names (here red) and #rrggbb notation. I haven’t specified a direction for the gradient, so the default top-to-bottom will be used by the browser, as shown in Figure 13.5.
Image

FIGURE 13.5 A CSS3 linear gradient

You can also enter a direction for the gradient; for instance, suppose you want the gradient to be directed left-to-right instead of top-to-bottom, like so:

background: linear-gradient(to right, red , #6699cc);

The following line defines a diagonal gradient:

background: linear-gradient(to bottom right, red , #6699cc);

If you want total control over the direction of the gradient, define an angle:

background: linear-gradient(135deg, red, #6699cc);
#### Radial Gradients

A radial gradient is defined by its center and (like its linear counterpart) must have at least two colors defined to act as end points for the gradient effect:

background: radial-gradient(red, #6699cc);

A radial gradient specified this way displays as shown in Figure 13.6.
Image

FIGURE 13.6 A CSS3 radial gradient

You can also set a location parameter for the center of the radial gradient, using the at keyword:

background: radial-gradient(at top left, red, #6699cc);

The result is shown in Figure 13.7.
Image

FIGURE 13.7 Moving the center of the radial gradient

Tip

CSS3 gradients can do much more than I have space to describe here, including the use of more than two colors, transparency, and modifications to the shape and size of the gradient. You can even add multiple gradients to the same element. Full details are in the W3C documentation:
http://www.w3.org/TR/2011/WD-css3-images-20110217/
### CSS3 Text Effects

CSS3 contains some new features to help you manipulate text.
#### Text Shadow

In CSS3, the text-shadow property applies shadow to text in a way almost identical to the box-shadow property for block elements. You specify the horizontal and vertical shadow distances and optionally the blur distance and the color of the shadow:

h3 {
 text-shadow: 10px 10px 3px #333;
 font-size: 26px;
}

You can see an example displayed in Figure 13.8.
Image

FIGURE 13.8 CSS3 text shadow
#### Word Wrap

If a word is too long to fit within the block element containing it, it overflows beyond its container. In CSS3, you can use the word-wrap property to force the text to wrap, even if has to wrap in the middle of a word:

p {
    word-wrap: break-word;
}
### CSS3 Transitions, Transformations, and Animations

Traditionally, programmers have used custom JavaScript code to create movement in page elements, which can be tricky to implement in a cross-browser way. It would be better if there were easier ways to add simple effects to elements on the page.

These capabilities are currently being introduced in CSS3, in the form of transitions, transformations, and animations. They already have support to varying degrees in most browsers.

In the following simple example, we add a transition effect (in those browsers that support it) to change the background color on link hover. As the background color changes, a transition effect will smooth out the transformation.

Here’s the code for our example link:

<a href="somepage.html" class="trans" id="link1">Show Me</a>

Following are the CSS declarations showing the original and hover background colors, and the declarations used to carry out the transition effect in the various different browsers. Note the range of different prefixes required, as discussed earlier in this hour. The last declaration, without a prefix, will be the one required once the technology moves from an experimental to a finished status.

a.trans {
    background: #669999;
    -webkit-transition: background 0.5s ease;
    -moz-transition: background 0.5s ease;
    -o-transition: background 0.5s ease;
    transition: background 0.5s ease;
}
a.trans:hover {
    background: #999966;
}

Note

You can find comprehensive information about CSS3 transitions, transformations, and animations at
http://css3.bradshawenterprises.com/all/.
### Referencing CSS3 Properties in JavaScript

The combination of CSS3 and JavaScript promises some great effects with slick performance, high reliability, and minimum code complexity. In this section we look at some ways to get and set CSS3 properties successfully from within your JavaScript code.
#### Converting CSS Property Names to JavaScript

As I mentioned in Hour 12, “JavaScript and CSS,” to make the names of CSS properties compatible with JavaScript naming conventions, CSS property names need a small conversion from the format they have in stylesheets.

Instead of using lowercase names and hyphens as they do in CSS, the JavaScript versions have the hyphens removed and the following characters capitalized. Hence, border-radius becomes borderRadius. Property names having no hyphens, such as width, are unchanged.

You saw in Hour 12 how to access element style properties using this naming convention along with the DOM style property:

var bRad = document.getElementById("div1").style.borderRadius;

As I mentioned at that time, while this can be useful, it is limited to elements with inline styles; for elements with CSS declarations grouped in <style> elements in the page head, or in external files, it won’t work. Luckily, there’s a better way, which I’ll discuss now.
#### The DOM getComputedStyle() Method

Nowadays nearly all browsers support the DOM getComputedStyle() method, which accesses the final (that is, computed) style of an element. By final style, we mean the style in which the browser finally displays the element after applying (in their appropriate order) all of the styling rules relevant to that element, be they inline, external, or inherited from container elements.

The getComputedStyle() method returns an object having various methods, including getPropertyValue(property), which returns the current value for the given CSS property name:

var myDiv = document.getElementById("div1");
var bRad = getComputedStyle(myDiv).getPropertyValue("borderRadius");

Try It Yourself: Controlling Lighting Effects

Video 13.1—Controlling Lighting Effects

Let’s create a small application to use box-shadow and radial-gradient, both controlled by JavaScript, to control lighting effects in a simple HTML page. The code is shown in Listing 13.1.

LISTING 13.1 Controlling CSS3 Effects

First, take a look at the <body> section of the page. It’s very simple, containing just two nested <div> elements, the inner one containing three buttons, labeled Top Left, Top Right, and Bottom, respectively.

Returning to the <head> section of the page, you’ll see that the window.onload event causes the attachment of an onclick event handler to each of these buttons. In each case, the event handler changes the gradient of the outer <div> element’s background and the direction of the box-shadow style of the inner <div> element. The combined effect is to simulate a light source emanating from one of three directions.

You can see the page in action in Figure 13.9.
Image

FIGURE 13.9 Controlling CSS3 with JavaScript

Note how there are no images used to create these effects—something that wouldn’t have been possible prior to CSS3.
### Setting CSS3 Properties with Vendor Prefixes

So you’ve seen how to get a CSS property, but how can you set a CSS3 property using JavaScript when different browsers support different variations of the property (that is, having different prefixes)?

When a browser supports a particular CSS property, it returns a string value when you request the property from a page element. (This will be an empty string if the property has not yet been set.) If your browser doesn’t support the property, the value undefined is returned instead. So you can easily carry out a test before setting a CSS3 property to determine which variant of the property is supported.

Let’s write code that accepts an array of potential CSS3 properties and returns the one supported by the browser.

function getCss3Property(properties){
    // loop through all possible property names
    for (var i=0; i<properties.length; i++) {
        // if the property exists for this element
        if (properties[i] in document.documentElement.style) {
            // return the associated string
            return properties[i];
        }
    }
}

With this we can return the appropriate version of the feature.

Let’s see how that might work for the transition used earlier in this hour:

//get the correct CSS3 transition property
var myTrans = getCss3Property(['transition', 'MozTransition', 'WebkitTransition',
'msTransition', 'OTransition'])

//set CSS transition for "link1"
document.getElementById("link1").style[myTrans] = "background 0.5s ease" ;

Let’s suppose that I’m using a version of Firefox that doesn’t support the CSS3 transition property, but does support Mozilla’s own version, MozTransition (corresponding to -moz-transition).

When called, the getCss3Property() function will begin to loop through the list of transition properties corresponding to the various vendor types. Having returned a value of undefined for the property transition (as the browser does not support it) it will, on the following trip through the loop, exit the function, returning a string value of MozTransition. We now know which version of the property to set in the following line of code.
### Summary

In this hour you learned about some of the new capabilities that CSS3 brings to web design. You saw how different browser manufacturers implement new or experimental CSS3 features via custom prefixes, and saw how you can access and set these custom features using JavaScript.
### Q&A

Q. What browsers currently support CSS3 transitions, transforms, and animations?

A. At the time of writing, 2D transforms are available in all popular current browsers, while 3D transforms are supported in Safari, Chrome/Chromium, and Firefox. Transitions and 3D transforms were added in IE10. Most of these effects degrade sensibly, so a user having a browser without support will still be OK, but will see the page elements without animation.

Q. Why do several different browser vendors use the -webkit- prefix?

A. WebKit is a layout engine used for rendering web pages in web browsers. The webkit engine is the basis of a number of popular browsers, including Safari, Chrome/Chromium, and various other browsers for both desktop and mobile platforms.

### Exercises

    Using the individual properties border-bottom-left-radius, border-top-left-radius, border-bottom-right-radius, and border-bottom-right-radius, use JavaScript to style a <div> element to be completely elliptical in shape. (Hint: Set the radius sizes such that all of the element’s border is within the radius of exactly one corner.) Use getComputedStyle() on your elliptical <div> to then report these border radii to the console.
    In this hour’s “Try It Yourself” section, the box shadow direction was set manually, while you were writing the code, to be appropriate to the simulated lighting direction. Can you write a function in JavaScript to set the shadow properties based on the detected value of the background gradient?
