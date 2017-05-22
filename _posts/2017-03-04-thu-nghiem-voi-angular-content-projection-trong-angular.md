---
id: 323
title: 'Thử Nghiệm Với Angular Phần 12: Content Projection Trong Angular'
date: 2017-03-04T13:50:01+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=323
permalink: /thu-nghiem-voi-angular-content-projection-trong-angular/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/03/angular2-12.jpg
categories:
  - Lập Trình
  - Lập Trình Angular
  - Programming
  - Web
tags:
  - Angular
  - Angular 2
  - Angular Component
  - Content Projection
  - Lập Trình Angular 2
  - Web Dev
---
<h2 style="text-align: center;">
  Content Projection Trong Angular
</h2>

Làm thế nào để sử dụng lại các component trong Angular 2+, hay làm sao để có thể nhúng content của một component cho một component khác. Bài học này sẽ giới thiệu cho các bạn về Content Projection trong Angular sử dụng ng-content directive.

<!--more-->

### 1. Nhúng một phần content vào một component

1.1 `ng-content` directive:

Chúng ta sẽ nhúng ng-content directive vào phần component template mà chúng ta mong muốn content sẽ được nhúng vào.

<pre class="brush:html;highlight:[2]" title="card.component.html">&lt;div class="tp-card"&gt;
  &lt;ng-content&gt;&lt;/ng-content&gt;
&lt;/div&gt;</pre>

<pre class="brush:js;" title="card.component.ts">import { Component, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'tp-card',
  templateUrl: './card.component.html',
  styleUrls: ['./card.component.scss'],
  encapsulation: ViewEncapsulation.None
})
export class CardComponent { }
</pre>

Khi ở trong Component khác mà chúng ta muốn nhúng template vào phần đã định nghĩa của Component cho phép nhúng thì chúng ta có thể làm như sau.

<pre class="brush:html;" title="app.component.html">&lt;tp-card&gt;
  &lt;header class="tp-card__title"&gt;Title&lt;/header&gt;
  &lt;div class="tp-card__content"&gt;
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Veniam, molestiae.
  &lt;/div&gt;
  &lt;footer class="tp-card__footer"&gt; 
    &lt;button class="tp-button btn btn-danger"&gt;Action&lt;/button&gt; 
  &lt;/footer&gt;
&lt;/tp-card&gt;</pre>

&nbsp;

1.2 Sử dụng `selector`:

> Khi bạn sử dụng **_selector_**, tất cả các _selector_ nào thỏa mãn sẽ được nhúng vào đúng vị trí đã chọn, dù có nhúng vào **_nhiều hơn một lần_**.

&#8211; Tag selector:

<pre class="brush:html;highlight:[2]" title="card.component.html">&lt;div class="tp-card"&gt;
  &lt;ng-content select="header"&gt;&lt;/ng-content&gt;
&lt;/div&gt;</pre>

&#8211; Class selector:

<pre class="brush:html;highlight:[2]" title="card.component.html">&lt;div class="tp-card"&gt;
  &lt;ng-content select=".tp-card__content"&gt;&lt;/ng-content&gt;
&lt;/div&gt;</pre>

&#8211; Attribute selector:

<pre class="brush:html;highlight:[2]" title="card.component.html">&lt;div class="tp-card"&gt;
  &lt;ng-content select="[data-footer=cool-footer]"&gt;&lt;/ng-content&gt;
&lt;/div&gt;</pre>

&#8211; Sử dụng nhiều selector:

<pre class="brush:html;highlight:[2]" title="card.component.html">&lt;div class="tp-card"&gt;
  &lt;ng-content select="footer[data-footer=cool-footer]"&gt;&lt;/ng-content&gt;
&lt;/div&gt;</pre>

Template từ Component muốn nhúng vào.

<pre class="brush:html;" title="app.component.html">&lt;tp-card&gt;
  &lt;header class="tp-card__title"&gt;Title&lt;/header&gt;
  &lt;div class="tp-card__content"&gt;
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Veniam, molestiae.
  &lt;/div&gt;
  &lt;footer class="tp-card__footer" data-footer="cool-footer"&gt; 
    &lt;button class="tp-button btn btn-danger"&gt;Action&lt;/button&gt; 
  &lt;/footer&gt;
&lt;/tp-card&gt;</pre>

### 2. Nhúng nhiều phần content vào một component

Việc nhúng nhiều phần content hoàn toàn được phép, bạn có thể nhúng nhiều phần khác nhau ví dụ như:

<pre class="brush:html;highlight:[2,3,4]" title="card.component.html">&lt;div class="tp-card"&gt;
 &lt;ng-content select="header"&gt;&lt;/ng-content&gt;
 &lt;ng-content select=".tp-card__content"&gt;&lt;/ng-content&gt;
 &lt;ng-content select="footer"&gt;&lt;/ng-content&gt;
&lt;/div&gt;</pre>

> Lưu ý: thứ tự đặt của _ng-content_ sẽ có tác động đến thứ tự truyền vào từ Component khác, nếu Component khác truyền Template vào với thứ tự khác, thì thứ tự hiển thị sẽ **_tuân theo thứ tự của Component khai báo ng-content_**.

Ví dụ như bạn nhúng content như sau:

<pre class="brush:html;" title="app.component.html">&lt;tp-card&gt;
  &lt;header class="tp-card__title"&gt;Title&lt;/header&gt;
  &lt;footer class="tp-card__footer" data-footer="cool-footer"&gt; 
    &lt;button class="tp-button btn btn-danger"&gt;Action&lt;/button&gt; 
  &lt;/footer&gt;
  &lt;div class="tp-card__content"&gt;
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Veniam, molestiae.
  &lt;/div&gt;
&lt;/tp-card&gt;</pre>

### 3. Video bài học



### 4. Tham khảo

Code repo: <a href="https://github.com/tieppt/try-angular/tree/lesson-12" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular/tree/lesson-12</a>

&nbsp;