---
id: 115
title: 'Bài 17: Mảng Ký Tự, C-String, Con Trỏ vs Mảng, Truyền Mảng Cho Hàm trong C++'
date: 2016-11-05T17:01:53+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=115
permalink: /bai-17-mang-ky-tu-c-string-con-tro-vs-mang-truyen-mang-trong-cpp/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/11/cpp17.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - C++ mảng
  - c++ pointer
  - Học lập trình C++
---
<h2 style="text-align: center;">
  Bài 17: Mảng Ký Tự, C-String, Con Trỏ vs Mảng, Truyền Mảng Cho Hàm trong C++
</h2>

Trong bài này, chúng ta cùng tìm hiểu các phần tiếp theo về mảng như: mảng ký tự, C-String vs String, con trỏ vs mảng và làm thế nào để truyền mảng vào cho hàm trong C++.

Ngoài ra còn các lưu ý khi sử dụng.

<!--more-->


  

  
Code demo:

<pre class="brush:c++;">#include &lt;iostream&gt;
#include &lt;cstring&gt;
#include &lt;string&gt;

using namespace std;

void printArray(int [], int);
void printArrayPtr(int *, int);

int main()
{
	//char message[] = {'H', 'e', 'l', 'l', 'o', 0};
	char message[] = "Hello";
	int length = 0;
	for (char c : message)
	{
		length++;
		cout &lt;&lt; c;
	}
	cout &lt;&lt; endl;
	cout &lt;&lt; strlen(message) &lt;&lt; endl;
	cout &lt;&lt; length &lt;&lt; endl;

	string str = "Hello";
	length = 0;
	for (char c : str)
	{
		length++;
		cout &lt;&lt; c;
	}
	cout &lt;&lt; endl;
	cout &lt;&lt; str.length() &lt;&lt; endl;
	cout &lt;&lt; length &lt;&lt; endl;

	char *cptr = message;
	int max = strlen(message);
	for (int i = 0; i &lt; max; ++i)
	{
		cout &lt;&lt; *(cptr + i);
	}
	cout &lt;&lt; endl;

	int iarr[] = { 34, 324, 345, 6, 78, 90 };
	int *iPtr = iarr;
	for (int i = 0; i &lt; 6; ++i)
	{
		cout &lt;&lt; *(iPtr + i) &lt;&lt; " ";
	}

	cout &lt;&lt; endl;
	//printArray(iarr, 6);
	printArray(iarr, 6);
	cout &lt;&lt; endl;
	printArrayPtr(iarr, 6);

	cout &lt;&lt; endl;
	return 0;
}

void printArray(int arr[], int n)
{
	for (int i = 0; i &lt; n; ++i)
	{
		arr[i] *= 2;
		cout &lt;&lt; arr[i] &lt;&lt; " ";
	}
}

void printArrayPtr(int *arr, int n)
{
	for (int i = 0; i &lt; n; ++i)
	{
		cout &lt;&lt; arr[i] &lt;&lt; " ";
	}
}</pre>

&nbsp;