---
title: filter
slug: Web/CSS/filter
tags:
  - CSS
  - CSS Property
  - Reference
  - SVG
  - SVG Filter
  - 'recipe:css-property'
browser-compat: css.properties.filter
---
<div>{{CSSRef}}</div>

<p>The <strong><code>filter</code></strong> <a href="/en-US/docs/Web/CSS">CSS</a> property applies graphical effects like blur or color shift to an element. Filters are commonly used to adjust the rendering of images, backgrounds, and borders.</p>

<p>Included in the CSS standard are several functions that achieve predefined effects. You can also reference an SVG filter with a URL to an <a href="/en-US/docs/Web/SVG/Element/filter">SVG filter element</a>.</p>

<div>{{EmbedInteractiveExample("pages/css/filter.html")}}</div>


<h2 id="Syntax">Syntax</h2>

<pre class="brush:css no-line-numbers">/* URL to SVG filter */
filter: url("filters.svg#filter-id");

/* &lt;filter-function&gt; values */
filter: blur(5px);
filter: brightness(0.4);
filter: contrast(200%);
filter: drop-shadow(16px 16px 20px blue);
filter: grayscale(50%);
filter: hue-rotate(90deg);
filter: invert(75%);
filter: opacity(25%);
filter: saturate(30%);
filter: sepia(60%);

/* Multiple filters */
filter: contrast(175%) brightness(3%);

/* Use no filter */
filter: none;

/* Global values */
filter: inherit;
filter: initial;
filter: revert;
filter: unset;
</pre>

<p>With a function, use the following:</p>

<pre class="brush: css">filter: &lt;filter-function&gt; [&lt;filter-function&gt;]* | none
</pre>

<p>For a reference to an SVG {{SVGElement("filter")}} element, use the following:</p>

