---
id: 86
title: 'C++ Bài 11: Ôn Tập Các Cấu Trúc Điều Khiển trong C++'
date: 2016-10-08T21:42:39+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=86
permalink: /cpp-bai-11-on-tap-cac-cau-truc-dieu-khien/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/10/cpp11.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 class="watch-title-container" style="text-align: center;">
  <span id="eow-title" class="watch-title watch-editable" dir="ltr" title="C++ Bài 11: Ôn Tập Các Cấu Trúc Điều Khiển trong C++ [HD]">C++ Bài 11: Ôn Tập Các Cấu Trúc Điều Khiển trong C++</span>
</h2>

Bài học này sẽ giải quyết một số ví dụ để các bạn ôn tập lại kiến thức về các cấu trúc điều khiển như if-else, for, while loop.

<!--more-->



Code:

Giải phương trình bậc 2: <a href="https://vi.wikipedia.org/wiki/Ph%C6%B0%C6%A1ng_tr%C3%ACnh_b%E1%BA%ADc_hai" target="_blank">https://vi.wikipedia.org/wiki/Ph%C6%B0%C6%A1ng_tr%C3%ACnh_b%E1%BA%ADc_hai</a>

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;
#include &lt;cmath&gt;

using namespace std;

int main()
{
	cout &lt;&lt; "Chuong trinh giai phuong trinh bac 2!\n";
	double a, b, c;
	cout &lt;&lt; "Nhap vao gia tri cac hang so: a, b, c ";
	cin &gt;&gt; a &gt;&gt; b &gt;&gt; c;

	if (a == 0)
	{
		if (b == 0)
		{
			if (c == 0)
			{
				cout &lt;&lt; "Phuong trinh co vo so nghiem.\n";
			}
			else
			{
				cout &lt;&lt; "Phuong trinh vo nghiem.\n";
			}
		}
		else
		{
			cout &lt;&lt; "Phuong trinh co nghiem: " &lt;&lt; (-c / b);
		}
	}
	else
	{
		double delta = b * b - (4 * a * c);
		if (delta &lt; 0)
		{
			cout &lt;&lt; "Phuong trinh vo nghiem.\n";
		}
		else if (delta == 0)
		{
			cout &lt;&lt; "Phuong trinh co nghiem kep: " &lt;&lt; (-b / (2 * a));
		}
		else
		{
			double nghiem1 = (-b - sqrt(delta)) / (2 * a);
			double nghiem2 = (-b + sqrt(delta)) / (2 * a);
			cout &lt;&lt; "Phuong trinh co nghiem: " &lt;&lt; nghiem1 &lt;&lt; endl;
			cout &lt;&lt; "Phuong trinh co nghiem: " &lt;&lt; nghiem2 &lt;&lt; endl;
		}
		cout &lt;&lt; endl;
	}

	return 0;
}</pre>

Tìm số thứ N trong dãy Fibonaci:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	cout &lt;&lt; "Nhap vao so can tinh: ";
	int n;
	cin &gt;&gt; n;
	cout &lt;&lt; "So trong day Fib: ";
	if (n == 1 || n == 2)
	{
		cout &lt;&lt; 1;
	}
	else 
	{
		int fibn = 1;
		int fibp = 1;
		int i = 3;
		while (i &lt;= n)
		{
			int temp = fibn;
			fibn += fibp;
			fibp = temp;
			++i;
		}
		cout &lt;&lt; fibn;
	}
	cout &lt;&lt; endl;

	return 0;
}</pre>

Tính tổng dãy liên tục:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	cout &lt;&lt; "Nhap vao so can tinh: ";
	int n;
	cin &gt;&gt; n;
	long sum = 0;
	for (int i = 1; i &lt;= n; ++i)
	{
		sum += i;
	}

	cout &lt;&lt; "Ket qua = " &lt;&lt; sum;

	cout &lt;&lt; endl;

	return 0;
}</pre>

Tính tổng dãy có sử dụng vòng lặp lồng nhau:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	cout &lt;&lt; "Nhap vao so can tinh: ";
	int n;
	cin &gt;&gt; n;
	double sum = 0.0;
	for (int i = 1; i &lt;= n; ++i)
	{
		double gt = 1.0;
		for (int j = 2; j &lt;= i; ++j)
		{
			gt *= j;
		}
		double giaTri = 1.0 / gt;
		sum += giaTri;
	}

	cout &lt;&lt; "Ket qua = " &lt;&lt; sum;

	cout &lt;&lt; endl;

	return 0;
}</pre>

&nbsp;

&nbsp;