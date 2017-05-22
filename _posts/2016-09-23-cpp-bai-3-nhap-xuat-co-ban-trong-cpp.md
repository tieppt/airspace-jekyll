---
id: 33
title: 'C++ &#8211; Bài 3: Nhập Xuất Cơ Bản trong C++'
date: 2016-09-23T12:37:20+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=33
permalink: /cpp-bai-3-nhap-xuat-co-ban-trong-cpp/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/cpp3.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ &#8211; Bài 3: Nhập Xuất Cơ Bản trong C++
</h2>

Tìm hiểu về nhập xuất cơ bản trong C++ sử dụng std::cout và std::cin.

Trong Visual Studio nhấn Ctrl+F5 để chạy không vào debug.

<!--more-->

<pre class="theme:vs2012-black lang:c++ decode:true " title="Basic input output">#include &lt;iostream&gt;
#include &lt;string&gt;

using namespace std;

int main()
{
	int age;
	cout &lt;&lt; "Nhap tuoi: ";
	cin &gt;&gt; age;
	cout &lt;&lt; "\nBan nam nay: " &lt;&lt; age &lt;&lt; " tuoi." &lt;&lt; endl;

	return 0;
}</pre>

&nbsp;