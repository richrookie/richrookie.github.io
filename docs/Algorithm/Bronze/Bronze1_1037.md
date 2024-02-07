---
layout: default
title: "[백준] C# : 약수 (1037번)"
parent: Bronze
grand_parent: Algorithm
nav_order: 2
permalink: /docs/Algorithm/Bronze/Bronze1_1037/
---

## 문 제

> 양수 A가 N의 진짜 약수가 되려면, N이 A의 배수이고, A가 1과 N이 아니어야 한다. 어떤 수 N의 진짜 약수가 모두 주어질 때, N을 구하는 프로그램을 작성하시오.

## 입 력

> 첫째 줄에 N의 진짜 약수의 개수가 주어진다. 이 개수는 50보다 작거나 같은 자연수이다. 둘째 줄에는 N의 진짜 약수가 주어진다. 1,000,000보다 작거나 같고, 2보다 크거나 같은 자연수이고, 중복되지 않는다.

```yaml
2
4 2
```

```yaml
1
2
```

```yaml
6
3 4 2 12 6 8
```

```yaml
14
14 26456 2 28 13228 3307 7 23149 8 6614 46298 56 4 92596
```

## 출 력

> 첫째 줄에 패턴을 출력하면 된다.

```yaml
8
```

```yaml
4
```

```yaml
24
```

```yaml
185192
```

## 코 드

- 두 번째 입력란에 N의 약수들이 주어진다. 두 가지 경우를 생각하면 쉽게 풀 수 있는 문제!

1. 경우-1 : 입력이 하나일 때, 제곱한 값이 정답. 왜? 소수인 숫자일 경우 문제에서 양수 A(입력값)가 1과 N이 아니어야 한다고 하였기 때문!

1. 경우-2 : 입력이 하나 이상일 때, 입력갑셍서 '최소 x 최대' 한 값이 정답!

<div class="code-example" markdown="1">

```csharp
using static System.Console;
using System.Linq;
using System;

namespace Algorithm
{
    class Program
    {
        static void Main(string[] args)
        {
            int count = int.Parse(ReadLine());

            int[] input = ReadLine().Split(' ').Select(int.Parse).ToArray();
            Array.Sort(input);
            int answer = 0;

            if(input.Length == 1)
                answer = input[0] * input[0];
            else
                answer = input[count - 1] * input[0];

            WriteLine(answer);
        }
    }
}

```

</div>
```
