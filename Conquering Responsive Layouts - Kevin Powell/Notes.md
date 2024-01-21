## Conquering Responsive Layouts - by Kevin Powell [.](https://courses.kevinpowell.co/view/courses/conquering-responsive-layouts)

### Responsive Layouts are found in nature!!

#### Using Percentages and avoiding heights

- HTML is responsive by default, if it is breaking, IT'S OUR FAULT!!
- Percentage of the child is the percentage for the width/height that of the parent. the upward hierarchy to find the defined height/width continues up until `<body>` and `<html>` if defined parameter not found.
- Avoid giving defined heights (in pxs or even ems or rems), the block is responsive by default.
- Read more abt the code [here](./codesnippets/percents-and-heights.html)

#### Em vs Rem

- The `em` unit allows setting the **font size of an element relative to the font size of its parent**. When the size of the parent element changes, the size of the child changes automatically.
- The `rem` is based upon the font-size value of the root element, which is the `<html>` element. And if the `<html>` element doesn’t have a specified font-size, **the browser default value of 16px is used**. So here only the value of the root is considered, and there is no relation with a parent element.

- `rem` unit is better considered for using throughout the application for setting font sizes, padding, margin, etc. But in cases of ***relative spacing, padding and not font sizing, inside the same parent***, `em` are more useful.

