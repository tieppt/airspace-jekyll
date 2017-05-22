---
id: 52
title: 'C++ &#8211; Bài 5: Ép Kiểu giữa Các Kiểu Dữ Liệu trong C++'
date: 2016-09-23T14:57:35+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=52
permalink: /cpp-bai-5-ep-kieu-giua-cac-kieu-du-lieu-trong-cpp/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/cpp5.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ &#8211; Bài 5: Ép Kiểu giữa Các Kiểu Dữ Liệu trong C++
</h2>

Cùng tìm hiểu việc thực hiện chuyển đổi kiểu dữ liệu trong C++.

Đây là nội dung quan trọng trong một chương trình máy tính. Chúng ta cùng tìm hiểu kỹ hơn trong video.

<!--more-->

Type Casting:
  
Implicit type conversion
  
Explicit type conversion: C-style cast expression, functional cast expression, static_cast

<a class=" yt-uix-servicelink " href="http://en.cppreference.com/w/cpp/language/explicit_cast" target="_blank" rel="nofollow" data-url="http://en.cppreference.com/w/cpp/language/explicit_cast" data-servicelink="CDEQ6TgiEwiKpcrN0KXPAhUKmVgKHTmcCkEo-B0">http://en.cppreference.com/w/cpp/language/explicit_cast</a>

Bảng mã ASCII: <a class=" yt-uix-servicelink " href="https://vi.wikipedia.org/wiki/ASCII" target="_blank" rel="nofollow" data-url="https://vi.wikipedia.org/wiki/ASCII" data-servicelink="CDEQ6TgiEwiKpcrN0KXPAhUKmVgKHTmcCkEo-B0">https://vi.wikipedia.org/wiki/ASCII</a>
  


<pre class="theme:vs2012-black lang:c++ decode:true " title="Type Casting">#include &lt;iostream&gt;

using namespace std;

int main()
{
	int character = 'A'; // ep kieu ngam dinh
	double lat = 1000000.234234;
	short intlat = short (lat);
	char c = (char)character;
	int mylat = static_cast&lt;int&gt;(lat);

	double abc = double(5) / 2;

	cout &lt;&lt; abc &lt;&lt; endl;
	return 0;
}</pre>

&nbsp;