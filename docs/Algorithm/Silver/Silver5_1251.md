---
layout: default
title: "[백준] C# : 단어 나누기 (1251번)"
parent: Silver
grand_parent: Algorithm
nav_order: 4
permalink: /docs/Algorithm/Bronze/Silver_1251/
---

> [Try Again]

## 문 제

> 알파벳 소문자로 이루어진 단어를 가지고 아래와 같은 과정을 해 보려고 한다.
>
> 먼저 단어에서 임의의 두 부분을 골라서 단어를 쪼갠다. 즉, 주어진 단어를 세 개의 더 작은 단어로 나누는 것이다. 각각은 적어도 길이가 1 이상인 단어여야 한다. 이제 이렇게 나눈 세 개의 작은 단어들을 앞뒤를 뒤집고, 이를 다시 원래의 순서대로 합친다.
>
> 예를 들어,

> - 단어 : arrested
> - 세 단어로 나누기 : ar / rest / ed
> - 각각 뒤집기 : ra / tser / de
> - 합치기 : ratserde
>   단어가 주어지면, 이렇게 만들 수 있는 단어 중에서 사전순으로 가장 앞서는 단어를 출력하는 프로그램을 작성하시오.

## 입 력

> 첫째 줄에 영어 소문자로 된 단어가 주어진다. 길이는 3 이상 50 이하이다.

```yaml
mobitel
```

## 출 력

> 첫째 줄에 구하고자 하는 단어를 출력하면 된다.

```yaml
bometil
```

## 코 드

- 모든 경우의 수를 조합하여 리스트에 넣고, 정렬하여 리스트의 첫 번째 항목을 출력!

<div class="code-example" markdown="1">

```csharp
using static System.Console;
using System.Collections.Generic;
using System;

namespace Algorithm
{
    class Program
    {
        static void Main(string[] args)
        {
            string input = ReadLine();

            int len = input.Length;
            int left = 1;
            int right = 2;

            List<string> strList = new List<string>();

            while(true)
            {
                char[] c1 = input[..left].ToArray();
                Array.Reverse(c1);
                char[] c2 = input[left..right].ToArray();
                Array.Reverse(c2);
                char[] c3 = input[right..len].ToArray();
                Array.Reverse(c3);

                strList.Add(new string(c1) + new string(c2) + new string(c3));

                right++;

                if(right >= len)
                {
                    left += 1;
                    right = left + 1;

                    if(right >= len)
                        break;
                }
            }

            strList.Sort();

            WriteLine(strList[0]);
        }
    }
}
```

</div>

## 비교코드 - 1

<div class="code-example" markdown="1">

```csharp

```

</div>

## 공 부
