---
id: 384
title: 'Thử Nghiệm Với Angular Phần 15 &#8211; Pipe Trong Angular'
date: 2017-04-10T02:53:51+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=384
permalink: /thu-nghiem-voi-angular-pipe-trong-angular/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/04/angular15.jpg
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
  - Angular Component
  - Angular Pipe
  - Lập Trình Angular 2
---
<h2 style="text-align: center;">
  Pipe Trong Angular
</h2>

Bạn có dữ liệu nhận được từ đâu đó &#8211; từ API trả về &#8211; cho kiểu Date là dãy số kiểu long, bây giờ bạn phải hiển thị dữ liệu đó thành dạng mà người dùng có thể hiểu được trong ứng dụng viết bằng Angular. Làm thế nào để thực hiện điều đó trong Angular? Bài học này sẽ giới thiệu cho các bạn về Pipe trong Angular &#8211; một thành phần cơ bản của Angular.
  
<!--more-->


  
Chúng ta sẽ cùng tìm hiểu các câu hỏi như:

  * [Pipe là gì?](#tnva-pipe-la-gi)
  * [Pipe sử dụng như thế nào?](#tnva-su-dung-pipe)
  * [Cách tạo một Custom Pipe trong Angular như thế nào?](#tnva-tao-custom-pipe)

[Chuyển xuống video.](#tnva-pipe-video)

### 1. Pipe là gì? {#tnva-pipe-la-gi}

> Pipes transform displayed values within a template.

Pipe được dùng để chuyển đổi dữ liệu mà bạn hiển thị lên template cho người dùng có thể hiểu được.

Ví dụ: định dạng ngày tháng cho kiểu Date, viết hoa các chữ cái đầu tiên của tên riêng như tên người, tên thành phố, etc.

Pipe nhận một đầu vào và cho kết quả ở đầu ra, giống hình minh họa sau:<figure id="attachment_389" style="width: 690px" class="wp-caption aligncenter">

[<img class="size-full wp-image-389" src="http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-what-is-it.png" alt="Pipe là gì?" width="690" height="444" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-what-is-it.png 690w, http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-what-is-it-300x193.png 300w" sizes="(max-width: 690px) 100vw, 690px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-what-is-it.png)<figcaption class="wp-caption-text">Pipe là gì?</figcaption></figure> 

Angular cung cấp cho chúng ta các Pipes sau đây (những Pipes là Stable):

<ul class="api-list">
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/AsyncPipe-pipe.html" target="_blank" rel="noopener noreferrer">AsyncPipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/CurrencyPipe-pipe.html" target="_blank" rel="noopener noreferrer">CurrencyPipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/DatePipe-pipe.html" target="_blank" rel="noopener noreferrer">DatePipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/DecimalPipe-pipe.html" target="_blank" rel="noopener noreferrer">DecimalPipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/JsonPipe-pipe.html" target="_blank" rel="noopener noreferrer">JsonPipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/LowerCasePipe-pipe.html" target="_blank" rel="noopener noreferrer">LowerCasePipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/PercentPipe-pipe.html" target="_blank" rel="noopener noreferrer">PercentPipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/SlicePipe-pipe.html" target="_blank" rel="noopener noreferrer">SlicePipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/TitleCasePipe-pipe.html" target="_blank" rel="noopener noreferrer">TitleCasePipe</a>
  </li>
  <li class="api-item ng-scope">
    <a class="ng-binding" href="https://angular.io/docs/ts/latest/api/common/index/UpperCasePipe-pipe.html" target="_blank" rel="noopener noreferrer">UpperCasePipe</a>
  </li>
</ul><figure id="attachment_391" style="width: 893px" class="wp-caption aligncenter">

[<img class="size-full wp-image-391" src="http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-list-item.png" alt="List Pipes trong Angular" width="893" height="149" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-list-item.png 893w, http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-list-item-300x50.png 300w, http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-list-item-768x128.png 768w" sizes="(max-width: 893px) 100vw, 893px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-list-item.png)<figcaption class="wp-caption-text">List Pipes trong Angular</figcaption></figure> 

Trong đó có TitleCasePipe là pipe có từ phiên bản Angular 4.

All Angular Pipes: <a href="https://angular.io/docs/ts/latest/api/#!?query=pipe" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/api/#!?query=pipe</a>

> Lưu ý rằng Angular không có FilterPipe or OrderByPipe như Angularjs.

### 2. Pipe sử dụng như thế nào? {#tnva-su-dung-pipe}

> The `Date` and `Currency` pipes need the _ECMAScript Internationalization API_. Safari and other older browsers don&#8217;t support it. You can add support with a polyfill.
> 
> Nếu bạn sử dụng `Date` và `Currency` pipes thì bạn cần phải có thêm polyfill để support trên các trình duyệt cũ, bằng việc thêm đoạn script sau vào file _index.html_
> 
> <pre class="brush:html">&lt;script src="https://cdn.polyfill.io/v2/polyfill.min.js?features=Intl.~locale.en"&gt;&lt;/script&gt;</pre>
> 
> Hoặc nếu bạn sử dụng Angular CLI thì chạy lệnh cài đặt `npm install --save intl` và uncomment dòng sau trong file polyfill.ts
> 
> <a href="https://github.com/tieppt/try-angular-2/blob/lesson-15/contact-app/src/polyfills.ts#L68" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular-2/blob/lesson-15/contact-app/src/polyfills.ts#L68</a>

Chúng ta có thể sử dụng một pipe duy nhất, có thể bao gồm cả tham số, hoặc có thể sử dụng pipe theo tuần tự &#8211; với kết quả của pipe này là đầu vào của pipe tiếp theo.
  
Ví dự sử dụng Pipe `lowercase` và `uppercase`: (sử dụng không có tham số)

<pre class="brush:js;highlight:[5,6]">@Component({
  selector: 'lowerupper-pipe',
  template: `&lt;div&gt;
    &lt;label&gt;Name: &lt;/label&gt;&lt;input #name (keyup)="change(name.value)" type="text"&gt;
    &lt;p&gt;In lowercase: &lt;pre&gt;'{{value | lowercase}}'&lt;/pre&gt;
    &lt;p&gt;In uppercase: &lt;pre&gt;'{{value | uppercase}}'&lt;/pre&gt;
  &lt;/div&gt;`
})
export class LowerUpperPipeComponent {
  value: string;
  change(value: string) { 
    this.value = value; 
  }
}</pre>

Sử dụng có tham số như Pipe `date`:

<pre class="brush:js;highlight:[4,5,6]">@Component({
  selector: 'date-pipe',
  template: `&lt;div&gt;
    &lt;p&gt;Today is {{today | date}}&lt;/p&gt;
    &lt;p&gt;Or if you prefer, {{today | date:'fullDate'}}&lt;/p&gt;
    &lt;p&gt;The time is {{today | date:'jmZ'}}&lt;/p&gt;
  &lt;/div&gt;`
})
export class DatePipeComponent {
  today: number = Date.now();
}</pre>

Sử dụng nhiều tham số như Pipe `slice`:

<pre class="brush:js;highlight:[4]">@Component({
  selector: 'slice-list-pipe',
  template: `&lt;ul&gt;
    &lt;li *ngFor="let i of collection | slice:1:3"&gt;{{i}}&lt;/li&gt;
  &lt;/ul&gt;`
})
export class SlicePipeListComponent {
  collection: string[] = ['a', 'b', 'c', 'd'];
}</pre>

Sử dụng nhiều Pipe tuần tự &#8211; Chaining Pipe:

Chúng ta có thể sử dụng nhiều Pipes để có được kết quả mong muốn.<figure id="attachment_395" style="width: 721px" class="wp-caption aligncenter">

[<img class="size-full wp-image-395" src="http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-chain-pipe.png" alt="Chain Pipe" width="721" height="490" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-chain-pipe.png 721w, http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-chain-pipe-300x204.png 300w" sizes="(max-width: 721px) 100vw, 721px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/pipe-chain-pipe.png)<figcaption class="wp-caption-text">Chain Pipe</figcaption></figure> 

<pre class="brush:js;highlight:[4,5,6]">@Component({
  selector: 'date-pipe',
  template: `&lt;div&gt;
    &lt;p&gt;Today is {{today | date | lowercase}}&lt;/p&gt;
    &lt;p&gt;Or if you prefer, {{today | date:'fullDate' | lowercase}}&lt;/p&gt;
    &lt;p&gt;The time is {{today | date:'jmZ' | uppercase}}&lt;/p&gt;
  &lt;/div&gt;`
})
export class DatePipeComponent {
  today: number = Date.now();
}</pre>

Trong Angular chia làm hai loại Pipe là **pure pipe** và **impure pipe**.

Pure pipe: chỉ thực hiện thay đổi khi đầu vào thay đổi. (các immutable objects, primitive type: string, number, boolean, etc): lowercase, uppercase, date, etc.

Impure pipe: thực hiện thay đổi mỗi chu kỳ của Change detection (chu kỳ kiểm tra xem các state trong ứng dụng có thay đổi không để update lên view): async, json, etc.

### 3. Cách tạo một Custom Pipe trong Angular như thế nào? {#tnva-tao-custom-pipe}

Đầu tiên, chúng ta tạo một class và decorate nó với decorator _**@Pipe**_, decorator này cần tối thiểu một object có property _**name**_, chính là tên của pipe.

Ví dụ, chúng ta có thể tạo một pipe để convert nhiệt độ giữa độ C và độ F với tên _tempConverter_ như sau:

<pre class="brush:js">import { Pipe } from '@angular/core';

@Pipe({
  name: 'tempConverter'
})
export class TempConverterPipe {
}</pre>

> Mặc định khi tạo là pure pipe.

Tiếp theo, chúng ta cần implement một interface là _**PipeTransform**_, và implement hàm _transform_ của interface đó:

<pre class="brush:js">import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
 name: 'tempConverter'
})
export class TempConverterPipe implements PipeTransform {
  transform(value: any, ...args: any[]): any {
  }
}</pre>

Trong hàm transform, chúng ta sẽ thực hiện các công việc để biến đổi đầu vào ra kết quả mong muốn ở đầu ra.

Lưu ý: chúng ta sử dụng <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters" target="_blank" rel="noopener noreferrer">Rest parameters của ES2015</a> &#8220;&#8230;args&#8221; để nhận tất cả các tham số được truyền vào cho pipe.

Sau khi hoàn thành implement class Pipe ở trên, chúng ta cần khai báo vào NgModule mà nó thuộc về để có thể sử dụng nó trong toàn module đó:

<pre class="brush:js">import { TempConverterPipe } from './pipes/temp-converter.pipe';

@NgModule({
  declarations: [
    // các Component, Directive, Pipe khác
    TempConverterPipe
  ],
  imports: [...],
  providers: [...],
  //...
})
export class AppModule { }</pre>

Code hoàn chỉnh cho Pipe converter tại đây: <a href="https://github.com/tieppt/try-angular-2/blob/lesson-15/contact-app/src/app/pipes/temp-converter.pipe.ts" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular-2/blob/lesson-15/contact-app/src/app/pipes/temp-converter.pipe.ts</a>

Sử dụng pipe ở trong Component như sau:

<pre class="brush:html"> Temperature {{ temp | tempConverter:true:'F' }}</pre>

### 4. Video bài học {#tnva-pipe-video}



### 5. Tham khảo

Angular Pipe Official Document: <a href="https://angular.io/docs/ts/latest/guide/pipes.html" target="_blank" rel="noopener noreferrer">https://angular.io/docs/ts/latest/guide/pipes.html</a>

Code: <a href="https://github.com/tieppt/try-angular/tree/lesson-15" target="_blank" rel="noopener noreferrer">https://github.com/tieppt/try-angular/tree/lesson-15</a>

&nbsp;