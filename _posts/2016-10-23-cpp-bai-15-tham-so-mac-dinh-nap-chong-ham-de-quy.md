---
id: 102
title: 'C++ Bài 15: Tham Số Mặc Định, Nạp Chồng Hàm, Đệ Quy trong C++'
date: 2016-10-23T09:57:41+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=102
permalink: /cpp-bai-15-tham-so-mac-dinh-nap-chong-ham-de-quy/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/10/cpp15.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - default parameters
  - hàm
  - Học lập trình C++
  - overload
  - recusive
---
<h2 style="text-align: center;">
  C++ Bài 15: Tham Số Mặc Định, Nạp Chồng Hàm, Đệ Quy trong C++
</h2>

Trong bài này, chúng ta cùng tìm hiểu về tham số mặc định, nạp chồng hàm và đệ quy trong C++ qua các ví dụ đơn giản cùng với các lưu ý khi sử dụng chúng.

<!--more-->

Nạp chồng hàm: <a href="http://en.cppreference.com/w/cpp/language/overload_resolution" target="_blank">http://en.cppreference.com/w/cpp/language/overload_resolution</a>
  

  
Code ví dụ:

Tham số mặc định:

<pre class="theme:solarized-dark toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

using namespace std;

double tinhLuong(int, int = 150, int = 40);

int main()
{
	cout &lt;&lt; tinhLuong(50, 100) &lt;&lt; endl;
	cout &lt;&lt; tinhLuong(30, 100) &lt;&lt; endl;
	return 0;
}

double tinhLuong(int soGio, int ltg, int tongTuan)
{
	if (soGio &gt;= tongTuan)
	{
		return soGio * ltg * 1.2;
	}
	else
	{
		return soGio * ltg;
	}
}
</pre>

Nạp chồng hàm:

<pre class="theme:solarized-dark toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int square(int);
double square(double);
void print(int);
void print(int, double);

int main()
{
	cout &lt;&lt; "5.2^2 = " &lt;&lt; square(5.2) &lt;&lt; endl;
	print(1);
	print(2, 2.5);
	return 0;
}

int square(int number)
{
	return number * number;
}

double square(double number)
{
	return number * number;
}

void print(int a)
{
	cout &lt;&lt; "print(int a): " &lt;&lt; a &lt;&lt; endl;
}

void print(int a, double d)
{
	cout &lt;&lt; "print(int a, double d): " &lt;&lt; a &lt;&lt; " " &lt;&lt; d &lt;&lt; endl;
}</pre>

Đệ quy tính giai thừa:

<pre class="theme:solarized-dark toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int tinhGT(int);

int main()
{
	cout &lt;&lt; "6! = " &lt;&lt; tinhGT(6) &lt;&lt; endl;
	return 0;
}

int tinhGT(int n)
{
	cout &lt;&lt; "Tinh giai thua: " &lt;&lt; n &lt;&lt; endl;
	if (n &lt;= 1)
	{
		return 1;
	}
	else
	{
		return n * tinhGT(n - 1);
	}
}
</pre>

&nbsp;