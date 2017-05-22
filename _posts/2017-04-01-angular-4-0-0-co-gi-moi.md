---
id: 362
title: Angular 4.0.0 Có Gì Mới?
date: 2017-04-01T14:10:17+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=362
permalink: /angular-4-0-0-co-gi-moi/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/03/angular-v4.jpg
categories:
  - Javascript
  - Lập Trình
  - Lập Trình Angular
  - Programming
  - Web
tags:
  - Angular
  - Angular 2
  - Angular 4
  - Angular Component
  - NgFor
  - NgIf
  - Web Dev
---
<h2 style="text-align: center;">
  Angular 4.0.0 Có Gì Mới?
</h2>

Tháng 3-2017, Angular team đã phát hành Angular 4, vậy Angular 4 có gì mới, có những gì thay đổi mà chúng ta cần lưu ý. Bài này sẽ giới thiệu cho các bạn những điểm mới trong Angular 4.

<!--more-->

### 1. Tổng quan

  * New features: Những tính năng mới có trong phiên bản mới.
  * Breaking changes: Những thay đổi ở phiên bản mới có thể làm hệ thống hiện tại bị lỗi khi nâng cấp.
  * Deprecated: Những thay đổi không được sử dụng trong phiên bản mới, và ở phiên bản tiếp theo sẽ bị loại bỏ đi.

### 2. New features

  * Smaller & Faster: new View Engine giúp giảm kích thước code gen ra khoảng 60% so với trước đây.
  * Tương thích với TypeScript 2.1, 2.2, Angular Universal, Source Maps for Templates.

[<img class="aligncenter wp-image-366" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-1.png" alt="angular 4" width="630" height="546" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-1.png 957w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-1-300x260.png 300w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-1-768x665.png 768w" sizes="(max-width: 630px) 100vw, 630px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-1.png)

  * Cải tiến ngIf, ngFor: tạo ra các local variable, if/else:

[<img class="aligncenter size-full wp-image-368" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-2.png" alt="angular 4" width="718" height="505" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-2.png 718w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-2-300x211.png 300w" sizes="(max-width: 718px) 100vw, 718px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-2.png)

  * Giới thiệu NgComponentOutlet và NgTemplateOutlet tương thích với * syntax.

Cú pháp của NgComponentOutlet và NgTemplateOutlet:

[<img class="aligncenter size-full wp-image-369" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-3.png" alt="angular 4" width="754" height="766" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-3.png 754w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-3-295x300.png 295w" sizes="(max-width: 754px) 100vw, 754px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-3.png)

Tạo dynamic component trong Angular:

[<img class="aligncenter size-full wp-image-370" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-4.png" alt="angular 4" width="962" height="935" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-4.png 962w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-4-300x292.png 300w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-4-768x746.png 768w" sizes="(max-width: 962px) 100vw, 962px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-4.png)

[<img class="aligncenter size-full wp-image-371" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-5.png" alt="angular 4" width="1141" height="721" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-5.png 1141w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-5-300x190.png 300w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-5-768x485.png 768w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-5-1024x647.png 1024w" sizes="(max-width: 1141px) 100vw, 1141px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-5.png)

### 3. Breaking changes

  * Lifecyle events: thay thế toàn bộ là interface nên phải thay thế hết kế thừa các event này thành “implements”, không được sử dụng &#8220;extends&#8221; như ở phiên bản 2.
  * Không cho phép deep imports và tất cả các export được đặt ký tự ɵ ở đầu thì không được phép sử dụng trong ứng dụng của bạn.

[<img class="aligncenter size-full wp-image-372" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-6.png" alt="angular 4 lifecycle" width="703" height="732" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-6.png 703w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-6-288x300.png 288w" sizes="(max-width: 703px) 100vw, 703px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-6.png)

Các imports không hợp lệ trong Angular 4:

[<img class="aligncenter size-full wp-image-373" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-7.png" alt="angular 4 imports exports" width="748" height="546" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-7.png 748w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-7-300x219.png 300w" sizes="(max-width: 748px) 100vw, 748px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-7.png)

  * Animation đã tách riêng khỏi @angular/core, thay vào đó là import BrowserAnimationsModule từ @angular/platform-browser/animations và các thành phần như trigger từ @angular/animations.

[<img class="aligncenter size-full wp-image-374" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-8.png" alt="angular 4 animation import" width="289" height="235" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-8.png)

### 4. Deprecated

  * OpaqueToken thay thế bằng InjectionToken<?>

[<img class="aligncenter size-full wp-image-375" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-9.png" alt="angular 4 injectiontoken" width="585" height="126" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-9.png 585w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-9-300x65.png 300w" sizes="(max-width: 585px) 100vw, 585px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-9.png)

  * Renderer thay thế bằng Renderer2
  * <template> thay thế bằng <ng-template>

[<img class="aligncenter size-full wp-image-376" src="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-10.png" alt="angular 4 ng-template" width="675" height="362" srcset="http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-10.png 675w, http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-10-300x161.png 300w" sizes="(max-width: 675px) 100vw, 675px" />](http://www.tiepphan.com/wp-content/uploads/2017/04/angular-4-10.png)

### 5. Video bài học



### 6. Tham khảo

<a href="http://angularjs.blogspot.com/2017/03/angular-400-now-available.html" target="_blank">http://angularjs.blogspot.com/2017/03/angular-400-now-available.html</a>

<a href="https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-0.html" target="_blank">TypeScript strictNullChecks</a>

<a href="https://github.com/angular/angular/blob/master/docs/RELEASE_SCHEDULE.md" target="_blank">Lịch trình phát hành phiên bản và tính tương thích giữa các phiên bản Angular</a>

Ngoài ra, còn khá nhiều các API bị đánh dấu là deprecated, bạn có thể vào trang documentation của Angular để tìm hiểu thêm tại địa chỉ: <a href="https://angular.io/search/#stq=deprecated&stp=1" target="_blank">https://angular.io/search/#stq=deprecated&stp=1</a>