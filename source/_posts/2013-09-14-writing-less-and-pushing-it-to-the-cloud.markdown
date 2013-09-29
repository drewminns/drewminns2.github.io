---
layout: post
title: "Writing LESS and pushing it to the cloud"
date: 2013-09-14 14:06
comments: true
categories: 
---
This lesson will cover the basics of working with preprocessed LESS and the basics of working with Github.

####Exercise Files
[Download Exercise](https://docs.google.com/file/d/0B1z6vJfOT3uJaXNBUTFKbXpiS0E/edit?usp=sharing)

Download and Install
[Codekit](http://incident57.com/codekit/)


#Preprocessing CSS
CSS has extended past the basic usage of targeting every element in a stylesheet. LESS, SASS, SCSS, Stylus have made writing CSS much faster, easier and with less work. Not only does it save time, but it introduces Functions and Operations into your values and properties that allow you to subtract, add, multiply, divide and use percentage based values.

For the purpose of this lesson, we will focus on LESS.

#Working with LESS
LESS is a javascript based language that is compiled into CSS for the browser to read. Like any CSS, the main stylesheet should be included in the header of an HTML page. Preprocessing tools like Codekit, Scout and others enable the LESS to be compiled prior to upload to the client-side. For the purpose of development, it is acceptable to use the LESS Javascript Compiler Include to compile live.

###To include the LESS JS Compiler in your site

####index.html
        <html>
            <head>
                <link rel="styles/less" type="text/css" href="styles.less" />
                <script src="js/less.js" type="text/javascript"></script>
            </head>
            <body></body>
        </html>
        
There is a known error where viewing local files will not parse the LESS file correctly.

### To compile on the go to CSS
Use a precompiler such as Codekit, Simpless or the LESS App and reference the css file that the precompiler will create rather than the Less file.
        
#Nesting Elements
With standard CSS, targeting elements inside of other elements required using long selectors that would need to be written over and over.

Example to select elements of a navigation

        <!-- index.html -->    
        <nav>
            <ul>
                <li><a href="#">Link 1</a></li>
            </ul>
        </nav>
        
        //main.css
        
        nav {
            width: 40%;
        }
        
        nav ul {
            list-style-type: none;
        }
        
        nav ul li {
            display: inline;
        }
        
        nav ul li a {
            text-decoration: none;
        }
        
        nav ul li a:hover {
            text-decoration: underline;
        }
        
 With LESS, you can nest selectors to keep your stylesheet concise.
 
         <!-- index.html -->    
        <nav>
            <ul>
                <li><a href="#">Link 1</a></li>
            </ul>
        </nav>
        
        //main.less
        nav {
         width: 40%;
         ul {
          list-style-type: none;
          li {
           display:inline;
           a {
            text-decoration: none;
            &:hover {
             text-decoration: underline;
            }
           }
          }
         }
        }
        
 
#Variables
Variables can be stated throughout and include only a single value. For example, you declare a certain blue to be used throughout, you would create a variable as such. The name you give the variable is completely up to you but must be prepended with an @ symbol. 

        @blue: #143352;
        
To use a variable within your stylesheet, simply reference it as you would any value.               
        
        body {
         background-color: @blue;
        }
        
        // Outputs to 
        body {
         background-color: #143352;
        }
 
 Another Example
 
     @basefontsize: 16px;
     
     p {
      font-size: @basefontsize;
      color: @blue;
     }
     
#Mixins
Mixins are used to include multiple elements and values that can be used multiple times. The concept is that you declare a mixin once and it can be used throughout a stylesheet without writing extra code.

A Mixin is much like a variable in the way it is declared. Use a '.' to begin the Mixin and give it any name you'd like. Within the Mixin, you can include as many properties as you'd like. Variables previously created can be used within Mixins as well.

####Example #1

    .roundedbutton {
      border-radius: 5px;
      background: @blue;
      color: #fff;
    }
    
    button[type="submit"] {
      .roundedbutton;
      padding: 5px 2px;
    }
    
####Example #2
    
    .basefont {
      font-family: Tahoma, Verdana, Segoe, sans-serif;
      color: #999;
      font-weight: 300;
    }
    
    h1 {
     .basefont;
     font-size: 32px;
    }
    
    h2 {
     .basefont;
     font-size: 26px;
    }
    
    p {
      .basefont;
      font-size: 16px;
    }
    
#Parametric Mixin
Mixins can also be used to accept parameters to create dynamic Mixins. Treat them like variables that can be declared at a later time.

#####Example #1

    .square(@size){
     width: @size;
     height: @size;
    }
    
    .button-square {
     .square(50px);
    }
    
Compiles to

    .button-square {
     width: 50px;
     height: 50px;
    }
    
####Example #2

    .boxbutton(@backgroundcolor) {
      color: #fff;
      background-color: @backgroundcolor;
      border: 0 none;
      &:hover {
        opacity: 0.5;
      }
    }
    
    .nextbutton {
     .boxbutton(#00bb83);
    }
    
Compiles to

    .nextbutton {
      color: #fff;
      background-color: #00bb83;
      border: 0 none;
    }
    
    .nextbutton:hover {
      opacity: 0.5;
    }
    
#Sending it to the Cloud

Working in a production environment with a team, there may be many people working on different aspects of a product at one time. To manage this, version control has been the norm. The most popular of these systems is Git, a software developed by Linus Torvalds of the OS Linux.

Building on the software, Github has become the standard for hosted distributed version control. With your account you can host your code, make changes and view history, allow people to 'fork' your code so they can make their own changes.

We'll touch on the most basic uses of Github.

**Branches** - A current timeline of the repository. There can be many branches at one time, but only one 'master'

**Cloning** - Download a local copy of a hosted repository

**Adding** - Add your changes to the staging area

**Committing** - Record a marker with your changes that captures your name and email address and a message stating what and why you're committing.

**Pushing** - Upload your commits to the current branch

**Pulling** - Sync any new commits to the current branch