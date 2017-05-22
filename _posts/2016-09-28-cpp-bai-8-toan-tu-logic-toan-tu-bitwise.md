---
id: 69
title: 'C++ Bài 8: Toán Tử Logic và Toán Tử Bitwise trong C++'
date: 2016-09-28T03:22:30+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=69
permalink: /cpp-bai-8-toan-tu-logic-toan-tu-bitwise/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/cpp8.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ Bài 8: Toán Tử Logic và Toán Tử Bitwise trong C++
</h2>

Trong video này, mình giới thiệu hai toán tử tiếp theo là toán tử logic và toán tử bitwise cùng với một số ví dụ cơ bản.
  
Và một vài lưu ý về thứ tự thực hiện các phép toán trong một chương trình C++.

<!--more-->

Link tham khảo:
  
Logical operators: <a href="http://en.cppreference.com/w/cpp/language/operator_logical" target="_blank">http://en.cppreference.com/w/cpp/language/operator_logical</a>

Bitwise operators: <a href="http://en.cppreference.com/w/cpp/language/operator_arithmetic#Bitwise_logic_operators" target="_blank">http://en.cppreference.com/w/cpp/language/operator_arithmetic#Bitwise_logic_operators</a>

Thứ tự thực hiện các phép toán: <a href="http://en.cppreference.com/w/cpp/language/operator_precedence" target="_blank">http://en.cppreference.com/w/cpp/language/operator_precedence</a>
  


Ví dụ với toán tử logic trong câu lệnh if-else:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

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

	if (0 &lt;= diem && diem &lt;= 10)
	{
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
	}
	else
	{
		cout &lt;&lt; "Ban da nhap sai diem.";
	}
	
	cout &lt;&lt; endl &lt;&lt; diem;
	cout &lt;&lt; endl;

	return 0;
}</pre>

Ví dụ phân quyền với toán tử bitwise:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const unsigned short VIEW = 1;
	const unsigned short POST = 2;
	const unsigned short ADMIN = 4;
	cout &lt;&lt; "Moi ban nhap vao quyen: ";
	unsigned short perm;
	cin &gt;&gt; perm;
	if ((perm & ADMIN))
	{
		cout &lt;&lt; "Ban co quyen ADMIN\n";
	}
	if ((perm & POST))
	{
		cout &lt;&lt; "Ban co quyen POST\n";
	}
	if ((perm & VIEW))
	{
		cout &lt;&lt; "Ban co quyen VIEW\n";
	}

	return 0;
}</pre>

&nbsp;