### SWABATS
***Students will be able to use responsive design to create web sites that look good on any device, no matter the size***

	* Responsive Design - Understand how to use percentages max and min to create fluid images and media
	+ Responsive Design - understand how to use iOS orientation bug fix
	+ Responsive Design - understand how to use Modernizr to handle cross-browser compatibility
	+ Responsive Design - understand how to use js media query fix
	+ Responsive Design - Understand how to user viewports to ensure that site scales properly on devices
	+ Responsive Design - understand how to modify type/text with media queries, including column count and size (percentage)
	+ Responsive Design - Understand the benefits of responsive layout
	+ Responsive Design - Understand how to use CSS3 media queries - best support for all, print and screen for now
	+ Responsive Design - Understand the options for Desktop Down vs. Mobile Up

### Motivation
I spend a lot of time on my iPhone and one of my biggest pet peeves is when I click on a link from an email or try to google something and the website that I go to asks me to download an app OR the page looks so cluttered and the text is so tiny that I can’t find what I’m looking for. I don’t want to download your stupid app! I just want to go to a site that looks good on my phone and works. That is what responsive web design is all about. Making websites that look good across screens and devices so people can view your page from the device of their choice.

### Lesson Plan
+ There are a couple of different ways to build responsive sites. 
+ You can start out with your desktop site and decide how you want to modify your page for smaller and smaller screens.
+ Or you can think about what your page will look like on a smaller screen - decided which content is most important - then think about what else you can add to the page for larger screens with more space. 
+ There is a big movement towards mobile first design - since so many people access websites on their phone - but it’s up to you. 
+ Either way you should think about the content and layout and draft up mockups for what you want your site too look like before you launch into modifying your code.

<img src="https://s3.amazonaws.com/after-school-assets/Screenshot+2015-04-23+10.18.37.png">

+ Some nice examples of responsive sites:
	+ http://www.sasquatchfestival.com/
	+ https://www.ableton.com/
	+ http://www.tilde.io/ 
	+ http://www.worldwildlife.org/
	+ https://css-tricks.com/
	+ https://dribbble.com/ 
	+ https://www.khanacademy.org/
+ You can make your layout responsive using some of the strategies we’ve already talked about in class - like using percentages, ems and max and min width and heights.
+ To apply certain CSS rules to a page based on the size of the screen we use something called CSS media queries. They look like this:
	```css
	 @media only screen and (max-width:800px) {
	 p { color: green; }
	 }
	```
+ They all start with` @media` followed by [not|only] and then the type of media. There are lots of different types but right now these are the three media types that have the best support (and will be the most useful for you):
	+ `all`	-	All Devices (default)
	+ `print`	-	Printing or print preview
	+ `screen`	-	Computer screen
+ The `and` let’s you add another condition to check for and in most cases that will be the width of the screen.
	+ You can also use a `,` if you want to set up an `or` condition
+ The CSS that you put inside of an `@media` query will only apply to screens that fit the criteria of the @media query. For example if we set up this CSS:
	```css
	 p { color: red; }
	 @media only screen and ( max-width: 800px ) {
       p { color: green; }
	 }
	 ```
	* Our screen would look something like this:

<img src= "https://s3.amazonaws.com/after-school-assets/responsive_design1.png">

+ And if we had a media query like this
	```css
	p { color: red; }
	 @media only screen and ( min-width: 400px ) {
   	 p { color: green; }
	 }

<img src= "https://s3.amazonaws.com/after-school-assets/responsive_design3.png">

+ The types of elements that you will want to think about when setting up a responsive site are:
	+ Media - images, audio and video players
	+ Text
	+ Layout - the size of you divs, number of columns, etc.
	+ Meta Device Width and Zoom Settings
	+ Browser Support and JavaScript Fixes
+ Media: In general to make your media responsive consider using percentages like this:
		+ img, table, form, input, video, audio, {
    	+ width: 100%;
    	+ max-width: 100%;
		+ }
		+ [Example](http://jsfiddle.net/flatiron_school/HP6A3/)
+ Text: The best way to make text responsive is to use ems rather than pixels for measurement. 
		+ In general 1em is equal 16px and [here](http://pxtoem.com/ ) is a helpful site for conversions
		+ You can reset this standard body font-size in your media queries though to adjust the text of the entire site to be larger or smaller on different screens while maintaining their proportional relationships.
		+ For example:
		```css
		body { font-size: 100%; }
		 h1 { font-size: 2.5em; } p { font-size: 1em; }   
		 @media only screen and (max-width: 768px) {
    	 body {
         	font-size: 90%;
          }
		 } 
		```
		+ [Example](http://jsfiddle.net/flatiron_school/H6cN5/)
	+ Additionally, elements like paragraphs can set their column  
		```css
		@media only screen and (min-width: 480px) {

 		 article p {
     	 -moz-column-count: 2;
     	 -webkit-column-count: 2;
     	 column-count: 2;      
  		 }
		 }
		 ```
		+ [Example](http://jsfiddle.net/flatiron_school/vy43K/2/)
+ Layout: Using percentages and max and min widths will be necessary to set up a responsive layout but one other important thing is to decide breaking points.
	+ Breaking points are the screen widths where, for example, your 3 column layout may no longer look good and you want to switch to one column instead.
	+ Let your content determine where breakpoints should fall. Use Developer Tools and Emulators to discover where your content starts to break down. Then create an appropriate breakpoint (media query at that width) to solve the issue. This will ensure that your content looks good on any and all devices not just the popular ones.
		+ The [device mode in Chrome](https://developer.chrome.com/devtools/docs/device-mode) can be helpful with this
	+ Here are some examples of how you might use media queries to modify your layout:
	```css
		.wrapper { width: 960px; }
		 @media only screen and (max-width: 980px) {
  		 .wrapper {
   		 width: 90%;
  		 }
		 }
		 .col-1 { width: 33%;  float: left; }
		 @media only screen and (max-width: 320px) {
  		 .col-1 {
    	 width: 100%; float: none;
  		 }
		 }
		 ```
		+ [Example](http://jsfiddle.net/flatiron_school/jERBH/)
+ Other things to worry about:
	+ Some small screens will automatically try to resize your content to fit and ignore your media queries. To fix that you’ll need to add this meta data to the headers on your pages:
		+ `<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0">`
			+ Prevents devices from zooming out or in and instead rely on the media query styling to change the layout accordingly
	+ There is also an orientation bug on iPhones that can be fixed with this:
		+ iOS Orientation Zoom Fix is a JavaScript file that corrects a zoom bug on Apple Devices like the iPhone.
		+ Download from:https://raw.github.com/Wilto/iOS-Orientationchange-Fix/master/ios-orientationchange-fix.js
			+ `<script src=”js/ios-orientationchange-fix.js"></script>`
	+ Not all media queries work in IE so there is another fix for that:
		+ Media Queries Fix gives support for media queries to work in older versions of IE.
		+ http://css3-mediaqueries-js.googlecode.com/svn/trunk/css3-mediaqueries.js
		+ `<script src="http://css3-mediaqueries-		+ js.googlecode.com/svn/trunk/css3-mediaqueries.js"></script>`
	+ You can also get a media queries fix when you download Modernizr:

<img src="https://s3.amazonaws.com/after-school-assets/responsive_design2.png">
