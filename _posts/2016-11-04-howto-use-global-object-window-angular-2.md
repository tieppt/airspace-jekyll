---
id: 111
title: Howto Use Global Object Window in Angular 2
date: 2016-11-04T17:48:44+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=111
permalink: /howto-use-global-object-window-angular-2/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/11/angular-2.png
categories:
  - Javascript
  - Lập Trình
  - Lập Trình Angular
  - Programming
  - Web
tags:
  - Angular
  - Angular 2
  - Angular Window
  - Web Dev
---
<h2 style="text-align: center;">
  Howto Use Global Object Window in Angular 2
</h2>

Hi guy, <a href="https://angular.io/" target="_blank">Angular 2</a> is _**hot**_, but sometime you wondering howto use global object like _**window**_ setInterval function, for example. As you may know, in Angular 1, Angular have wrapper class to access these object.

So, how about Angular 2.

<!--more-->

First of all, in your module, you need add a provider like this:

<pre class="theme:github lang:js decode:true">@NgModule({
  declarations: [
    ...
  ],
  imports: [
    ...
  ],
  providers: [{provide: Window, useValue: window}],
  bootstrap: [...]
})</pre>

And in your component/service, &#8230;

You need Inject like this:

<pre class="theme:github lang:js decode:true">constructor(@Inject(Window) public window: Window) {
...
}</pre>

Then you can use in your method like this:

<pre class="theme:github lang:js decode:true ">someMethod() {
  this.window.setTimeout(() =&gt; {
	// do something here
  }, 2000);
}</pre>

Have fun!