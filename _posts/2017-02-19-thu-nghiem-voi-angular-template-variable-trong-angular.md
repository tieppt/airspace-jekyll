---
id: 299
title: 'Thử Nghiệm Với Angular Phần 11: Template Variable Trong Angular'
date: 2017-02-19T16:39:00+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=299
permalink: /thu-nghiem-voi-angular-template-variable-trong-angular/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/02/angular2-11.jpg
categories:
  - Lập Trình
  - Lập Trình Angular
  - Programming
  - Web
tags:
  - Angular
  - Angular 2
  - Angular Component
  - Lập Trình Angular 2
  - Web Dev
---
<h2 style="text-align: center;">
  Template Variable Trong Angular
</h2>

Bài học này sẽ giới thiệu cho các bạn về cách sử dụng Template Variable trong Angular và ngOnInit, ngAfterViewInit lifecycle.

<!--more-->

Template variable trong Angular có thể tạo bằng cách đặt tên kèm theo dấu # vào trước như sau:

<pre class="brush: html; highlight: [2, 4]">&lt;div class="tp-app__content"&gt;
  &lt;input type="text" #nameInput&gt;
  &lt;button (click)="sayHello()"&gt;Click me&lt;/button&gt;
  &lt;tp-switches #switches&gt;&lt;/tp-switches&gt;
&lt;/div&gt;
</pre>

Ở ví dụ trên, chúng ta đã tạo hai template variables là _nameInput_ và _switches. _Chúng ta có thể sử dụng trực tiếp các public properties của chúng như sau:

<pre class="brush: js;">nameInput.value

switches.toggle()</pre>

Hoặc sử dụng ở trong Component:

<pre class="brush: js; highlight: [11, 12, 16]">import { Component, ViewChild, ElementRef, AfterViewInit } from '@angular/core';
import { SwitchesComponent } from "./presentation/switches/switches.component";

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent implements AfterViewInit {
  title = 'app works!';
  @ViewChild('nameInput') name: ElementRef;
  @ViewChild('switches') switches: SwitchesComponent;
  sayHello() {
    this.switches.toggle();
  }
  ngAfterViewInit() {
    this.name.nativeElement.focus();
  }
}</pre>

Ở ví dụ trên, chúng ta đã tạo ra các properties để trỏ đến các Template variable bằng việc sử dụng <a href="https://angular.io/docs/ts/latest/api/core/index/ViewChild-decorator.html" target="_blank" rel="noopener noreferrer">@ViewChild</a>, đối với các element cơ bản của HTML, chúng ta có kiểu dữ liệu tương ứng là <a href="https://angular.io/docs/ts/latest/api/core/index/ElementRef-class.html" target="_blank" rel="noopener noreferrer">ElementRef</a>, còn các kiểu như Component, thì chúng ta có thể có cả kiểu ElementRef hoặc Component tương ứng.

Chúng ta cũng đã hook vào ngAfterViewInit lifecycle để thực hiện hành động focus _nameInput_.

Video bài học:
  


&nbsp;

Angular lifecycle: <a href="https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html</a>

Code repo: <a href="https://github.com/tieppt/try-angular/tree/lesson-11" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular/tree/lesson-11</a>