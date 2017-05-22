---
id: 65
title: 'C++ &#8211; Bài 7: Đưa Ra Quyết Định với Cấu Trúc If-Else trong C++'
date: 2016-09-24T11:55:27+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=65
permalink: /cpp-bai-7-dua-ra-quyet-dinh-cau-truc-if-else-trong-cpp/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/cpp7.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ &#8211; Bài 7: Đưa Ra Quyết Định với Cấu Trúc If-Else trong C++
</h2>

Trong bài này, chúng ta cùng tìm hiểu cấu trúc if-else trong C++ để lựa chọn, đưa ra quyết định dựa vào một điều kiện đầu vào.

Cùng với đó là các bẫy khi thực hiện tính toán biểu thức logic.

<!--more-->

Video hướng dẫn:
  

  
Game đoán tuổi của Hà Nội.

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const int TUOI_HA_NOI = 1000;
	int soTuoiCuaHaNoi = 0;

	cout &lt;&lt; "Nhap vao tuoi cua Ha noi: ";
	cin &gt;&gt; soTuoiCuaHaNoi;

	if (soTuoiCuaHaNoi == TUOI_HA_NOI)
	{
		cout &lt;&lt; "Chuc mung ban da thang tro choi!\n";
	}
	else
	{
		cout &lt;&lt; "Chuc ban may man lan sau.\n";
	}
	
	cout &lt;&lt; endl;

	return 0;
}</pre>

&nbsp;

Chương trình chuyển đổi điểm hệ 10 sang hệ chữ.

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const double DIEM_A = 8.5;
	const double DIEM_B = 7.0;
	const double DIEM_C = 5.5;
	const double DIEM_D = 4.0;

	double diem = 0.0;

	cout &lt;&lt; "Moi ban nhap vao diem he 10: ";
	cin &gt;&gt; diem;
	if (diem &gt;= DIEM_A)
	{
		cout &lt;&lt; "Chuc mung ban da duoc diem A.";
	}
	else if (diem &gt;= DIEM_B)
	{
		cout &lt;&lt; "Chuc mung ban da duoc diem B.";
	}
	else if (diem &gt;= DIEM_C)
	{
		cout &lt;&lt; "Ban da duoc diem C.";
	}
	else if (diem &gt;= DIEM_D)
	{
		cout &lt;&lt; "Ban da duoc diem D.";
	}
	else
	{
		cout &lt;&lt; "Ban da duoc diem F.";
	}

	cout &lt;&lt; endl;

	return 0;
}</pre>

&nbsp;

&nbsp;