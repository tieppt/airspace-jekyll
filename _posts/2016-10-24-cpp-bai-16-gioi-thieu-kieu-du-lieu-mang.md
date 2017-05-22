---
id: 106
title: 'C++ Bài 16: Giới Thiệu Kiểu Dữ Liệu Mảng trong C++'
date: 2016-10-24T15:57:54+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=106
permalink: /cpp-bai-16-gioi-thieu-kieu-du-lieu-mang/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/10/cpp16.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - C++ mảng
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ Bài 16: Giới Thiệu Kiểu Dữ Liệu Mảng trong C++
</h2>

Trong bài này chúng ta cùng tìm hiểu cơ bản về kiểu dữ liệu mảng trong C++, các thao tác cơ bản khi thực hiện với mảng như khai báo, khởi tạo, duyệt mảng, &#8230;
  
<!--more-->


  
Tham khảo về mảng: <a href="http://www.cplusplus.com/doc/tutorial/arrays/" target="_blank">http://www.cplusplus.com/doc/tutorial/arrays/</a>



Code:

<pre class="lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	int dsTienThuong[5] = {100, 500, 600, 300, 800};

	for (int index = 0; index &lt; 5; ++index)
	{
		cout &lt;&lt; "Thang nay ban nhan duoc: " &lt;&lt; dsTienThuong[index] &lt;&lt; endl;
	}

	cout &lt;&lt; "\nSo tien thuong cua ban sau khi nhan doi nhan duoc:\n";
	int index = 0;
	while (index &lt; 5)
	{
		cout &lt;&lt; "Thang nay ban nhan duoc: " &lt;&lt; dsTienThuong[index] * 2 &lt;&lt; endl;
		++index;
	}

	cout &lt;&lt; "\nSo tien thuong cua ban sau khi nhan 3 nhan duoc:\n";
	for (int thuong : dsTienThuong)
	{
		cout &lt;&lt; "Thang nay ban nhan duoc: " &lt;&lt; thuong * 3 &lt;&lt; endl;
	}
	return 0;
}</pre>

Nhập xuất dữ liệu với mảng:

<pre class="lang:c++ decode:true ">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const int SLPT = 20;
	int dsTienThuong[SLPT];
	int number = 0;

	do
	{
		cout &lt;&lt; "Moi nhap so luong phan tu ban muon nhap: ";
		cin &gt;&gt; number;
	} while (number &lt; 1 || number &gt; 20);
	
	for (int i = 0; i &lt; number; ++i)
	{
		cout &lt;&lt; "Moi nhap vao tien thuong cua nguoi thu: #" &lt;&lt; i + 1 &lt;&lt; " ";
		cin &gt;&gt; dsTienThuong[i];
	}

	int index = 0;
	while (index &lt; number)
	{
		cout &lt;&lt; "Nguoi thu #" &lt;&lt; index + 1 &lt;&lt; " duoc thuong: " &lt;&lt; dsTienThuong[index] &lt;&lt; endl;
		index++;
	}
	
	return 0;
}</pre>

&nbsp;

&nbsp;