- Watch this [video by Kevin powell](https://youtu.be/pautqDqa54I) for more understanding.

- `em` also has a `compounding width issue`, where the child is `2em`, i.e twice the size of the parent who in turn is `2em` that is 2 times its parent ---> therefore the child effectively becomes `4em` the width we wanted it!!! 

- [codepen](https://codepen.io/SGueddes/pen/gBwGrz)

#### why max-width?

- If we keep the width too fluid the things may go out of hand. Therefore, its suggested to have a limit to how much the things can grow. Here, the concept of `max-width` comes in for larger screen sizes.
- Many professionally designed websites have this implemented in order to preserve the structure and have better control on the layout of the website.
- Read more abt the code [here](./codesnippets/enter-max-width.html)

#### vw, vh, dvh/w, svh/w, vmin, vmax

- `vh` or `vw` was described as Equal to 1% of the height/width of the **initial containing block**.
- A dynamic `vh` unit was not great, so they changed it to be a static unit equal to the size of the viewport when the browser UI was its smallest (and the content / "view size" was the largest).
- `vw` are a great measure for defining font-sizes for the hero sections' headers. Not for the paragraphs though.

- In 2019, some new units were born, they were large, small, dynamic and traditional units. Check this [blog](https://dev.to/frehner/css-vh-dvh-lvh-svh-and-vw-units-27k4#large-viewport-units) or [this](https://www.terluinwebdesign.nl/en/css/incoming-20-new-css-viewport-units-svh-lvh-dvh-svw-lvw-dvw/) one's better
  - The large viewport-percentage units (lv*) are defined with respect to the large viewport size: the viewport sized assuming any UA interfaces that are dynamically expanded and retracted to be retracted.
  - The small viewport-percentage units (sv*) are defined with respect to the small viewport size: the viewport sized assuming any UA interfaces that are dynamically expanded and retracted to be expanded.
  - The dynamic viewport-percentage units (dv*) are defined with respect to the dynamic viewport size: the viewport sized with dynamic consideration of any UA interfaces that are dynamically expanded and retracted. This allows authors to size content such that it can exactly fit within the viewport whether or not such interfaces are present.
  - The UA-default viewport-percentage units (v*) are defined with respect to a UA-defined UA-default viewport size, which for any given document should be equivalent to the large viewport size, small viewport size, or some intermediary size.

### Flexboxes are truly useful!!

- Earlier we used to use `float`s and `clear`s to create the layouting, which used to cause 99 different problems.
- We can make `div`s responsive by giveing percentage widths, but to make them more dynamic and useful -use **Flexs**.
- To convert a `div` into a **flex container**, we just change --- `display:flex;`. Default direction of flex container is **row**.
- The children of the flex-container called as **flex-items**, and all the children are converted into flex too but with `flex-direction:column;`
- `Div`s have default width set as 100% but `Flex-items` usually try to shrink to the **smallest size possible**. If there is no content in a flexbox, it'll disapper from the view!!

- Adding spacing between adjacent flex-items in flex container flex-direction:row
  1. gap property of flexbox - gap:100px -- add it in the same class where you declare display:flex;
      > gap property is experimental(now supported in all browsers) and is only availalbe in Firefox, check it on - [can I use? gap](https://caniuse.com/?search=gap)
  
  2. Adjacent combinator in CSS (+): here set a left margin in the combinator (.flex-item + .flex-item {}). It checks for the items that satify the condition.

### Vertically challenging Flexboxes

- We know, when we convert a `div` into a `display: flex;`, the immediate children of the `div` turn into the **Flex-Items** too.
- All the flex-items, in the flex, are strechted to the same height!!
- To vertically distribute the elements evenly, we can --- 
  - Either use margins - but maintaining them is very troublesome
  - Or use `justify-items` or `justify-content` to align the items.

- For large contents that should not overflow in small screens, give `min-height`.

### Working with NavBars

- Navbars are generally the strips are the header that hold tabs for navigation to different pages/sections of the website.
- `<nav>` tag is used to enclose the nav items (which can be lists of anchor tags made into buttons, divs, buttons, etc) and are grouped at the header of the page.
- using `<nav>` tag is important when considering accessibility into account, like screen-readers, etc.
- Find an example of navbar and how t arrange it [here](./codesnippets/challenges/challenge06-navbar/challenge06-navbar.html)

### Working with images

- Generally the images gets stretched and distorted in order to fill all the empty space.
- **One of the important set-up to do is to set up** `max-width` property, `max-width` property is set to 100%, **the image will scale down if it has to, but never scale up to be larger than its original size.**

- In this [Example](./codesnippets/challenges/challenge06-navbar/challenge06-navbar.html), we have used a div wrapper around the `img` tag. The div is the one that will distort leaving the image unfazed.
- `img` tag was aligned to the `flex-start` using `align-self: flex-start` (which aligns only itself and does not affect other elements). **Also, to make all the images responsive along the lines of the div-wrappers, use img { max-width: 100% } everytime!!**

#### \<picture\> tag

- The HTML `<picture>` element gives web developers more flexibility in specifying image resources.
- Instead of having one image that is scaled up or down based on the viewport width, **multiple images** can be designed to more nicely fill the browser viewport.
- The `<picture>` element works similar to the `<video>` and `<audio>` elements. We set up different sources, and the first source that fits the preferences is the one being used:

    ```css
      <picture>
        <source srcset="img_smallflower.jpg" media="(max-width: 400px)">
        <source srcset="img_flowers.jpg">
        <img src="img_flowers.jpg" alt="Flowers">
      </picture>
    ```

  - The `srcset` attribute is required, and defines the source of the image.
  - The `media` attribute is optional, and accepts the media queries you find in CSS @media rule.
  - **We should also define an `<img>` element for browsers that do not support the `<picture>` element**.

### min, max, clamp()

- We have seen that we set certain restrictions on the elements like containers that form the layout on different screens, like - 
  ```css
    width : 60%
    max-width: 1500px
  ```
- There is a new shorthand introduced for the above use-case, i.e `min()`, `max()` and `clamp()`. And it let's us do, so many things.
- We can refactor the above the css definition as -- 
  ```css
  width : min(60%, 1500px)               // we can add multiple value too like min(500px, 15%, 5rem) depending on the use case
  ```
- We can also perform mathematical operation in the parenthesis -- just make sure that even spacing is added around the operator. ' * ', 
  '5rem +20%' <-- is not allowed --
  ```css
  width : max(500px + 15%, 1500px)
  ```
- We can even nest the max, min operators -- `max-width : min( max(150px, 30%), min(100vw - 2rem, 3em))`

#### Clamp
- `clamp(min, val, max)` -- clamps a middle value within a range of values between a defined minimum bound and a maximum bound.
- The preferred value is the expression whose value will be used as long as the result is between the minimum and maximum values.
- `clamp(MIN, VAL, MAX)` is resolved as `max(MIN, min(VAL, MAX))`.

- **The rem changes when we press zoom in the browser window of desktop sites.**
- **For bigger Typography, we can give sizes in viewport units, but it can cause a issue when the viewport becomes too small. Clamp can help us resolve that issue.**
 
  eg, `font-size : clamp(2rem, 5vw, 8rem)`

### Media Queries

- Media Queries are one of the most important tool when it comes to the responsive design paradigm.
- Media queries can be used to check many things, such as:
  1. width and height of the viewport
  2. width and height of the device
  3. orientation (is the tablet/phone in landscape or portrait mode?)
  4. resolution

- A media query consists of a **media type** and **can contain one or more expressions, called media features**, which resolve to either true or false.

    ```css
    @media not|only mediatype and (expressions) {
      CSS-Code;
    }
    ```

- You can also have different stylesheets for different media:
  `<link rel="stylesheet" media="mediatype and|not|only (expressions)" href="print.css">`

- check this for more proper knowledge of deciding CSS breakpoints - [here](https://www.freecodecamp.org/news/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862/)

**The tl;dr of the article: Use `600px, 900px, 1200px, and 1800px` if you plan on giving the giant-monitor people something special. **

### View port 

- The viewport is the user's visible area of a web page. The viewport varies with the device, and will be smaller on a mobile phone than on a computer screen.

- The early webpages were designed for big desktop screens only. Then, when we started surfing the internet using tablets and mobile phones, fixed size web pages were too large to fit the viewport. To fix this, browsers on those devices scaled down the entire web page to fit the screen.

- HTML5 introduced a method to let web designers take control over the viewport, through the <meta> tag.
    
    `<meta name="viewport" content="width=device-width, initial-scale=1.0">`

    - The `width=device-width` part sets the width of the page to follow the screen-width of the device (which will vary depending on the device).
    - The `initial-scale=1.0` part sets the initial zoom level when the page is first loaded by the browser.

- Users are used to scroll websites vertically on both desktop and mobile devices - but not horizontally!

  Some additional rules to follow:

  1. **Do NOT use large fixed width elements** - For example, if an image is displayed at a width wider than the viewport it can cause the viewport to scroll horizontally. Remember to adjust this content to fit within the width of the viewport.

  2. **Do NOT let the content rely on a particular viewport width to render well** - Since screen dimensions and width in CSS pixels vary widely between devices, content should not rely on a particular viewport width to render well.

  3. **Use CSS media queries to apply different styling for small and large screens**

  source - [W3Schools](https://www.w3schools.com/css/css_rwd_viewport.asp)

