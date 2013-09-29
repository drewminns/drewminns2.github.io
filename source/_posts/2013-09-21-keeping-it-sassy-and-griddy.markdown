---
layout: post
title: "Keeping it Sassy and Griddy"
date: 2013-09-23 13:28
comments: true
categories: 
---

##Class Links

###Exercises
- [Preprocessors](https://github.com/drewminns/W3---Preprocessing)

###Preprocessors
- [Codekit](http://incident57.com/codekit/)
- [the official LESS app](http://incident57.com/less/)
- [SimpLESS](http://wearekiss.com/simpless)

###Grid Systems
- [960](http://960.gs/)
- [Semantic](http://semantic.gs/)
- [Blueprint](http://www.blueprintcss.org/)
- [Grid System Generator](http://www.gridsystemgenerator.com/gs04.php).


#Review
Last lesson we learned how to extend CSS with preprocessed languages. For that lesson we used [LESS](http://less.org) and learned of some of the features that can be used with it. Let's review some of these features.

###Preprocessing
LESS and other CSS-compiled programming languages cannot be read by the browser because of their format. Using a preprocessing tool such as [Codekit](http://incident57.com/codekit/), [the official LESS app](http://incident57.com/less/), or [SimpLESS](http://wearekiss.com/simpless), among others, you can develop locally in an extended language and have the code outputted into CSS.

Files written in LESS need to have the extension .less in order to use the features required.

###Nesting
LESS allows nesting of selectors inside other selectors. This makes inheritance clear and style sheets shorter.

#####Example
    #header {
      h1 {
        font-size: 26px;
        font-weight: bold;
      }
      p { 
        font-size: 12px;
        a { 
          text-decoration: none;
          &:hover { 
            border-width: 1px;
          }
        }
      }
    }
    
#####Compiles to
    #header h1 {
      font-size: 26px;
      font-weight: bold;
    }
    #header p {
      font-size: 12px;
    }
    #header p a {
      text-decoration: none;
    }
    #header p a:hover {
      border-width: 1px;
    }

###Variables
LESS allows variables to be defined. LESS variables are defined with an at sign(@). Variable assignment is done with a colon (:).

#####Example
        @color: #4D926F;
        
        #header {
          color: @color;
        }
        h2 {
          color: @color;
        }
        
#####Compiles To
        #header {
          color: #4D926F;
        }
        h2 {
          color: #4D926F;
        }
        
###Mixins
Mixins allow embedding all the properties of a class into another class by including the class name as one of its properties, thus behaving as a sort of constant or variable. They can also take arguments.

#####Example
    .rounded-corners (@radius: 5px) {
      border-radius: @radius;
      -webkit-border-radius: @radius;
      -moz-border-radius: @radius;
    }
    
    #header {
      .rounded-corners;
    }
    #footer {
      .rounded-corners(10px);
    }

#####Compiles to
    #header {
      border-radius: 5px;
      -webkit-border-radius: 5px;
      -moz-border-radius: 5px;
    }
    #footer {
      border-radius: 10px;
      -webkit-border-radius: 10px;
      -moz-border-radius: 10px;
    }



#Continuing to extend

###Operators
Operators allow addition, subtraction, multiplication and division of property values and colours to manipulate the output. Operators can be manipulated using order of operations and incorporate brackets.

#####Example
    @width: 500px;
    @height: 600px;
    margin: 15px;
    
    #feature {
        background-size: (@width * 2) - (@height - @margin)
    }
    
#####Compiles to
    #feature {
      background-size: 415px;
    }
    

###Functions
Functions allow manipulation of values using included tools in the codebase. Many of these functions take a value to manipulate the values. Basic functions include lighten, darken, desaturate, saturate, fadein, fadeout.

#####Example
    #feature {
      background-color: lighten(#e74c3c, 20%);
      border: 1px bottom desaturate(#2c3e50, 45%);
    }
    
#####Compiles to
    #feature {
      background-color: #f29f97;
      border: 1px bottom #3e3e3e;
    }  

Many more available and are documented at [LESS Function Reference](http://lesscss.org/#reference).

#SASS
LESS is based on SASS, the originator of extended CSS. Therefore, many of the same concepts in LESS are within SASS. Variables, Mixins, nesting, operators and functions are all the same but the Syntax is different.

- Variables are now called with a **$name**
- Mixins are now called with **@mixin name**

SASS has two syntaxes SCSS (Sassy CSS) and SASS (Syntactically Awesome Style Sheets). SCSS is much like LESS and uses brackets while SASS uses indentation to specify blocks instead of using brackets and semicolons. Literally, you are writing less.

######Example
    //LESS
    @bg: #ff0
    
    header {
        width: 100%;
        height: 100px;
        background-color: #ff0;
    }
    
    //SCSS
    $bg: #ff0
    
    header {
        width: 100%;
        height: 100px;
        background-color: #ff0;
    }
    
    //SASS
    $bg: #ff0
    
    header
        width: 100%
        height: 100px
        background-color: $bg
        
        
 To use either of these syntaxes simply give the one you are using the correct extension - .sass or .scss. You will experience errors if you include semicolons or brackets within your SASS so be very mindful of your habits.
 
#Working with a Grid

Designing with a grid can make the layout of a page easier and help layout the page with more consistency. Attributes of a page can be designed to follow certain widths that are predefined within a grid. These are called columns and you use a number of them to define widths of your elements.
        
#####Grid Example
![alt text](http://blog.mytemplatez.com/wp-content/uploads/2010/05/12-column-grid.png "Logo Title Text 1")

The image above shows a grid width of 960px. The red vertical lines are columns and the space in between them are called gutters. Each red column has a width of 60 pixels and each column has 10 pixels of margin on either side of them, resulting in a gutter of 20 pixels.

Using columns and gutters ensures that there is always consistent space between elements when laying out a page. Using the classes set within each grid system, we can set the width of each item by calling the class name for each width ex div class="col_12" will make the div stretch all 12 columns. This class name structure will vary from system to system.

There are many well known grid systems that exist such as [960](http://960.gs/), [Semantic](http://semantic.gs/) and [Blueprint](http://www.blueprintcss.org/). For the purpose of this lesson, we'll use the Simple Grid available from [Grid System Generator](http://www.gridsystemgenerator.com/gs04.php).




       
    

        
    
