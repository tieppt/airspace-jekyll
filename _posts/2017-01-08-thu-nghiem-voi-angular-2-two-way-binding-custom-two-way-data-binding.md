---
id: 273
title: 'Thử Nghiệm Với Angular 2 Phần 9: Angular 2 Two-way Binding Và Tạo Custom Two-way Data Binding'
date: 2017-01-08T12:19:29+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=273
permalink: /thu-nghiem-voi-angular-2-two-way-binding-custom-two-way-data-binding/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/01/angular-2-Two-way-Binding-Va-Tao-Custom-Two-way-Data-Binding.jpg
categories:
  - Javascript
  - Lập Trình
  - Lập Trình Angular
  - Programming
  - Web
tags:
  - Angular
  - Angular 2
  - Angular 2 Directives
  - Angular 2 Event
  - Angular 2 Two-way Binding
  - Angular @Input
  - Angular @Output
  - Angular Component
  - Custom Two-way Data Binding
  - Lập Trình Angular 2
  - Web Dev
---
<h2 style="text-align: center;">
  Angular 2 Two-way Binding Và Tạo Custom Two-way Data Binding
</h2>

Angular 2 Component có thể <a href="http://www.tiepphan.com/thu-nghiem-voi-angular-2-truyen-du-lieu-cho-component-voi-input/" target="_blank" rel="noopener noreferrer">truyền vào data với @Input</a> hoặc <a href="http://www.tiepphan.com/thu-nghiem-voi-angular-2-component-event-voi-eventemitter-output/" target="_blank" rel="noopener noreferrer">gửi event ra ngoài với @Output</a>, chúng đều là _**unidirectional data flow** _hay one-way binding. Angular 2 Two-way Binding không là built-in trong Angular 2. Tuy vậy chúng ta vẫn có thể áp dụng Two-way Binding bằng cách sử dụng directive _**ngModel**_ trong Angular 2. Bài học này chúng ta sẽ cùng tìm hiểu về Two-way Binding và cách tạo Custom Two-way Data Binding trong Angular 2.

<!--more-->

### 1. Giới thiệu về Angular 2 Two-way Binding với **_ngModel_**.

Angular 2 có một directive để áp dụng two-way binding đó là _**ngModel**_. Chúng ta có thể bao ngModel trong cặp dấu _**[()]**_, nó sẽ thực hiện đồng bộ dữ liệu từ Component vs DOM và ngược lại.

<pre class="brush:html; highlight:[4]" title="app.component.html">&lt;div&gt;
  &lt;input type="text" 
    (keyup.enter)="updateMesssages()" 
    [(ngModel)]="message"
  &gt;
  &lt;button (click)="updateMesssages()"&gt;Button...&lt;/button&gt;
&lt;/div&gt;</pre>

&nbsp;

<pre class="brush:js;" title="app.component.ts">import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent {
  messages: string[] = [];
  message: string = '';
  updateMesssages() {
    this.messages.push(this.message);
    this.message = '';
  }
}</pre>

Nếu không sử dụng _**[(ngModel)]**_ chúng ta có thể hoàn toàn viết một cú pháp tương ứng cho ví dụ trên như sau:

<pre class="brush:html; highlight:[4,5]" title="app.component.html">&lt;div&gt;
  &lt;input type="text" 
    (keyup.enter)="updateMesssages()" 
    [value]="message" 
    (input)="message = $event.target.value"
  &gt;
  &lt;button (click)="updateMesssages()"&gt;Button...&lt;/button&gt;
&lt;/div&gt;</pre>

Khi không sử dụng directive _**ngModel**_ ở cấu trúc binding bởi cặp dấu [()], chúng ta hoàn toàn có thể tách thành 2 cấu trúc binding riêng biệt là event binding và property binding:

<pre class="brush:html; highlight:[4,5]" title="app.component.html">&lt;div&gt;
  &lt;input type="text" 
    (keyup.enter)="updateMesssages()" 
    [ngModel]="message" 
    (ngModelChange)="message = $event"&gt;
  &lt;button (click)="updateMesssages()"&gt;Button...&lt;/button&gt;
&lt;/div&gt;</pre>

Như các bạn có thể thấy,  directive _**ngModel**_ ở ví dụ minh họa trên bao gồm property _**ngModel**_ và event _**ngModelChange.**_

### 2. Tạo Custom Two-way Data Binding.

Để tạo được Custom Two-way Data Binding, chúng ta kết hợp @Input (property binding) và @Output (event binding) với cú pháp:

Tên của input là _**xyz**_ thì tên của output là _**xyzChange**_.

<pre class="brush:js; highlight:[15,16]" title="switches.component.ts">import { 
  Component, 
  OnInit, 
  Input, 
  Output, 
  EventEmitter 
} from '@angular/core';

@Component({
  selector: 'tp-switches',
  templateUrl: './switches.component.html',
  styleUrls: ['./switches.component.scss']
})
export class SwitchesComponent implements OnInit {
  @Input() checked: boolean = false;                              // input
  @Output('checkedChange') change = new EventEmitter&lt;boolean&gt;();  // output

  constructor() { }

  ngOnInit() {
  }
  emitChangeValue(event) {
    this.change.emit(event.target.checked);
  }
}</pre>

Sử dụng trong một component khác:

<pre class="brush:html; highlight:[2]" title="contact-list.component.html">&lt;div&gt;
  &lt;tp-switches [(checked)]="contact.avatar.round"&gt;
  &lt;/tp-switches&gt;
  &lt;tp-contact-image-detail
    [avatar-url]="contact.avatar?.url"
    [round]="contact.avatar?.round"
  &gt;
  &lt;/tp-contact-image-detail&gt;
&lt;/div&gt;</pre>

> Lưu ý: two-way binding không dùng kết hợp với dạng check null như `contact.avatar?.round` .

Link tham khảo:<a href="https://angular.io/docs/ts/latest/guide/architecture.html#!#data-binding" target="_blank" rel="noopener noreferrer"> https://angular.io/docs/ts/latest/guide/architecture.html#!#data-binding</a>

Code demo: <a href="https://github.com/tieppt/try-angular/tree/lesson-9" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular/tree/lesson-9</a>

### 3. Video bài học.