---
id: 94
title: 'C++ Bài 13: Khai Báo Hàm &#8211; Function Prototype &#8211; trong C++'
date: 2016-10-15T15:48:30+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=94
permalink: /cpp-bai-13-khai-bao-ham-function-prototype/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/10/cpp13.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - hàm
  - Học lập trình C++
---
<h2 class="watch-title-container" style="text-align: center;">
  <span id="eow-title" class="watch-title watch-editable" dir="ltr" title="C++ Bài 13: Khai Báo Hàm - Function Prototype - trong C++ [HD]">C++ Bài 13: Khai Báo Hàm &#8211; Function Prototype &#8211; trong C++</span>
</h2>

Trong bài này, chúng ta cùng tìm hiểu về Nguyên mẫu hàm, hay khai báo hàm trong C++ thông qua các ví dụ cơ bản. Function Protytpe trong C++.

<!--more-->

C++ Function:
  
<a href="http://en.cppreference.com/w/cpp/language/function" target="_blank">http://en.cppreference.com/w/cpp/language/function</a>
  
<a href="http://www.cplusplus.com/doc/tutorial/functions/" target="_blank">http://www.cplusplus.com/doc/tutorial/functions/</a>
  

  
Code ví dụ tính tổng dãy dùng hàm: 1 + 1/2! + 1/3! + 1/4! + &#8230; + 1/n!

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

/**
* Chuong trinh tinh 1 + 1/2! + 1/3! + 1/4! + ... + 1/n!
*/


double tongDay(int);  // khai bao ham
double giaiThua(int); // khai bao ham

int main()
{
	while (true)
	{
		cout &lt;&lt; "Nhap so n can tim: ";
		int so;
		cin &gt;&gt; so;
		if (so &lt; 1)
		{
			continue;
		}
		cout &lt;&lt; "Ket qua: " &lt;&lt; tongDay(so) &lt;&lt; endl;
		char c;
		cout &lt;&lt; "Ban co muon tiep tuc: (y/n) ";
		cin &gt;&gt; c;
		if (c == 'n')
		{
			cout &lt;&lt; "Ket thuc chuong trinh.\n";
			break;
		}
	}
	
	return 0;
}

// Dinh nghia ham
double giaiThua(int num)
{
	double rs = 1.0;
	for (int i = 2; i &lt;= num; ++i)
	{
		rs *= i;
	}
	return rs;
}

double tongDay(int n)
{
	double r = 1;
	for (int i = 2; i &lt;= n; ++i)
	{
		r += 1.0 / giaiThua(i);
	}
	return r;
}
</pre>

&nbsp;