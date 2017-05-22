---
id: 55
title: 'C++ &#8211; Bài 6: Các Toán Tử Cơ Bản trong C++'
date: 2016-09-23T15:06:20+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=55
permalink: /cpp-bai-6-cac-toan-tu-co-ban-trong-cpp/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/cpp6.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ &#8211; Bài 6: Các Toán Tử Cơ Bản trong C++
</h2>

Trong video này, tôi hướng dẫn các bạn tìm hiểu các toán tử cơ bản nhất trong Ngôn ngữ lập trình C++.

Video giới thiệu các toán tử cơ bản nhất, các toán tử nâng cao hơn sẽ được giới thiệu trong các video sau.
  
<!--more-->


  
Common operators: + &#8211; * / %
  
Assignment: f = (9/5) * c + 32.0
  
Compound assignment operators: += -= *= /= %=
  
Fibonaci: 1 1 2 3 5 8 13 21
  
Increment and Decrement operator: ++ &#8212; ++i i++
  
Comparison Operator: toán tử quan hệ. > < == != >= <=
  
C++ Operator Precedence: <a class=" yt-uix-servicelink " href="http://en.cppreference.com/w/cpp/language/operator_precedence" target="_blank" rel="nofollow" data-servicelink="CDEQ6TgiEwiXnOKf4KXPAhVCH1gKHeXACJko-B0" data-url="http://en.cppreference.com/w/cpp/language/operator_precedence">http://en.cppreference.com/w/cpp/language/operator_precedence</a>
  


<pre class="theme:vs2012-black lang:c++ decode:true ">#include &lt;iostream&gt;
using namespace std;

int main()
{
	int sokgthocconlai = 25;
	int sokgthoccan = 25;

	bool kq = sokgthocconlai == sokgthoccan;

	cout &lt;&lt; kq &lt;&lt; endl;

	return 0;
}</pre>

&nbsp;