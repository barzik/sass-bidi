SASS-bidi - Direction agnostic stylesheets
=========

SASS-bidi is a set of SASS mixins that allows creating bi-directional styling without significant code duplication. <br/>
By using SASS-bidi mixins, it’s possible to create direction agnostic CSS stylesheets, which are faster to write and much easier to maintain.
Moreover, the naming convention used throughout the mixins makes it easier to comprehend by keeping the naming of properties as close as possible to the original CSS property names. <br/>


Paradigm shift
--------------
Direction agnostic styling is made possible by using a new approach of referring to both sides of a document as the “start” and “end” of the text as opposed to “left” or “right” of the document. This approach is similar to what is done in flex-box specification (although SASS-bidi does not use or depend on flex-box). 
The interpretation of the terms *start* and *end* depends on the value of the variable $bidi; when the value is **ltr** than *start* is **left** and *end* is **right**, and when the value is **rtl** it will be exactly the opposite.


For example:
<table>
<tr>
<th>
SASS-bidi
</th>
<th>
CSS
</th>
</tr>
<tr>
<td>
<pre>
// css 2.1
@import "border" ;
@import "clear";
@import "float";
@import "margin";
@import "padding";
@import "position";
@import "text";

// css 3
@import "border-radius";
@import "box-shadow";
@import "text-shadow";

// Example

$bidi : ltr; //define it on top of your general SCSS file

body{
	@include bidi-direction();
}

h1 {
	@include bidi-margin-start(20px);
	margin-bottom: 10px;
}
.two-col article {
	@include bidi-float(start);
}
.two-col nav {
	@include bidi-float(end);
}
</pre>
</td>
<td>
<pre>
body {
  direction: ltr;
}

h1 {
  margin-left: 20px;
  margin-bottom: 10px;
}

.two-col article {
  float: left;
}

.two-col nav {
  float: right;
}
</pre>
</td>
</tr>
</table>
