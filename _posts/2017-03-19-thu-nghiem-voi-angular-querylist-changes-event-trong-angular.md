---
id: 350
title: 'Thử Nghiệm Với Angular Phần 14 &#8211; QueryList Changes Event Trong Angular'
date: 2017-03-19T16:06:57+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=350
permalink: /thu-nghiem-voi-angular-querylist-changes-event-trong-angular/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/03/angular2-14.jpg
categories:
  - Javascript
  - Lập Trình
  - Lập Trình Angular
  - Programming
  - Web
tags:
  - Angular
  - Angular 2
  - Angular 2 Event
  - Angular Component
  - Javascript
  - Lập Trình Angular 2
  - QueryList Changes Event
  - Web Dev
---
<h2 style="text-align: center;">
  QueryList Changes Event Trong Angular
</h2>

Trong bài học trước, chúng ta đã &#8220;<a href="http://www.tiepphan.com/thu-nghiem-voi-angular-thuc-hanh-content-projection-va-lifecycle-angular/" target="_blank" rel="noopener noreferrer">Thực Hành Content Projection Và Lifecycle Liên Quan Trong Angular</a>&#8220;, với phiên bản code đó khi chúng ta làm việc với async như gọi api để lấy dữ liệu rồi in ra thì liệu app của chúng ta có chạy đúng. Bài học này sẽ giải quyết vấn đề chúng ta gặp phải khi cần phải hook vào QueryList Changes Event Trong Angular nhằm theo dõi khi nào đối tượng này thay đổi để áp dụng các logic liên quan.

<!--more-->

Với phiên bản code từ bài học trước liệu rằng khi chúng ta làm việc với dữ liệu async thì app của chúng ta sẽ chạy đúng. Lúc này, chúng ta gặp phải một vấn đề đó là mặc dù chúng ta đã để `[multiple]="false"` nhưng app lại chạy không như chúng ta mong muốn.

<pre class="brush:html" title="app.component.html">&lt;tp-collapse-group [multiple]="false"&gt;
  &lt;tp-collapse
    *ngFor="let post of posts" [title]="post.title" [selected]="false"&gt;
    &lt;div&gt;
      {{ post.body }}
    &lt;/div&gt;
  &lt;/tp-collapse&gt;
&lt;/tp-collapse-group&gt;
</pre>

<pre class="brush:js" title="app.component.ts">import { Component, OnInit } from '@angular/core';
import { POSTS } from './services/post';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent implements OnInit {
  posts: any[] = [];
  ngOnInit() {
    setTimeout(() =&gt; {
      this.posts = POSTS.slice();
    }, 500);
  }
}</pre>

Bây giờ, chúng ta cần quan sát đối tượng của QueryList thay đổi như thế nào để có các hành động tương ứng bằng việc subscribe vào Changes Event của đối tượng đó như sau:

<pre class="brush:js">this.collapses.changes.subscribe((object) =&gt; {
  // do something here
});</pre>

Ví dụ như trong app của chúng ta đang phát triển, chúng ta cần quan sát sự thay đổi của list CollapseComponent để thực hiện quản lý ở mode accordion như sau:

<pre class="brush:js">this.collapses.changes.subscribe(() =&gt; {
  this.clearListener();
  this.initListener();
});</pre>

Việc quan sát này thực sự cẩn thiết khi chúng ta cần phải áp dụng một phần logic nào đó để Component của chúng ta chạy đúng, chẳng hạn như mong muốn của chúng ta là CollapseGroupComponent chỉ thực hiện cho phép một CollapseComponent được phép mở ở tại một thời điểm nếu chúng ta set cho mode của group là accordion.

Thêm vào đó, khi thực hiện subscribe bằng code như trên, chúng ta đã tạo ra một object của class Subscription, vậy nên khi Component bị destroy thì chúng ta nên (phải) hủy object đó đi như sau:

<pre class="brush:js">// some method
this._changeSubs = this.collapses.changes.subscribe(() =&gt; {
  this.clearListener();
  this.initListener();
});

// on destroy
ngOnDestroy() {
  if (this._changeSubs) {
    this._changeSubs.unsubscribe();
  }
}</pre>

Đơn giản phải không nào!

Và code hoàn thiện của **CollapseGroupComponent** như sau:

<pre class="brush:js">import { Component, OnInit, AfterContentInit, Input, ContentChildren, QueryList, OnDestroy } from '@angular/core';
import { CollapseComponent } from "../collapse/collapse.component";
import { Subscription } from "rxjs/Rx";

@Component({
  selector: 'tp-collapse-group',
  templateUrl: './collapse-group.component.html',
  styleUrls: ['./collapse-group.component.scss']
})
export class CollapseGroupComponent implements OnInit, AfterContentInit, OnDestroy {
  @ContentChildren(CollapseComponent) collapses: QueryList&lt;CollapseComponent&gt;;
  @Input() multiple: boolean = true;

  private _subscriptions: Subscription[] = [];
  private _changeSubs: Subscription;
  constructor() { }

  ngOnInit() {
  }

  ngAfterContentInit() {
    this.initListener();
    this._changeSubs = this.collapses.changes.subscribe(() =&gt; {
      this.clearListener();
      this.initListener();
    });
  }

  initListener() {
    this.collapses.forEach(collapse =&gt; {
      let subscription = collapse.selectedChange.subscribe(coll =&gt; {
        if (!this.multiple && coll.selected) {
          this.toggleCollapse(coll);
        }
      });
      this._subscriptions.push(subscription);
    });
  }

  toggleCollapse(collapse) {
    this.collapses.forEach(c =&gt; {
      if (c.collapseId != collapse.collapseId) {
        c.selected = false;
      }
    });
  }

  clearListener() {
    if (this._subscriptions && this._subscriptions.length) {
      this._subscriptions.forEach(sub =&gt; sub.unsubscribe());
    }
    this._subscriptions = [];
  }

  ngOnDestroy() {
    this.clearListener();
    if (this._changeSubs) {
      this._changeSubs.unsubscribe();
    }
  }

}</pre>

Video bài học:
  


Source code: <a href="https://github.com/tieppt/try-angular/tree/lesson-14" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular/tree/lesson-14</a>