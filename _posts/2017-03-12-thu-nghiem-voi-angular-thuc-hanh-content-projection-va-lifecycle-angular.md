---
id: 335
title: 'Thử Nghiệm Với Angular Phần 13: Thực Hành Content Projection Và Lifecycle Liên Quan Trong Angular'
date: 2017-03-12T08:13:55+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=335
permalink: /thu-nghiem-voi-angular-thuc-hanh-content-projection-va-lifecycle-angular/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/03/angular13.jpg
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
  - Angular Lifecycle
  - Content Projection
  - Lập Trình Angular 2
---
<h2 style="text-align: center;">
  Thực Hành Content Projection Và Lifecycle Liên Quan Trong Angular
</h2>

Content Projection là một concept khá hay trong Angular, giúp chúng ta có thể dễ dàng tạo các component có khả năng tái sử dụng cao. Bài học này chúng ta sẽ tạo các Component để tìm hiểu chi tiết hơn về Content Projection và các Lifecycle liên quan khi sử dụng.

<!--more-->

### 1. Các thành phần cơ bản của app.

Trong bài học này chúng ta sẽ tạo mới hai component là **CollapseGroupComponent** và **CollapseComponent. **Trong đó **CollapseGroupComponent** sẽ chịu trách nhiệm quản lý các component **CollapseComponent** như sau:

<pre class="brush:html; highlight:[1,2,8]" title="app.component.html">&lt;tp-collapse-group [multiple]="false"&gt;
  &lt;tp-collapse [title]="'First block'" [selected]="true"&gt;
    &lt;span&gt;
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
      Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
    &lt;/span&gt;
  &lt;/tp-collapse&gt;
  &lt;tp-collapse [title]="'Second block'" [selected]="false"&gt;
    &lt;span&gt;
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
      Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
    &lt;/span&gt;
  &lt;/tp-collapse&gt;
&lt;/tp-collapse-group&gt;</pre>

### 2. Cài đặt:

Cài đặt chi tiết của các component như sau:

#### 2.1 CollapseGroupComponent

<pre class="brush: html" title="collapse-group.component.html">&lt;div class="collapsible"&gt;
  &lt;ng-content select="tp-collapse"&gt;&lt;/ng-content&gt;
&lt;/div&gt;</pre>

<pre class="brush: js" title="collapse-group.component.ts">import { Component, OnInit, AfterContentInit, Input, ContentChildren, QueryList, OnDestroy } from '@angular/core';
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
  constructor() { }

  ngOnInit() {
  }

  ngAfterContentInit() {
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

  ngOnDestroy() {
    if (this._subscriptions && this._subscriptions.length) {
      this._subscriptions.forEach(sub =&gt; sub.unsubscribe());
    }
    this._subscriptions = [];
  }

}</pre>

Ở dòng 11, chúng ta sử dụng **@ContentXXX** để query các phần tử được nhúng vào thông qua _ng-content_ mà chúng ta đã cài đặt ở template. Trong trường hợp ở trên, chúng ta muốn query tất cả các phần tử là CollapseComponent.

Bây giờ, để sử dụng các element, chúng ta cần hook vào lifecycle là ngAfterContentInit, kết quả là chúng ta có một mảng element để thao tác.

Về mặt logic, lúc này chúng ta kiểm tra xem Component này có cho phép multiple CollapseComponent được open cùng một lúc không, nếu không thì chúng ta phải thực hiên việc đóng các component khác mà đang open khi muốn open một thằng khác.

Dòng 22 chúng ta subscribe vào event emitter của CollapseComponent để thực hiện việc quản lý trạng thái của chúng.

Khi component CollapseGroupComponent bị hủy, chúng ta cũng thực hiện xóa bỏ các phần dữ liệu không cần thiết như: hủy các event listener đang tồn tại chẳng hạn.

#### 2.2 CollapseComponent:

<pre class="brush:html" title="collapse.component.html">&lt;header class="collapsible-header" (click)="toggleSelected()"&gt;
  {{ title }}
&lt;/header&gt;
&lt;section class="collapsible-body" [class.active]="selected"&gt;
  &lt;ng-content&gt;&lt;/ng-content&gt;
&lt;/section&gt;</pre>

<pre class="brush: js" title="collapse.component.ts">import { Component, OnInit, Input, ViewEncapsulation, Output, EventEmitter } from '@angular/core';

export interface DataCollapseChange {
  collapseId: string;
  selected: boolean;
}

let uuid: number = 1;

@Component({
  selector: 'tp-collapse',
  templateUrl: './collapse.component.html',
  styleUrls: ['./collapse.component.scss'],
  encapsulation: ViewEncapsulation.None
})
export class CollapseComponent implements OnInit {
  @Input() title: string = '';
  @Input() selected: boolean = false;
  @Output() selectedChange: EventEmitter&lt;DataCollapseChange&gt; = new EventEmitter&lt;DataCollapseChange&gt;();
  private _id: number;
  constructor() { }

  ngOnInit() {
    this._id = ++uuid;
  }

  get collapseId() {
    return 'tp-collapse-' + this._id;
  }

  toggleSelected() {
    this.selected = !this.selected;
    this.selectedChange.emit({
      collapseId: this.collapseId,
      selected: this.selected
    });
  }
}</pre>

Dòng 3 đến 6 chúng ta định nghĩa một kiểu dữ liệu để thực hiện trả về khi component thay đổi trạng thái của nó. Component này đơn giản chỉ nhận đầu vào, hiển thị và có thể gửi lại một event là selectedChange.

#### 2.3 ContentChild vs ContentChildren vs ViewChild vs ViewChildren.

Content: là các phần tử được truyền vào theo ng-content hay content projection.

View: là các phần tử nội tại của component đó, có thể hiểu là phần DOM mà bạn cài đặt.

Ví dụ trong CollapseComponent thì phần _header_ là view, còn phần được truyền vào qua _ng-content_ là _content_.

XXXChild vs XXXChildren: thì XXXChild nó sẽ trả về 1 phần tử, còn XXXChildren trả về một list các phần tử.

### 

### 3. Video bài học:



### 4. Tham khảo:

Source code: <a href="https://github.com/tieppt/try-angular/tree/lesson-13" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular/tree/lesson-13</a>

Docs:

<a href="https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html</a>

<a href="https://angular.io/docs/ts/latest/api/core/index/ContentChild-decorator.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/api/core/index/ContentChild-decorator.html</a>

<a href="https://angular.io/docs/ts/latest/api/core/index/ContentChildren-decorator.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/api/core/index/ContentChildren-decorator.html</a>

<a href="https://angular.io/docs/ts/latest/api/core/index/ViewChild-decorator.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/api/core/index/ViewChild-decorator.html</a>

<a href="https://angular.io/docs/ts/latest/api/core/index/ViewChildren-decorator.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/api/core/index/ViewChildren-decorator.html</a>

<a href="https://angular.io/docs/ts/latest/api/core/index/Query-class.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/api/core/index/Query-class.html</a>

<a href="https://angular.io/docs/ts/latest/api/core/index/QueryList-class.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/api/core/index/QueryList-class.html</a>