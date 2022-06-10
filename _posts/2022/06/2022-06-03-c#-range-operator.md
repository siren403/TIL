---
title: C# Range
categories:
  - Blog
tags:
  - c#
---

[범위 연산자](https://docs.microsoft.com/ko-kr/dotnet/csharp/language-reference/proposals/csharp-8.0/ranges)
---

[**tutorials**](https://docs.microsoft.com/ko-kr/dotnet/csharp/whats-new/tutorials/ranges-indexes)

c# 8.0에 추가된 연산자.

python의 [Extended Slices](https://docs.python.org/release/2.3.5/whatsnew/section-slices.html) 비슷하게 배열을 다룰 수 있음

```csharp
var arr = new []{
    1, 2, 3, 4, 5
};

int last = arr[^1];

var all = arr[0..all.Length];
var all = arr[0..^0];

var empty = arr[1..1];
var empty = arr[0..^5];

var second = arr[1..2]; // [2]

var fromLast = arr[^2..^0]; // [4, 5]
```

