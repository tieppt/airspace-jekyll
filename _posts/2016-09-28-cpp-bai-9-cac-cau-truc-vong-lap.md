---
id: 76
title: 'C++ &#8211; Bài 9: Các Cấu Trúc Vòng Lặp trong C++'
date: 2016-09-28T18:28:34+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=76
permalink: /cpp-bai-9-cac-cau-truc-vong-lap/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/cpp9.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ &#8211; Bài 9: Các Cấu Trúc Vòng Lặp trong C++
</h2>

Trong bài này, mình giới thiệu cho các bạn các cấu trúc vòng lặp trong C++ để thực hiện việc lặp đi lặp lại một số công việc hay hành động nào đó.

<!--more-->

while loop: <a href="http://en.cppreference.com/w/cpp/language/while" target="_blank">http://en.cppreference.com/w/cpp/language/while</a>

for loop: <a href="http://en.cppreference.com/w/cpp/language/for" target="_blank">http://en.cppreference.com/w/cpp/language/for</a>

do-while loop: <a href="http://en.cppreference.com/w/cpp/language/do" target="_blank">http://en.cppreference.com/w/cpp/language/do</a>

Range-based for loop (since C++11): <a href="http://en.cppreference.com/w/cpp/language/range-for" target="_blank">http://en.cppreference.com/w/cpp/language/range-for</a>
  

  
Code:

Ví dụ với while:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

using namespace std;

int main()
{
	int siSo = 0;
	cout &lt;&lt; "Hay cho biet so sinh vien cua lop: ";
	cin &gt;&gt; siSo;
	int soThe = 1;
	while (soThe &gt; siSo);
	{
		cout &lt;&lt; "Sinh vien thu: " &lt;&lt; soThe &lt;&lt; endl;
		++soThe;
	}

	return 0;
}</pre>

Ví dụ việc kiểm tra đầu vào người dùng nhập vào:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const double DIEM_A = 8.5;
	const double DIEM_B = 7.0;
	const double DIEM_C = 5.5;
	const double DIEM_D = 4.0;
	const double DIEM_MIN = 0.0;
	const double DIEM_MAX = 10.0;

	double diem = 0.0;

	cout &lt;&lt; "Moi ban nhap vao diem he 10: ";
	cin &gt;&gt; diem;

	while (!(DIEM_MIN &lt;= diem && diem &lt;= DIEM_MAX))
	{
		cout &lt;&lt; "Ban da nhap sai diem.\n";
		cout &lt;&lt; "Moi ban nhap vao diem he 10: ";
		cin &gt;&gt; diem;
	}
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

Ví dụ với for:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

using namespace std;

int main()
{
	int siSo = 0;
	cout &lt;&lt; "Hay cho biet so sinh vien cua lop: ";
	cin &gt;&gt; siSo;
	
	for (int soThe = 1; soThe &lt;= siSo; ++soThe)
	{
		cout &lt;&lt; "Sinh vien thu: " &lt;&lt; soThe &lt;&lt; endl;
	}

	return 0;
}</pre>

Ví dụ với do-while để kiểm tra nhập vào:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const double DIEM_A = 8.5;
	const double DIEM_B = 7.0;
	const double DIEM_C = 5.5;
	const double DIEM_D = 4.0;
	const double DIEM_MIN = 0.0;
	const double DIEM_MAX = 10.0;

	double diem = 0.0;
	bool valid = false;
	do
	{
		cout &lt;&lt; "Moi ban nhap vao diem he 10: ";
		cin &gt;&gt; diem;
		valid = (DIEM_MIN &lt;= diem && diem &lt;= DIEM_MAX);
		if (!valid)
		{
			cout &lt;&lt; "Ban da nhap sai diem.\n";
		}
	} while (!valid);

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

Ví dụ việc tính tổng với vòng lặp do-while:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	double sum = 0.0;
	double so = 0.0;
	do
	{
		cout &lt;&lt; "Nhap vao so: ";
		cin &gt;&gt; so;
		sum += so;
	} while (so != 0.0);

	cout &lt;&lt; "Sum = " &lt;&lt; sum &lt;&lt; endl;

	return 0;
}</pre>

Ví dụ Range-based for:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	string str = "Lap Trinh Vi Dieu";

	for (auto value : str)
	{
		cout &lt;&lt; value &lt;&lt; " ";
	}

	cout &lt;&lt; endl;

	double mang[]{ 1,2,3,4,5,6 };

	for (auto number: mang)
	{
		cout &lt;&lt; number &lt;&lt; "^2 = " &lt;&lt; number * number &lt;&lt; endl;
	}

	return 0;
}</pre>

&nbsp;