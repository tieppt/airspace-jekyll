---
id: 83
title: 'C++ Bài 10: Vòng Lặp Lồng Nhau và Các Lệnh Nhảy trong Vòng Lặp trong C++'
date: 2016-10-08T21:33:17+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=83
permalink: /cpp-bai-10-vong-lap-long-nhau-lenh-nhay/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/10/cp10p.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 class="watch-title-container" style="text-align: center;">
  <span id="eow-title" class="watch-title watch-editable" dir="ltr" title="C++ Bài 10: Vòng Lặp Lồng Nhau và Các Lệnh Nhảy trong Vòng Lặp trong C++ [HD]">C++ Bài 10: Vòng Lặp Lồng Nhau và Các Lệnh Nhảy trong Vòng Lặp trong C++</span>
</h2>

Bài học này mình giới thiệu về vòng lặp lồng nhau và các lệnh nhảy trong vòng lặp. Các ví dụ cơ bản để các bạn nắm được kiến thức về chúng.

break statement: <a href="http://en.cppreference.com/w/cpp/language/break" target="_blank">http://en.cppreference.com/w/cpp/language/break</a>
  
continue statement: <a href="http://en.cppreference.com/w/cpp/language/continue" target="_blank">http://en.cppreference.com/w/cpp/language/continue</a>

<!--more-->


  

  
Code:

Chương trình in bảng cửu chương:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;
#include &lt;iomanip&gt;

using namespace std;

int main()
{
	cout &lt;&lt; "Chuong trinh in ra Bang cuu chuong:\n";
	for (int i = 2; i &lt; 10; ++i)
	{
		for (int j = 1; j &lt; 10; ++j)
		{
			cout &lt;&lt; i &lt;&lt; "x" &lt;&lt; j &lt;&lt; "=" &lt;&lt; left &lt;&lt; setw(2) &lt;&lt; i * j &lt;&lt; setw(4) &lt;&lt; " ";
		}
		cout &lt;&lt; endl;
	}
	return 0;
}</pre>

Break Demo Application:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

using namespace std;

int main()
{
	cout &lt;&lt; "Break demo application!\n";
	double sum = 0.0;
	int soLuot = 1;
	const int LUOT_MAX = 5;

	while (soLuot &lt;= LUOT_MAX)
	{
		cout &lt;&lt; "Nhap vao so tien thuong: ";
		double soTien = 0.0;
		cin &gt;&gt; soTien;
		sum += soTien;
		if (sum &gt;= 1000.0)
		{
			cout &lt;&lt; "Ban da nhan toi da so tien duoc nhan.\n";
			break;
		}
		++soLuot;
	}
	cout &lt;&lt; "Ket thuc.\n";
	return 0;
}</pre>

Continue Demo Application:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	cout &lt;&lt; "Continue Demo Application!\n";
	int i = 1;
	while (i &lt;= 100)
	{
		if (i % 5 != 0)
		{
			++i;
			continue;
		}
		cout &lt;&lt; i * i * i &lt;&lt; endl;
		++i;
	}

	cout &lt;&lt; "END" &lt;&lt; endl;
	return 0;
}
</pre>

&nbsp;