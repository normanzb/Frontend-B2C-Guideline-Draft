#CSS File

* Charset must be utf-8（no BOM）
* Use <link /> to reference the file, DO NOT USE @Import
* http://www.stevesouders.com/blog/2009/04/09/dont-use-import/ 
* Use <style /> Only if it is used for single page.
* NO inline CSS pls! 
* No horizontal scrollbar in your code editor:
  that means, if the statement is too long, break it to into multiple lines, try utilize vertical space
  as much as you can.

#CSS Hacks?

If you requirement can be done by using [css media query](http://www.w3.org/TR/css3-mediaqueries/), then use it.

If there is better choice, such as etch is available in your page, we suggest you targeting browser this way:

    html.msie6 foobar {}
    html.msie7 foobar {}
    html.msie8 foobar {}
    html.msie9 foobar {}
    html.non-msie6-msie7 {} /* for better browser */
    html.non-html5browser foobar{}
    html.html5browser foobar{} /* for modern html5 browser */
    html.webkit foobar{}
    html.win foobar{}
    html.mac foobar{}
    html.linux foobar{}
    html.iphone foobar{}
    html.ios foobar{}
    html.ipad foobar{}
    html.winxp foobar{}
    html.qs-protocol-https foobar{} /* if we are under https */
    html.ornt-portrait foobar{} /* in portrait mode */
    html.ornt-landscape foobar{} /* in landscape mode */
    html.device-pixelrate-1 foobar{} /* default image quality */
    html.device-pixelrate-1.5 foobar{} /* hi-resolution quality image for retina screen */
    
For more, check out https://github.com/ETUI/ETUI/blob/master/lib/etch/tagger.js
  
However if there is no tagger available in your page, 
we suggest to targeting browser smartly by using superior syntax that older browser doesn't support:

    .selector .child{property:value;} /* for ie-6 */
    .selector > .child{property:value;} /* except ie-6 */

The last choice, CSS Hacks:

    .all-IE{property:value\9;}
    :root .IE-9{property:value\0/;}
    .gte-IE-8{property:value\0;}
    .lte-IE-7{*property:value;}
    .IE-7{+property:value;}
    .IE-6{_property:value;}
    .not-IE{property//:value;}
    @-moz-document url-prefix() { .firefox{property:value;} }
    @media all and (-webkit-min-device-pixel-ratio:0) { .webkit{property:value;} }
    @media all and (-webkit-min-device-pixel-ratio:10000),not all and (-webkit-min-device-pixel-ratio:0) { .opera{property:value;} }
    @media screen and (max-device-width: 480px) { .iphone-or-mobile-s-webkit{property:value;} }

## Unit

Using em carefully, generally it should be used for 2 purposes:

1.  In IE, there is an option to change text size, 
using em allowing user to change the text size in web page by using that option in IE. 
Vice versa, if you fixed the font size with `px` or `pt`, the text size will not change when user changed the option. 
**but keep in mind that it also break  your layout when the original ‘design’ is fixed 
or your didn’t properly make your html structure flexible enough.**
for example, in current global SP, if you look at the 3 step section, the background is fixed size, that means once you enlarge the font size your layout will be broken.
In modern browser other than IE, people simply zoom in the whole page rather than just text so there is no such problem
2.	Em is better for code maintenance, says if title font size is always 2 times of normal text size, why no set title font size to 2em? Once you modified the text size, title size will be automatically changed also.


#Common CSS classes

##State indicateors

###et-active
Indicate current tab/slide/whatelse is in active state.

###et-disabled
Indicate current ui component is disabled.

###et-enabled
Indicate current ui component is enabled.

###et-error
Indicate the validation failed on current element

##Pseudo Class Replacement

###et-first
A replacement for :first-child for older browser such as IE6

###et-last

##Position Indicator

###et-opening

###et-closing

###et-north

###et-south

###et-west

###et-east

##DOM Structure Indicator

###et-top

###et-bottom

###et-inner

###et-outer

###et-cnt
The actuall content area (wrapping the text)

##Form elements

###et-field
The wrapping element

###et-field-text
The text input area

## Modules

### borderable

#JavaScript 

##Rules

1. Try best not to pollute global object, including but not limits to `window`, 
   built in objects and their prototypes, `jQuery.fn` ...
2. If you do need to expose an global object, make sure it is under proper name space, 
   for example, `etPage.project.page.func`
3. JS files in under rootapp (/_scripts/, /widgets/) are meant to be shared across project, 
   you can reference to it directly in your project. 
   The other js files are not meant to be shared by the other projects. If you do want to use a file from
   the other project, please make a copy of that to your own project directory.
4. If you want to reference 3rd party javascript files, keep in mind that those api providers may not always available
   due to network or server maintenance issue. for example, if you are in China mainland, than you wouldn't have
   access to youtube.com and some google apis.
   so in order to avoid from above issues, we suggest:
   1. Try load the api asynchronously rather than put the `<script />` tag directly into page.
   2. If the api provider does not support asynchronously loading, e.g. there are document.write() inside the js file
      so it breaks our page if we load it asynchronously, we should consider copy the js file to our server, or use 
      an `<iframe />` to wrap the content.

##Naming convention

1. lowerCamelCase for local variables or namespace.

2. UPPER_CASE_FOR_CONSTANTS

3. prefix with _underline for virtual member or private member

4. Recommand to use ''var prvt = {}'' in your closure to holds all private methods.

5. Small **simple** words for namespaces.

6. Add prefix $ to jQuery object.

7. UpperCamelCase for constructors.