<pre class="brush: css">filter: url(file.svg#filter-element-id)
</pre>

<h3 id="Interpolation">Interpolation</h3>

<p>If both the beginning and end filters have a function list of the same length without {{cssxref("url()","url()")}}, each of their filter functions is interpolated according to its specific rules. If they have different lengths, the missing equivalent filter functions from the longer list are added to the end of the shorter list using their lacuna values, then all filter functions are interpolated according to their specific rules. If one filter is <code>none</code>, it is replaced with the filter functions list of the other one using the filter function default values, then all filter functions are interpolated according to their specific rules. Otherwise, discrete interpolation is used.</p>

<h2 id="Functions">Functions</h2>

<p>The <code>filter</code> property is specified as <code>none</code> or one or more of the functions listed below. If the parameter for any function is invalid, the function returns <code>none</code>. Except where noted, the functions that take a value expressed with a percent sign (as in <code>34%</code>) also accept the value expressed as decimal (as in <code>0.34</code>).</p>

<p>When a single <code>filter</code> property has two or more functions it's results will be different from when two or more <code>filter</code> properties are separately applied with the same functions.</p>

<h3 id="SVG_filter">SVG filter</h3>

<h4 id="url">url()</h4>

<p>Takes an URI pointing to an <a href="/en-US/docs/Web/SVG/Element/filter">SVG filter</a>, which may be embedded in an external XML file.</p>

<pre class="brush: css">filter: url(resources.svg#c1)
</pre>

<h3 id="Filter_functions">Filter functions</h3>

<h4 id="blur">blur()</h4>

<p>The {{cssxref("filter-function/blur()", "blur()")}} function applies a Gaussian blur to the input image. The value of <code>radius</code> defines the value of the standard deviation to the Gaussian function, or how many pixels on the screen blend into each other, so a larger value will create more blur. The lacuna value for interpolation is <code>0</code>. The parameter is specified as a CSS length, but does not accept percentage values.</p>

<pre class="brush: css">filter: blur(5px)
</pre>

<pre class="brush: html hidden">  &lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_2.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_2.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;
        &lt;div class="svg-container"&gt;
          &lt;svg id="img3" overflow="visible" viewbox="0 0 212 161" color-interpolation-filters="sRGB"&gt;
            &lt;filter id="svgBlur" x="-5%" y="-5%" width="110%" height="110%"&gt;
              &lt;feGaussianBlur in="SourceGraphic" stdDeviation="3.5"/&gt;
            &lt;/filter&gt;
            &lt;image xlink:href="test_form_2.jpeg" filter="url(#svgBlur)" width="212px" height="161px"/&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_2_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande", "Lucida Sans Unicode", "DejaVu Sans", Lucida, Arial, Helvetica, sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -webkit-filter:blur(5px);
  -ms-filter:blur(5px);
  filter:blur(5px); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0;
  margin: 0 0 1.286em;
  height: 100%;
  width: 85%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<pre class="brush: svg">&lt;svg style="position: absolute; top: -99999px" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;filter id="svgBlur" x="-5%" y="-5%" width="110%" height="110%"&gt;
    &lt;feGaussianBlur in="SourceGraphic" stdDeviation="5"/&gt;
  &lt;/filter&gt;
&lt;/svg&gt;</pre>

<div>{{EmbedLiveSample('blur','100%','236px','','', 'no-codepen')}}</div>

<h4 id="brightness">brightness()</h4>

<p>The {{cssxref("filter-function/brightness()", "brightness()")}} function applies a linear multiplier to the input image, making it appear more or less bright. A value of <code>0%</code> will create an image that is completely black. A value of <code>100%</code> leaves the input unchanged. Other values are linear multipliers on the effect. Values of an amount over <code>100%</code> are allowed, providing brighter results. The lacuna value for interpolation is <code>1</code>.</p>

<pre class="brush: css">filter: brightness(2)</pre>

<pre class="brush: svg">&lt;svg style="position: absolute; top: -99999px" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;filter id="brightness"&gt;
    &lt;feComponentTransfer&gt;
      &lt;feFuncR type="linear" slope="[amount]"/&gt;
      &lt;feFuncG type="linear" slope="[amount]"/&gt;
      &lt;feFuncB type="linear" slope="[amount]"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
&lt;/svg&gt;</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 286 217" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="brightness"&gt;
    &lt;feComponentTransfer&gt;
        &lt;feFuncR type="linear" slope="2"/&gt;
        &lt;feFuncG type="linear" slope="2"/&gt;
        &lt;feFuncB type="linear" slope="2"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="test_form.jpg" filter="url(#brightness)" width="286px" height="217px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:brightness(2);
  -webkit-filter:brightness(2);
  -ms-filter:brightness(2);
  filter:brightness(2); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  height:100%;
  width: 85%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<p>{{EmbedLiveSample('brightness','100%','231px','','', 'no-codepen')}}</p>

<h4 id="contrast">contrast()</h4>

<p>The {{cssxref("filter-function/contrast()", "contrast()")}} function adjusts the contrast of the input image. A value of <code>0%</code> will create an image that is completely gray. A value of <code>100%</code> leaves the input unchanged. Values of an amount over <code>100%</code> are allowed, providing results with more contrast. The lacuna value for interpolation is <code>1</code>.</p>

<pre class="brush: css">filter: contrast(200%)
</pre>

<pre class="brush: svg">&lt;svg style="position: absolute; top: -99999px" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;filter id="contrast"&gt;
    &lt;feComponentTransfer&gt;
      &lt;feFuncR type="linear" slope="[amount]" intercept="-(0.5 * [amount]) + 0.5"/&gt;
      &lt;feFuncG type="linear" slope="[amount]" intercept="-(0.5 * [amount]) + 0.5"/&gt;
      &lt;feFuncB type="linear" slope="[amount]" intercept="-(0.5 * [amount]) + 0.5"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
&lt;/svg&gt;
</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_3.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_3.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 240 151" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="contrast"&gt;
    &lt;feComponentTransfer&gt;
      &lt;feFuncR type="linear" slope="2" intercept="-0.5"/&gt;
      &lt;feFuncG type="linear" slope="2" intercept="-0.5"/&gt;
      &lt;feFuncB type="linear" slope="2" intercept="-0.5"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="test_form_3.jpeg" filter="url(#contrast)" width="240px" height="151px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_3_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:contrast(200%);
  -webkit-filter:contrast(200%);
  -ms-filter:contrast(200%);
  filter:contrast(200%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<div>{{EmbedLiveSample('contrast','100%','203px','','', 'no-codepen')}}</div>

<h4 id="drop-shadow">drop-shadow()</h4>

<p>The {{cssxref("filter-function/drop-shadow()", "drop-shadow()")}} function applies a drop shadow effect to the input image. A drop shadow is effectively a blurred, offset version of the input image's alpha mask drawn in a particular color, composited below the image. The function accepts a parameter of type <code>&lt;shadow&gt;</code> (defined in <a href="https://www.w3.org/TR/css-backgrounds-3/#typedef-shadow">CSS3 Backgrounds</a>), with the exception that the <code>inset</code> keyword and <code>spread </code>parameter are not allowed. This function is similar to the more established {{cssxref("box-shadow")}} property; the difference is that with filters, some browsers provide hardware acceleration for better performance. The parameters of the <code>&lt;shadow&gt;</code> parameter are as follows:</p>

<dl>
 <dt><code>&lt;offset-x&gt;</code> <code>&lt;offset-y&gt;</code> <small>(required)</small></dt>
 <dd>These are two {{cssxref("&lt;length&gt;")}} values to set the shadow offset. <code>&lt;offset-x&gt;</code> specifies the horizontal distance. Negative values place the shadow to the left of the element. <code>&lt;offset-y&gt;</code> specifies the vertical distance. Negative values place the shadow above the element. See {{cssxref("&lt;length&gt;")}} for possible units.<br>
 If both values are <code>0</code>, the shadow is placed behind the element (and may generate a blur effect if <code>&lt;blur-radius&gt;</code> and/or <code>&lt;spread-radius&gt;</code> is set).</dd>
 <dt><code>&lt;blur-radius&gt;</code> <small>(optional)</small></dt>
 <dd>This is a third {{cssxref("&lt;length&gt;")}} value. The larger this value, the bigger the blur, so the shadow becomes bigger and lighter. Negative values are not allowed. If not specified, it will be <code>0</code> (the shadow's edge is sharp).</dd>
 <dt><code>&lt;color&gt;</code> <small>(optional)</small></dt>
 <dd>See {{cssxref("&lt;color&gt;")}} values for possible keywords and notations. If not specified, the color used depends on the browser - it is usually the value of the {{cssxref("&lt;color&gt;")}} property, but note that Safari currently paints a transparent shadow in this case.</dd>
</dl>

<pre class="brush: css">filter: drop-shadow(16px 16px 10px black)</pre>

<pre class="brush: svg">&lt;svg style="position: absolute; top: -999999px" xmlns="http://www.w3.org/2000/svg"&gt;
 &lt;filter id="drop-shadow"&gt;
    &lt;feGaussianBlur in="SourceAlpha" stdDeviation="[radius]"/&gt;
    &lt;feOffset dx="[offset-x]" dy="[offset-y]" result="offsetblur"/&gt;
    &lt;feFlood flood-color="[color]"/&gt;
    &lt;feComposite in2="offsetblur" operator="in"/&gt;
    &lt;feMerge&gt;
      &lt;feMergeNode/&gt;
      &lt;feMergeNode in="SourceGraphic"/&gt;
    &lt;/feMerge&gt;
  &lt;/filter&gt;
&lt;/svg&gt;
</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_4.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_4.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;
        &lt;div class="svg-container"&gt;
          &lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" overflow="visible" viewbox="0 0 213 161" color-interpolation-filters="sRGB"&gt;
            &lt;defs&gt;
              &lt;image id="MyImage" xlink:href="test_form_4.jpeg" width="213px" height="161px"/&gt;
            &lt;/defs&gt;
            &lt;filter id="drop-shadow" x="-50%" y="-50%" width="200%" height="200%"&gt;
              &lt;feOffset dx="9" dy="9" in="SourceAlpha"/&gt;
              &lt;feGaussianBlur stdDeviation="5"/&gt;
            &lt;/filter&gt;
            &lt;use xlink:href="#MyImage" filter="url(#drop-shadow)"/&gt;
            &lt;use xlink:href="#MyImage"/&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_4_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="test_form_4 distorted border - Original image" id="img11" class="internal default" src="test_form_4_irregular-shape_opacity-gradient.png" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="test_form_4 distorted border - Live example" id="img12" class="internal default" src="test_form_4_irregular-shape_opacity-gradient.png" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;
        &lt;div class="svg-container"&gt;
          &lt;svg xmlns="http://www.w3.org/2000/svg" id="img13" overflow="visible" viewbox="0 0 213 161" color-interpolation-filters="sRGB"&gt;
            &lt;defs&gt;
              &lt;image id="MyImage2" xlink:href="test_form_4_irregular-shape_opacity-gradient.png" width="213px" height="161px"/&gt;
            &lt;/defs&gt;
            &lt;filter id="drop-shadow2" x="-50%" y="-50%" width="200%" height="200%"&gt;
              &lt;feOffset dx="5" dy="5.5" in="SourceAlpha"/&gt;
              &lt;feGaussianBlur stdDeviation="2.5"/&gt;
              &lt;feComponentTransfer&gt;
                &lt;feFuncA type="table" tableValues="0 0.8"/&gt;
              &lt;/feComponentTransfer&gt;
            &lt;/filter&gt;
            &lt;use xlink:href="#MyImage2" filter="url(#drop-shadow2)"/&gt;
            &lt;use xlink:href="#MyImage2"/&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/td&gt;
      &lt;td&gt;&lt;img alt="test_form_4 distorted border drop shadow - Static example" id="img14" class="internal default" src="test_form_4_irregular-shape_opacity-gradient_drop-shadow.png" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: drop-shadow(16px 16px 10px black);
  -webkit-filter: drop-shadow(16px 16px 10px black);
  -ms-filter: drop-shadow(16px 16px 10px black);
  filter: drop-shadow(16px 16px 10px black);
}
#img12 {
  width:100%;
  height:auto;
  -moz-filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
  -webkit-filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
  -ms-filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
  filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
}
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
#irregular-shape {
  width: 64%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3, #img13 {
  width:100%;
  height:auto;
}
</pre>

<div>{{EmbedLiveSample('drop-shadow','100%','400px','','', 'no-codepen')}}</div>

<h4 id="grayscale">grayscale()</h4>

<p>The {{cssxref("filter-function/grayscale()", "grayscale()")}} function converts the input image to grayscale. The value of <code>amount</code> defines the proportion of the conversion. A value of <code>100%</code> is completely grayscale. A value of <code>0%</code> leaves the input unchanged. Values between <code>0%</code> and <code>100%</code> are linear multipliers on the effect. The lacuna value for interpolation is <code>0</code>.</p>

<pre class="brush: css">filter: grayscale(100%)</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_5.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_5.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 276 184" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="grayscale"&gt;
    &lt;feColorMatrix type="matrix"
               values="0.2126 0.7152 0.0722 0 0
                       0.2126 0.7152 0.0722 0 0
                       0.2126 0.7152 0.0722 0 0
                       0 0 0 1 0"/&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="test_form_5.jpeg" filter="url(#grayscale)" width="276px" height="184px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_5_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:grayscale(100%);
  -webkit-filter:grayscale(100%);
  -ms-filter:grayscale(100%);
  filter:grayscale(100%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<div>{{EmbedLiveSample('grayscale','100%','209px','','', 'no-codepen')}}</div>

<h4 id="hue-rotate">hue-rotate()</h4>

<p>The {{cssxref("filter-function/hue-rotate()", "hue-rotate()")}} function applies a hue rotation on the input image. The value of <code>angle</code> defines the number of degrees around the color circle the input samples will be adjusted. A value of <code>0deg</code> leaves the input unchanged. The lacuna value for interpolation is <code>0</code>. Though there is no maximum value; the effect of values above <code>360deg</code> wraps around.</p>

<pre class="brush: css">filter: hue-rotate(90deg)</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_6.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_6.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 266 190" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="hue-rotate"&gt;
    &lt;feColorMatrix type="hueRotate"
               values="90"/&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="test_form_6.jpeg" filter="url(#hue-rotate)" width="266px" height="190px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_6_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:hue-rotate(90deg);
  -webkit-filter:hue-rotate(90deg);
  -ms-filter:hue-rotate(90deg);
  filter:hue-rotate(90deg); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<pre class="brush: html">&lt;svg style="position: absolute; top: -999999px" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;filter id="svgHueRotate"&gt;
    &lt;feColorMatrix type="hueRotate" values="[angle]"/&gt;
  &lt;/filter&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('hue-rotate','100%','221px','','', 'no-codepen')}}</p>

<h4 id="invert">invert()</h4>

<p>The {{cssxref("filter-function/invert()", "invert()")}} function inverts the samples in the input image. The value of <code>amount</code> defines the proportion of the conversion. A value of <code>100%</code> is completely inverted. A value of <code>0%</code> leaves the input unchanged. Values between <code>0%</code> and <code>100%</code> are linear multipliers on the effect. The lacuna value for interpolation is <code>0</code>.</p>

<pre class="brush: css">filter: invert(100%)</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_7.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_7.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 183 276" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="invert"&gt;
    &lt;feComponentTransfer&gt;
        &lt;feFuncR type="table" tableValues="1 0"/&gt;
        &lt;feFuncG type="table" tableValues="1 0"/&gt;
        &lt;feFuncB type="table" tableValues="1 0"/&gt;
    &lt;/feComponentTransfer&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="test_form_7.jpeg" filter="url(#invert)" width="183px" height="276px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_7_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: invert(100%);
  -webkit-filter: invert(100%);
  -ms-filter: invert(100%);
  filter: invert(100%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<p>{{EmbedLiveSample('invert','100%','407px','','', 'no-codepen')}}</p>

<h4 id="opacity">opacity()</h4>

<p>The {{cssxref("filter-function/opacity()", "opacity()")}} function applies transparency to the samples in the input image. The value of <code>amount</code> defines the proportion of the conversion. A value of <code>0%</code> is completely transparent. A value of <code>100%</code> leaves the input unchanged. Values between <code>0%</code> and <code>100%</code> are linear multipliers on the effect. This is equivalent to multiplying the input image samples by amount. The lacuna value for interpolation is <code>1</code>. This function is similar to the more established {{cssxref("opacity")}} property; the difference is that with filters, some browsers provide hardware acceleration for better performance.</p>

<pre class="brush: css">filter: opacity(50%)</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_14.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_14.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 276 183" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="opacity"&gt;
    &lt;feComponentTransfer&gt;
        &lt;feFuncA type="table" tableValues="0 0.5"&gt;
    &lt;/feComponentTransfer&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="test_form_14.jpeg" filter="url(#opacity)" width="276px" height="183px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_14_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: opacity(50%);
  -webkit-filter: opacity(50%);
  -ms-filter: opacity(50%);
  filter: opacity(50%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<p>{{EmbedLiveSample('opacity','100%','210px','','', 'no-codepen')}}</p>

<h4 id="saturate">saturate()</h4>

<p>The {{cssxref("filter-function/saturate()", "saturate()")}} function saturates the input image. The value of <code>amount</code> defines the proportion of the conversion. A value of <code>0%</code> is completely un-saturated. A value of <code>100%</code> leaves the input unchanged. Other values are linear multipliers on the effect. Values of amount over <code>100%</code> are allowed, providing super-saturated results. The lacuna value for interpolation is <code>1</code>.</p>

<pre class="brush: css">filter: saturate(200%)</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_9.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_9.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 201 239" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="saturate"&gt;
    &lt;feColorMatrix type="saturate"
               values="2"/&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="test_form_9.jpeg" filter="url(#saturate)" width="201px" height="239px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_9_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: saturate(200%);
  -webkit-filter: saturate(200%);
  -ms-filter: saturate(200%);
  filter: saturate(200%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<p>{{EmbedLiveSample('saturate','100%','332px','','', 'no-codepen')}}</p>

<h4 id="sepia">sepia()</h4>

<p>The {{cssxref("filter-function/sepia()", "sepia()")}} function converts the input image to sepia. The value of <code>amount</code> defines the proportion of the conversion. A value of <code>100%</code> is completely sepia. A value of <code>0%</code> leaves the input unchanged. Values between <code>0%</code> and <code>100%</code> are linear multipliers on the effect. The lacuna value for interpolation is <code>0</code>.</p>

<pre class="brush: css">filter: sepia(100%)</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_12.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_12.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 259 194" color-interpolation-filters="sRGB"&gt;
 &lt;filter id="sepia"&gt;
    &lt;feColorMatrix type="matrix"
               values="0.393 0.769 0.189 0 0
                       0.349 0.686 0.168 0 0
                       0.272 0.534 0.131 0 0
                       0 0 0 1 0"/&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="test_form_12.jpeg" filter="url(#sepia)" width="259px" height="194px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_12_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: sepia(100%);
  -webkit-filter: sepia(100%);
  -ms-filter: sepia(100%);
  filter: sepia(100%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<p>{{EmbedLiveSample('sepia','100%','229px','','', 'no-codepen')}}</p>

<h2 id="Combining_functions">Combining functions</h2>

<p>You may combine any number of functions to manipulate the rendering. The following example enhances the contrast and brightness of the image:</p>

<pre class="brush: css">filter: contrast(175%) brightness(103%)</pre>

<pre class="brush: html hidden">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th style="text-align: left;" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img id="img1" class="internal default" src="test_form_8.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img2" class="internal default" src="test_form_8.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img id="img4" class="internal default" src="test_form_8_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css hidden">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: contrast(175%) brightness(103%);
  -webkit-filter: contrast(175%) brightness(103%);
  -ms-filter: contrast(175%) brightness(103%);
  filter: contrast(175%) brightness(103%);
}
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>

<p>{{EmbedLiveSample('Combining_functions','100%','209px','','', 'no-codepen')}}</p>

<h2 id="Formal_definition">Formal definition</h2>

<p>{{cssinfo}}</p>

<h2 id="Formal_syntax">Formal syntax</h2>

{{csssyntax}}

<h2 id="Examples">Examples</h2>

<h3 id="Applying_filter_functions">Applying filter functions</h3>

<p>Examples of using the predefined functions are shown below. See each function for a specific example.</p>

<pre class="brush: css">.mydiv {
  filter: grayscale(50%);
}

/* Gray all images by 50% and blur by 10px */
img {
  filter: grayscale(0.5) blur(10px);
}</pre>

<h3 id="Applying_SVG_filters">Applying SVG filters</h3>

<p>Examples of using the URL function with an SVG resource are as follows:</p>

<pre class="brush: css">.target {
  filter: url(#c1);
}

.mydiv {
  filter: url(commonfilters.xml#large-blur);
}
</pre>

<h2 id="Specifications">Specifications</h2>

{{Specifications}}

<h2 id="Browser_compatibility">Browser compatibility</h2>

<p>{{Compat}}</p>

<h2 id="See_also">See also</h2>

<ul>
 <li><a href="/en-US/docs/Web/SVG/Applying_SVG_effects_to_HTML_content">Applying SVG effects to HTML content</a></li>
 <li>The {{cssxref("mask")}} property</li>
 <li><a href="/en-US/docs/Web/SVG">SVG</a></li>
</ul>