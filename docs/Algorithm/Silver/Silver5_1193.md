---
layout: default
title: "[백준] C# : 분수찾기 (1193번)"
parent: Silver
grand_parent: Algorithm
nav_order: 3
permalink: /docs/Algorithm/Bronze/Silver_1193/
---

> [Try Again]

## 문 제

> 무한히 큰 배열에 다음과 같이 분수들이 적혀있다.

![](assets/images/fraction_1193.png)

> 이와 같이 나열된 분수들을 1/1 → 1/2 → 2/1 → 3/1 → 2/2 → … 과 같은 지그재그 순서로 차례대로 1번, 2번, 3번, 4번, 5번, … 분수라고 하자.
>
> X가 주어졌을 때, X번째 분수를 구하는 프로그램을 작성하시오.

## 입 력

> 첫째 줄에 X(1 ≤ X ≤ 10,000,000)가 주어진다.

```yaml
1
```

```yaml
2
```

```yaml
3
```

```yaml
9
```

```yaml
14
```

## 출 력

> 첫째 줄에 분수를 출력한다.

```yaml
1/1
```

```yaml
1/2
```

```yaml
2/1
```

```yaml
3/2
```

```yaml
2/4
```

## 코 드

> 몇 번째 대각선에 있는지 구하면 쉽게 푸는 문제! 그런데 오래 걸렸다..
> 문제를 보면 **홀수는 대각선 위 방향으로, 짝수는 대각선 아래 방향**의 순서를 갖는다.
> 하지만 문제를 풀 때는 짝수번째 대각선이면 시작점을 대각선 **'아래 방향'**에서 부터 푸는 방식 적용!
> 반대로 홀수번째 대각선이면 시작점을 대각선 **'위 방향'**으로부터 시작!

<div class="code-example" markdown="1">

```csharp
using static System.Console;

namespace Algorithm
{
    class Program
    {
        static void Main(string[] args)
        {
            int X = int.Parse(ReadLine());

            int count = 0;          // 대각선에서 제일 끝에 번째 녀석
            int sequence = 0;       // 대각선 순서가 홀/짝인지 구분하는 녀석

            while(count < X)
            {
                sequence++;
                count += sequence;
            }

            int dif = count - X;    // 홀/짝 대각선에서 몇 번째에 있는지

            int denominator = 0;
            int numerator = 0;

            if(sequence % 2 == 0)
            {// 짝수번째 대각선
                denominator = 1 + dif;
                numerator = sequence - dif;
            }
            else
            {// 홀수번째 대각선
                denominator = sequence - dif;
                numerator = 1 + dif;
            }

            WriteLine($"{numerator}/{denominator}");
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
