---
layout: default
title: "[백준] C# : 다리놓기 (1010번)"
parent: Silver
grand_parent: Algorithm
nav_order: 1
permalink: /docs/Algorithm/Bronze/Silver_1010/
---

## 문 제

> 재원이는 한 도시의 시장이 되었다. 이 도시에는 도시를 동쪽과 서쪽으로 나누는 큰 일직선 모양의 강이 흐르고 있다. 하지만 재원이는 다리가 없어서 시민들이 강을 건너는데 큰 불편을 겪고 있음을 알고 다리를 짓기로 결심하였다. 강 주변에서 다리를 짓기에 적합한 곳을 사이트라고 한다. 재원이는 강 주변을 면밀히 조사해 본 결과 강의 서쪽에는 N개의 사이트가 있고 동쪽에는 M개의 사이트가 있다는 것을 알았다. (N ≤ M)

> 재원이는 서쪽의 사이트와 동쪽의 사이트를 다리로 연결하려고 한다. (이때 한 사이트에는 최대 한 개의 다리만 연결될 수 있다.) 재원이는 다리를 최대한 많이 지으려고 하기 때문에 서쪽의 사이트 개수만큼 (N개) 다리를 지으려고 한다. 다리끼리는 서로 겹쳐질 수 없다고 할 때 다리를 지을 수 있는 경우의 수를 구하는 프로그램을 작성하라.

![](/assets/images/bridge_1010.png)

## 입 력

> 입력의 첫 줄에는 테스트 케이스의 개수 T가 주어진다. 그 다음 줄부터 각각의 테스트케이스에 대해 강의 서쪽과 동쪽에 있는 사이트의 개수 정수 N, M (0 < N ≤ M < 30)이 주어진다.

```yaml
3
2 2
1 5
13 29
```

## 출 력

> 각 테스트 케이스에 대해 주어진 조건하에 다리를 지을 수 있는 경우의 수를 출력한다.

```yaml
1
5
67863915
```

## 코 드

- 순열/조합에 대해 알고 있느냐 없느냐 문제!

- 예제에서 3번째 입력(13 29), 출력(67863915)을 int로 받으면 StackOverflow가 남.

BigInteger를 사용하면 해결!

<div class="code-example" markdown="1">

```csharp
using static System.Console;
using System.Linq;
using System;
using System.Numerics;

namespace Algorithm
{
    class Program
    {
        static void Main(string[] args)
        {
            int T = int.Parse(ReadLine());

            for (int i = 0; i < T; i++)
            {
                int[] input = ReadLine().Split(' ').Select(int.Parse).ToArray();
                int N = Math.Min(input[0], input[1]);
                int M = Math.Max(input[0], input[1]);

                BigInteger answer = 0;

                if(N > M || M < 0)
                    answer = 0;
                else
                    answer = Factorial(M) / (Factorial(M - N) * Factorial(N));
                    // nCr (조합) : nPr / r! = n! / (n-r)!r!

                WriteLine(answer);
            }
        }

        static BigInteger Factorial(int value)
        {
            if(value <= 0)
                return 1;

            return value * Factorial(value - 1);
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

### **순열/조합**

> - 순열 : 순서가 있다 = 순서에 영향을 받는다 = 조건이 없다 ex) 회장/부회장, 금메달/은메달/동메달
> - 조합 : 순서가 없다 = 순서에 영향을 받지 않는다 = 조건이 있다 ex) 조장
>
> 위 문제는 '다리끼리는 서로 겹쳐질 수 없다'
> **조건**이 걸렸기 때문에 **조합식(nCr)**로 풀면 된다!
>
> 문제의 그림 예제처럼 우측 7개점, 좌측 4개점이 있다.
> 좌측은 하나의 직선에만 연결이 가능하다.
> 즉, 좌측보다 점이 많은 우측점에서 좌측점을 선택한다는 뜻!
>
> 좌측점이 4개가 우측점 4개를 임의로 골랐다고 해보자.
> 4개의 연결된 점에서 우측점 4개를 이을 수 있는 방식은 순열(nPr), 즉 경우의 수가 4!이다.
> 그런데 **조건**이 걸렸기 때문에 중복되는 경우의 수를 없애야한다.
> 결론적으로 위 문제에서 '조건이 걸렸다'의 의미는 '중복된 선의 경우의 수는 제외시킨다'가 된다!
> 그래서 nCr(조합식) 으로 풀어야 한다.

### **BigInteger**

> 부호 있는 임의의 큰 정수!
> System.Numerics 선언
> 유니티 c#은 옛날 버전이기 때문에 사용불가.. 구현해서 사용해야한다..!
> https://github.com/keiwando/biginteger
