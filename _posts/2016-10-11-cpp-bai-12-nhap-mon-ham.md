---
id: 89
title: 'C++ Bài 12: Nhập Môn Hàm trong C++'
date: 2016-10-11T16:20:15+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=89
permalink: /cpp-bai-12-nhap-mon-ham/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/10/cpp12.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - hàm
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ Bài 12: Nhập Môn Hàm trong C++
</h2>

Trong bài này, mình sẽ giới thiệu cơ bản về hàm hay function trong C++ thông qua các ví dụ đơn giản. Từ đó giúp các bạn tiếp cận các lý thuyết về hàm.

<!--more-->

Tham khảo về hàm: <a href="http://en.cppreference.com/w/cpp/language/functions" target="_blank">http://en.cppreference.com/w/cpp/language/functions</a>


  
Code:

Car Builder:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

void inBanhXe()
{
	cout &lt;&lt; "Toi lam banh xe o day.\n";
}

void inDongCo()
{
	cout &lt;&lt; "Toi in dong co o day.\n";
}

void inKhungXe()
{
	cout &lt;&lt; "In khung xe + son xe.\n";
}

int main()
{
	cout &lt;&lt; "Chuong trinh in ra Oto.\n";
	inBanhXe();
	inDongCo();
	inKhungXe();
	cout &lt;&lt; "Da hoan thien Oto.\n";
	return 0;
}</pre>

Tính chênh lệch tiền lương:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;
#include &lt;cmath&gt;

using namespace std;

int tinhTongTien(int soGio, int ltime)
{
	int tongTien = 0;
	if (soGio &gt; 25)
	{
		tongTien = ltime * 1.2 * soGio;
	}
	else
	{
		tongTien = ltime * soGio;
	}
	return tongTien;
}

int main()
{
	cout &lt;&lt; "Chuong trinh tinh luong.\n";
	const int ltg = 150000;
	int soGio1 = 20;
	int soGio2 = 30;

	int tongTien1 = tinhTongTien(soGio1, ltg);
	int tongTien2 = tinhTongTien(soGio2, ltg);
	int tongTien3 = tinhTongTien(30.5, ltg);
	cout &lt;&lt; tongTien1 &lt;&lt; " " &lt;&lt; tongTien2 &lt;&lt; " " &lt;&lt; tongTien3 &lt;&lt; endl;

	cout &lt;&lt; "Chenh lech tien giua 2 nhan vien la: " &lt;&lt; abs(tongTien1 - tongTien2) &lt;&lt; endl;
	
	return 0;
}

</pre>

&nbsp;