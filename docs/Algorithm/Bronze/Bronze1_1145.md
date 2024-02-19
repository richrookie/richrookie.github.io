---
layout: default
title: "[백준] C# : 적어도 대부분의 배수 (1145번)"
parent: Bronze
grand_parent: Algorithm
nav_order: 4
permalink: /docs/Algorithm/Bronze/Bronze1_1145/
---

## 문 제

> 다섯 개의 자연수가 있다. 이 수의 적어도 대부분의 배수는 위의 수 중 적어도 세 개로 나누어 지는 가장 작은 자연수이다.
>
> 서로 다른 다섯 개의 자연수가 주어질 때, 적어도 대부분의 배수를 출력하는 프로그램을 작성하시오.

## 입 력

> 첫째 줄에 다섯 개의 자연수가 주어진다. 100보다 작거나 같은 자연수이고, 서로 다른 수이다.

```yaml
30 42 70 35 90
```

```yaml
1 2 3 4 5
```

```yaml
30 45 23 26 56
```

```yaml
3 14 15 92 65
```

## 출 력

> 첫째 줄에 N의 사이클 길이를 출력한다.

```yaml
210
```

```yaml
4
```

```yaml
1170
```

```yaml
195
```

## 코 드

> 5개 자연수 중 제일 작은 수 부터 1씩 더해간다. 그렇게 5개 자연수 중 3개 이상으로 나누어지는지 체크하하는 방식으로 해결!

<div class="code-example" markdown="1">

```csharp
using static System.Console;
using System.IO;
using System;
using System.Linq;

namespace Algorithm
{
    class Program
    {
        static void Main(string[] args)
        {
            StreamWriter writer = new StreamWriter(OpenStandardOutput());
            StreamReader reader = new StreamReader(OpenStandardInput());

            int[] input = Array.ConvertAll(reader.ReadLine().Split(), int.Parse);

            long result = input.Min();
            int count = 0;

            while(true)
            {
                for (int i = 0; i < 5; i++)
                {
                    if(result % input[i] == 0)
                        count++;
                }

                if(count >= 3)
                    break;

                count = 0;
                result++;
            }

            writer.WriteLine(result);

            writer.Close();
            reader.Close();
        }
    }
}

```

</div>
```
