---
id: 122
title: 'Bài 18: Các Thao Tác Xử Lý Với Mảng: Tìm Kiếm, Sắp Xếp trong C++'
date: 2016-11-06T10:52:29+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=122
permalink: /bai-18-cac-thao-tac-xu-ly-voi-mang-tim-kiem-sap-xep/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/11/cpp18.jpg
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
  Bài 18: Các Thao Tác Xử Lý Với Mảng: Tìm Kiếm, Sắp Xếp trong C++
</h2>

Trong bài này, chúng ta cùng xem xét các thao tác xử lý với mảng như duyệt mảng để tìm kiếm sự xuất hiện của một phần tử, hay đếm số lần xuất hiện, xóa phần tử cũng như thuật toán để sắp xếp các phần tử trong mảng.

<!--more-->

Thuật toán sắp xếp chèn &#8211; <a href="https://www.toptal.com/developers/sorting-algorithms/insertion-sort" target="_blank">Insertion Sort</a>.

Thuật toán sắp xếp nổi bọt &#8211; <a href="https://www.toptal.com/developers/sorting-algorithms/bubble-sort" target="_blank">Bubble Sort</a>.

Các thuật toán sắp xếp phổ biến minh họa bằng hình ảnh động &#8211; <a href="https://www.toptal.com/developers/sorting-algorithms/" target="_blank">Sorting Algorithms Animations</a>.
  


Code demo:

Tìm kiếm:

<pre class="brush:c++;">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const int spt = 50;
	double diemSo[spt];
	int n;
	do
	{
		cout &lt;&lt; "Nhap so phan tu muon nhap: (0 &lt; n &lt;= 50)";
		cin &gt;&gt; n;
	} while (n &lt; 0 || n &gt; 50);
	for (int i = 0; i &lt; n; ++i)
	{
		cout &lt;&lt; "Moi nhap diem cua sinh vien thu (" &lt;&lt; i &lt;&lt; "): ";
		cin &gt;&gt; diemSo[i];
	}
	
	cout &lt;&lt; "\nMoi ban nhap vao diem can tim: ";
	double diemCanTim;
	cin &gt;&gt; diemCanTim;

	bool tonTai = false;
	int count = 0;

	for (int i = 0; i &lt; n; ++i)
	{
		if (diemSo[i] == diemCanTim)
		{
			tonTai = true;
			count++;
		}
	}
	if (tonTai)
	{
		cout &lt;&lt; "Diem ban can tim co trong du lieu.\n";
		cout &lt;&lt; "Diem ban can tim xuat hien " &lt;&lt; count &lt;&lt; " lan.";
	}
	else
	{
		cout &lt;&lt; "Diem ban can tim khong co trong du lieu.";
	}

	cout &lt;&lt; endl;
	return 0;
}</pre>

Xóa phần tử ở vị trí nào đó.

<pre class="brush:c++;">#include &lt;iostream&gt;

using namespace std;

int main()
{
	const int spt = 50;
	double diemSo[spt];
	int n;
	do
	{
		cout &lt;&lt; "Nhap so phan tu muon nhap: (0 &lt; n &lt;= 50)";
		cin &gt;&gt; n;
	} while (n &lt; 0 || n &gt; 50);
	for (int i = 0; i &lt; n; ++i)
	{
		cout &lt;&lt; "Moi nhap diem cua sinh vien thu (" &lt;&lt; i &lt;&lt; "): ";
		cin &gt;&gt; diemSo[i];
	}
	int vtriCanXoa;
	do
	{
		cout &lt;&lt; "\nMoi ban nhap vao vi tri can xoa: ";
		cin &gt;&gt; vtriCanXoa;

	} while (vtriCanXoa &gt;= n || vtriCanXoa &lt; 0);

	for (int i = vtriCanXoa; i &lt; n - 1; ++i)
	{
		diemSo[i] = diemSo[i + 1];
	}
	n--;
	for (int i = 0; i &lt; n; ++i)
	{
		cout &lt;&lt; diemSo[i] &lt;&lt; " ";
	}
	cout &lt;&lt; endl;
	return 0;
}</pre>

Sắp xếp: cài đặt thuật toán sắp xếp chèn &#8211; Selection Sort.

<pre class="brush:c++;">#include &lt;iostream&gt;

using namespace std;

void insertionSort(int[], int);

int main()
{
	int iArr[] = { 15, 4, 6, 2, 20 };
	int spt = 5;

	cout &lt;&lt; "Mang truoc khi sap xep:\n";
	for (int in : iArr)
	{
		cout &lt;&lt; in &lt;&lt; " ";
	}
	cout &lt;&lt; endl;

	insertionSort(iArr, spt);

	cout &lt;&lt; "Mang sau khi sap xep:\n";
	for (int in : iArr)
	{
		cout &lt;&lt; in &lt;&lt; " ";
	}
	cout &lt;&lt; endl;

	return 0;
}

void insertionSort(int arr[], int n)
{
	for (int i = 1; i &lt; n; ++i)
	{
		for (int k = i; k &gt; 0 && arr[k] &lt; arr[k - 1]; --k)
		{
			int temp = arr[k];
			arr[k] = arr[k - 1];
			arr[k - 1] = temp;
		}
	}
}</pre>

Happy coding!