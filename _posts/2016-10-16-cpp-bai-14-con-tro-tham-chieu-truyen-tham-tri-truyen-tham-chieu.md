---
id: 98
title: 'C++ Bài 14: Con Trỏ, Tham Chiếu, Truyền Tham Trị, Truyền Tham Chiếu Cho Hàm'
date: 2016-10-16T17:32:58+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=98
permalink: /cpp-bai-14-con-tro-tham-chieu-truyen-tham-tri-truyen-tham-chieu/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/10/cpp14.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - c++ pointer
  - c++ reference
  - hàm
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ Bài 14: Con Trỏ, Tham Chiếu, Truyền Tham Trị, Truyền Tham Chiếu Cho Hàm
</h2>

Trong bài này, mình giới thiệu cơ bản về quản lý bộ nhớ trong máy tính, về kiểu dữ liệu con trỏ, tham chiếu, truyền dữ liệu vào hàm theo tham trị hoặc tham chiếu thông qua các ví dụ đơn giản.

<!--more-->

Quản lý bộ nhớ trong máy tính (phần W8, W9): <a href="http://www.tenouk.com/ModuleW.html" target="_blank">http://www.tenouk.com/ModuleW.html</a>

Con trỏ: <a href="http://en.cppreference.com/w/cpp/language/pointer" target="_blank">http://en.cppreference.com/w/cpp/language/pointer</a>

Con trỏ tutorial: <a href="http://www.cplusplus.com/doc/tutorial/pointers/" target="_blank">http://www.cplusplus.com/doc/tutorial/pointers/</a>

Pointers, References and Dynamic Memory Allocation: <a href="https://www.ntu.edu.sg/home/ehchua/programming/cpp/cp4_PointerReference.html" target="_blank">ntu.edu.sg</a>
  


Code ví dụ:

Pointer:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	int a = 5;
	cout &lt;&lt; &a &lt;&lt; endl;
	int *ptrA = &a;
	cout &lt;&lt; ptrA &lt;&lt; endl;
	cout &lt;&lt; (*ptrA) &lt;&lt; endl;
	*ptrA = 50;
	const int * ptrB = ptrA;
	int b = 20;
	ptrB = &b;

	cout &lt;&lt; a &lt;&lt; " " &lt;&lt; *ptrA &lt;&lt; endl;
	cout &lt;&lt; b &lt;&lt; " " &lt;&lt; *ptrB &lt;&lt; " " &lt;&lt; ptrB &lt;&lt; endl;

	//int *ptrC = 0;
	//int *ptrC = NULL;
	int *ptrC = nullptr;
	ptrC = &b;
	cout &lt;&lt; *ptrC &lt;&lt; endl;

	ptrC = ptrA;
	cout &lt;&lt; *ptrC &lt;&lt; endl;

	return 0;
}</pre>

Reference:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	int a = 5;
	int &nA = a;
	cout &lt;&lt; a &lt;&lt; " " &lt;&lt; nA &lt;&lt; endl;
	nA *= 2;
	cout &lt;&lt; a &lt;&lt; " " &lt;&lt; nA &lt;&lt; endl;
	int b = 15;
	nA = b;
	cout &lt;&lt; a &lt;&lt; " " &lt;&lt; nA &lt;&lt; endl;
	nA *= 2;
	cout &lt;&lt; a &lt;&lt; " " &lt;&lt; nA &lt;&lt; endl;
	cout &lt;&lt; b &lt;&lt; endl;

	return 0;
}</pre>

Pass-by-value and pass-by-references:

<pre class="theme:vs2012-black toolbar:1 lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

void doubleNumber(int *);
void doubleNumberRef(int &);
int modifyWConst(const int &);

int main()
{
	int a = 5;
	cout &lt;&lt; a &lt;&lt; endl;
	//doubleNumber(&a);
	doubleNumberRef(a);
	int kq = modifyWConst(a);
	cout &lt;&lt; a &lt;&lt; endl;
	cout &lt;&lt; kq &lt;&lt; endl;

	return 0;
}

void doubleNumber(int *number)
{
	(*number) *= 2;
	cout &lt;&lt; "Trong ham doubleNumber: " &lt;&lt; (*number) &lt;&lt; endl;
}

void doubleNumberRef(int &n)
{
	n *= 2;
	cout &lt;&lt; "Trong ham doubleNumberRef: " &lt;&lt; n &lt;&lt; endl;
}

int modifyWConst(const int &m)
{
	return m * 10;
}</pre>

&nbsp;

&nbsp;