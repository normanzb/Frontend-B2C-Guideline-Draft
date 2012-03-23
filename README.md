#CSS File

* Charset must be utf-8（no BOM）
* Use <link /> to reference the file, DO NOT USE @Import
* http://www.stevesouders.com/blog/2009/04/09/dont-use-import/ 
* Use <style /> Only if it is used for single page.
* NO inline CSS pls! 

#CSS Hacks?

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