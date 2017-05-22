---
id: 39
title: 'C++ &#8211; Bài 4: Kiểu Dữ Liệu string trong C++'
date: 2016-09-23T12:54:01+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=39
permalink: /cpp-bai-4-kieu-du-lieu-string-trong-cpp/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/cpp-string.jpg
categories:
  - Lập Trình
  - Lập Trình C++
tags:
  - C++
  - C++ cơ bản
  - Học lập trình C++
---
<h2 style="text-align: center;">
  C++ &#8211; Bài 4: Kiểu Dữ Liệu string trong C++
</h2>

Tìm hiểu cơ bản về kiểu dữ liệu string trong C++.

Cung cấp kiến thức cơ bản nhất để thao tác với kiểu dữ liệu string như nhập, xuất, tính độ dài string.

Cùng với việc hiển thị các ký tự đặc biệt xuất hiện trong string.

<!--more-->

C++ Strings library: <a class=" yt-uix-servicelink " href="http://en.cppreference.com/w/cpp/string" target="_blank" rel="nofollow" data-servicelink="CDEQ6TgiEwjUxfOIw6XPAhVMN1gKHT-wBJgo-B0" data-url="http://en.cppreference.com/w/cpp/string">http://en.cppreference.com/w/cpp/string</a>
  
std::basic_string: <a class=" yt-uix-servicelink " href="http://en.cppreference.com/w/cpp/string/basic_string" target="_blank" rel="nofollow" data-servicelink="CDEQ6TgiEwjUxfOIw6XPAhVMN1gKHT-wBJgo-B0" data-url="http://en.cppreference.com/w/cpp/string/basic_string">http://en.cppreference.com/w/cpp/string/basic_string</a>
  
C++ Escape sequences: <a class=" yt-uix-servicelink " href="http://en.cppreference.com/w/cpp/language/escape" target="_blank" rel="nofollow" data-servicelink="CDEQ6TgiEwjUxfOIw6XPAhVMN1gKHT-wBJgo-B0" data-url="http://en.cppreference.com/w/cpp/language/escape">http://en.cppreference.com/w/cpp/language/escape</a>
  
std::getline: <a class=" yt-uix-servicelink " href="http://www.cplusplus.com/reference/string/string/getline/" target="_blank" rel="nofollow" data-servicelink="CDEQ6TgiEwjUxfOIw6XPAhVMN1gKHT-wBJgo-B0" data-url="http://www.cplusplus.com/reference/string/string/getline/">http://www.cplusplus.com/reference/string/string/getline/</a>
  
std::istream::ignore: <a class=" yt-uix-servicelink " href="http://www.cplusplus.com/reference/istream/istream/ignore/" target="_blank" rel="nofollow" data-servicelink="CDEQ6TgiEwjUxfOIw6XPAhVMN1gKHT-wBJgo-B0" data-url="http://www.cplusplus.com/reference/istream/istream/ignore/">http://www.cplusplus.com/reference/istream/istream/ignore/</a>
  


&nbsp;

<pre class="theme:vs2012-black lang:c++ decode:true " title="string basic">#include &lt;iostream&gt;
#include &lt;string&gt;

using namespace std;

int main()
{
	string name;
	string city;
	int age;
	cout &lt;&lt; "Nhap ten: ";
	getline(cin, name);
	cout &lt;&lt; "Nhap tuoi: ";
	cin &gt;&gt; age;
	std::cin.ignore();
	cout &lt;&lt; "Nhap thanh pho ban dang song: ";
	getline(cin, city);
	cout &lt;&lt; "Ban ten la: " &lt;&lt; name 
		&lt;&lt; "\nBan nam nay: " &lt;&lt; age &lt;&lt; " tuoi." 
		&lt;&lt; "\nBan dang song o: " &lt;&lt; city &lt;&lt; endl;

	return 0;
}</pre>

&nbsp;