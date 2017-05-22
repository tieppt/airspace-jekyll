---
id: 126
title: Javascript Trim polyfill match any pattern, include Left Trim and Right Trim
date: 2016-11-10T07:46:59+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=126
permalink: /javascript-trim-polyfill-match-pattern-include-left-trim-right-trim/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/11/trim.png
categories:
  - Lập Trình
  - Programming
  - Web
tags:
  - Javascript
  - JS String
  - left trim
  - right trim
  - string trim
---
## Javascript Trim polyfill match any pattern, include Left Trim and Right Trim

The following scripts useful when you need trim some string with pattern, even work when you need trim white space as well.

Working on any browser support <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace" target="_blank">String.replace</a> method.

<!--more-->

Left Trim:

<pre class="lang:js decode:true ">String.prototype.ltrim = function(pattern) {
  pattern = pattern || new RegExp(/\s\uFEFF\xA0/);
  var trimPattern = new RegExp('^[' + pattern + ']+', 'g');
  return this.replace(trimPattern, '');
};
console.log("=== LEFT TRIM ===");
console.log('...this text ... trim.....'.ltrim(/\./));
console.log('  this text  trim    '.ltrim());</pre>

Result:

<pre class="lang:js decode:true ">"=== LEFT TRIM ==="
"this text ... trim....."
"this text  trim    "</pre>

Right Trim:

<pre class="lang:js decode:true ">String.prototype.rtrim = function(pattern) {
  pattern = pattern || new RegExp(/\s\uFEFF\xA0/);
  var trimPattern = new RegExp('[' + pattern + ']+$', 'g');
  return this.replace(trimPattern, '');
};
console.log("=== RIGHT TRIM ===");
console.log('...this text ... trim.....'.rtrim(/\./));
console.log('  this text  trim    '.rtrim());</pre>

Result:

<pre class="lang:js decode:true ">"=== RIGHT TRIM ==="
"...this text ... trim"
"  this text  trim"</pre>

Trim both left and right with pattern:

<pre class="lang:js decode:true ">String.prototype.trim = function(pattern) {
  return this.ltrim(pattern).rtrim(pattern);
};
console.log("=== TRIM ===");
console.log('...this text ... trim.....'.trim(/\./));
console.log('  this text  trim    '.trim());</pre>

Result:

<pre class="lang:js decode:true ">"=== TRIM ==="
"this text ... trim"
"this text  trim"</pre>

Live demo: <a href="http://jsbin.com/gabiterawu/edit?js,console,output" target="_blank">http://jsbin.com/gabiterawu/edit?js,console,output</a>

&nbsp;