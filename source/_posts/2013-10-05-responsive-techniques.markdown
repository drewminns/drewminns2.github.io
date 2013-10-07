---
layout: post
title: "Responsive Techniques"
date: 2013-10-05 15:24
comments: true
categories: 
---

###Exercise Files
[https://github.com/drewminns/Week-5](https://github.com/drewminns/Week-5)

#Accessibility

The web is constantly changing and it is difficult to create something futuristic today that will still be futuristic tomorrow. There are no ways to force browser upgrades. Users and organizations will not change their technologies due to developer demand, mainly due to ignorance of available tools.

Accessibility is important to ensure that all users are supported no matter what browsing technology they are using.

A site that works on a wider variety of devices will have a much larger reach than one that doesn't.

Web design is a fine game of looking backwards while working forwards. You need to continue to use modern technologies while ensuring that you are not cutting off a market of your users.

Two planes of thought exist when approaching a project: graceful degradation and progressive enhancement.

##Graceful Degradation
The idea of building a site that will work well in modern browsers and then providing fallback support in older browsers. The fallback support may not be as 'pretty' as on the most modern browser, but basic functionality will still exist.

An example of graceful degradation is PNG's with alpha transparencies. IE6 browsers will show the image but ignore the transparency and replace it with a white area. There are tools that can provide this functionality, but the best way is provide a gif fallback for older browsers.

##Progressive Enhancement
The concept of Graceful Degradation but in reverse.  Developing an experience for a base-level of users and adding functionality when the browser supports it.

Example:
Providing a Javascript built image slider will work on more devices than a CSS one.

###Which one is better?
Ultimately it depends. It depends on what you are trying to accomplish. Many sites completely ignore accessibility, not only for users but for browsers. Progressive enhancement is more widely used as ideologies shift to simpler user experiences and less flashy cosmetic uses.

#Tools to use
There are many tools that exist to bring older browsers in line with modern ones. These can be used to ensure correct semantics, design tools and more are usable by all your audience.

###HTML5 Shiv
[https://code.google.com/p/html5shiv/](https://code.google.com/p/html5shiv/)

A javascript tool used to enable styling of HTML5 elements in browsers prior to IE9. Before IE9, these elements were not part of the spec and therefore not recognized as block elements within CSS. 

**Usage**

  
###CSSPie
[http://css3pie.com/](http://css3pie.com/)

A javascript that allows IE6-9 to identify and render several of CSS3's features. The tools it provides, that IE6-9 was missing are: border-radius, box-shadow, border-image, multiple background images and linear-gradient as background image.

**Usage**

Include the 'behavior: url(path/to/pie_files/PIE.htc);' property along with the path to your CSS3 files in your style rule.

  #myAwesomeElement {
    border: 1px solid #999;
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    border-radius: 10px;
    behavior: url(path/to/pie_files/PIE.htc);
  }

###Modernizr
[http://modernizr.com/](http://modernizr.com/)

Utilizing feature detection to detect whether a browser supports the latest web technologies, Modernizr is the most widely used tool to work with progressive enhancement, as it provides tools to write conditional code, based on the browser. The basic download of modernizr includes HTML5 Shiv and other tools to ensure CSS3 features are included.

**Usage**

  <!DOCTYPE html>
   <html class="no-js">
    <head>
    <title>Modernizr - Javascript Example</title>
 
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js" type="text/javascript"></script>
    <script src="modernizr.js" type="text/javascript"></script>
    <script type="text/javascript">
      $(document).ready(function()
      {
      if (Modernizr.boxshadow)
      {
        $("#result").html('Your browser has support for Box-Shadow');
      }
      else
      {
        $("#result").html('Your browser does not support Box-Shadow');
      }
      });
    </script>
    </head>
    <body>
    <p id="result"></p>
     </body>
   </html>
   
#EM
Using EM sizes for fonts increase accessibility for your site, because it allows the fonts used throughout to be set according to the font size that the user finds comfortable. By default, most browsers use a default font of 16px, which is recognized as 1em. 

Of course this can be changed many ways, the base font can be set within the html and all children will use that sizing, or if the user has set a larger base font size, the default size they have set will be recognized as 1em.

To facilitate accessibility for users with visual disabilities and for different screen sizes, it is crucial to not set a base font in order for fonts to appear correctly.

#SVG
Scalable Vector Graphics are a relatively new addition to HTML and allow for scalable graphics to be used in a webpage without the worry of pixelation when sized larger.

SVG's are defined through an XML film and can be created within programs such as Illustrator. 

They are useful within Responsive Design because of their ability to be modified through code to fit different screen sizes and resolution. They are particularly useful when used for a Retina display application because they suffer no loss of quality when viewed at higher resolutions.

There are several ways to work with svg's and each depends on the purpose.

SVG's can be displayed just like any other image format and have it's size modified through width and height.
  
  <!img src="image.svg">
  
SVG's can also be displayed by inserting the full XML output onto the page. While this can create a cumbersome page, it allows for more control of it's design.

  <!svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
   width="242.883px" height="153.923px" viewBox="0 0 242.883 153.923" enable-background="new 0 0 242.883 153.923"
   xml:space="preserve">
   
  <polygon class="star1" points="121.441,0 133.938,25.321 161.883,29.382 141.662,49.092 146.436,76.923 121.441,63.783 96.448,76.923 
  101.221,49.092 81,29.382 108.944,25.321 "/>
  
  <polygon class="star2" points="202.441,77 214.938,102.321 242.883,106.381 222.662,126.092 227.436,153.923 202.441,140.784 177.447,153.923 
  182.221,126.092 162,106.381 189.944,102.321 "/>
  
  <polygon class="star3" points="40.441,77 52.938,102.321 80.883,106.381 60.662,126.092 65.436,153.923 40.441,140.784 15.447,153.923 
  20.221,126.092 0,106.381 27.944,102.321 "/>
  
  </svg>
  
One of the downsides of inserting the XML file is it's size in not controllable. It uses the exact size of the file itself. The components within though can have their colours changed if classes are applied to it's objects.

  //Index.html
  <!svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
   width="242.883px" height="153.923px" viewBox="0 0 242.883 153.923" enable-background="new 0 0 242.883 153.923"
   xml:space="preserve">
   
  <polygon class="star1" points="121.441,0 133.938,25.321 161.883,29.382 141.662,49.092 146.436,76.923 121.441,63.783 96.448,76.923 
  101.221,49.092 81,29.382 108.944,25.321 "/>
  
  <polygon class="star2" points="202.441,77 214.938,102.321 242.883,106.381 222.662,126.092 227.436,153.923 202.441,140.784 177.447,153.923 
  182.221,126.092 162,106.381 189.944,102.321 "/>
  
  <polygon class="star3" points="40.441,77 52.938,102.321 80.883,106.381 60.662,126.092 65.436,153.923 40.441,140.784 15.447,153.923 
  20.221,126.092 0,106.381 27.944,102.321 "/>
  
  </svg>
  
  //main.css
  .star1 {
    fill: #2ecc71;
  }
  

  
#Media Queries
Media queries are used to change the presentational content by limiting the scope of the stylesheet to a certain context set by width, height and color.

The usage of media queries is widespread in responsive design because of the ability to target very specific screen sizes and devices.

A media query can be used multiple ways

**Link**

  <!-- CSS media query on a link element -->
  <link rel="stylesheet" media="(max-width: 800px)" href="main.css" />
  
**In a stylesheet**

  <style>
  @media (max-width: 600px) {
      .content {
      display: none;
      }
  }   
  </style>
  
###Operators in a media query
Media queries except operators to create complex media queries. These operators and _and_, _only_ and _not_

####and
*and* is used to combine media features together into one chain. All features of the media query that you want to select an object must have an _and_ separating them.

Example
  
  @media screen and (min-width: 700px) and (orientation: landscape) { ... }
  
####only
*only* is used to be provide specific styles to certain users. This can be used to prevent certain objects that a browser will not support from displaying.

Example

  @media only print { ... }
  
####not
*not* is used to negate all previous queries that include the same context.

Example

  @media print not screen { … }
  
####comma-seperated lists
Commas act like _or_ operators between media features.

Example

    @media (min-width: 700px), handheld and (orientation: landscape) { ... }
The above media query would target devices devices that have a screen larger than 700px and handheld devices that are ONLY in landscape mode. If the handheld device was in portrait mode, the media query would not apply unless it had a screen larger than 700px.
  
###Media Types
Targets the output of the display. Used to target phones, printers, screens, etc.

**all**  Used for all media type devices

**aural**  Used for speech and sound synthesizers

**braille**  Used for braille tactile feedback devices

**embossed**   Used for paged braille printers

**handheld**   Used for small or handheld devices

**print**  Used for printers

**projection**   Used for projected presentations, like slides

**screen**   Used for computer screens

**tty**  Used for media using a fixed-pitch character grid, like teletypes and terminals

**tv** Used for television-type devices
  
###Media Features
Media features are use to provide the context for the media query. This allows you to target your devices for specific screen types. Some of the most commonly used media features are below

**Height**
Describes the height of the viewport on a rendering device. Can be used with max and min.
    
    @media (height:800px) { … }
    @media (max-height:800px) { … }
    @media (min-height:800px) { … }
    
**Width**
Describes the width of the viewport on a rendering device

    @media (width:1080px) { … }
    @media (max-width:1080px) { … }
    @media (min-width:1080px) { … }
    
**Orientation**
Describes whether the device is in landscape or portrait mode. Very useful for tablet and mobile phones.

    @media (orientation: portrait) { … }
    @media (orientation: landscape) { … }
    
**Device Pixel Ratio**
Used to target higher resolution screens on devices. Mainly retina displays on Apple products.

    @media (min-device-pixel-ratio : 1.5) { … }
    
Chaining these together, we can provide media queries for most devices

**Smartphones(Portrait and Landscape)**

    @media screen and handheld and (min-device-width : 320px) and (max-device-width : 480px) { … }
    
**Retina Devices**

    @media only screen and (-webkit-min-device-pixel-ratio : 1.5), only screen and (min-device-pixel-ratio : 1.5) { … }
    
**Larger Screens**

    @media only screen and (min-width : 1820px) { … }
    
**Printers**

    @media only print { … }

  



  
