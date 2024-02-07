---
layout: default
title: "[백준] C# : 명령 프롬프트 (1032번)"
parent: Bronze
grand_parent: Algorithm
nav_order: 1
permalink: /docs/Algorithm/Bronze/Bronze1_1032/
---

## 문 제

> 시작 -> 실행 -> cmd를 쳐보자. 검정 화면이 눈에 보인다. 여기서 dir이라고 치면 그 디렉토리에 있는 서브디렉토리와 파일이 모두 나온다. 이때 원하는 파일을 찾으려면 다음과 같이 하면 된다.
>
> dir \*.exe라고 치면 확장자가 exe인 파일이 다 나온다. "dir 패턴"과 같이 치면 그 패턴에 맞는 파일만 검색 결과로 나온다. 예를 들어, dir a?b.exe라고 검색하면 파일명의 첫 번째 글자가 a이고, 세 번째 글자가 b이고, 확장자가 exe인 것이 모두 나온다. 이때 두 번째 문자는 아무거나 나와도 된다. 예를 들어, acb.exe, aab.exe, apb.exe가 나온다.
>
> 이 문제는 검색 결과가 먼저 주어졌을 때, 패턴으로 뭘 쳐야 그 결과가 나오는지를 출력하는 문제이다. 패턴에는 알파벳과 "." 그리고 "?"만 넣을 수 있다. 가능하면 ?을 적게 써야 한다. 그 디렉토리에는 검색 결과에 나온 파일만 있다고 가정하고, 파일 이름의 길이는 모두 같다.

## 입 력

> 첫째 줄에 파일 이름의 개수 N이 주어진다. 둘째 줄부터 N개의 줄에는 파일 이름이 주어진다. N은 50보다 작거나 같은 자연수이고 파일 이름의 길이는 모두 같고 길이는 최대 50이다. 파일이름은 알파벳 소문자와 '.' 로만 이루어져 있다.

```yaml
3
config.sys
config.inf
configures
```

```yaml
2
contest.txt
context.txt
```

```yaml
3
c.user.mike.programs
c.user.nike.programs
c.user.rice.programs
```

```yaml
4
a
a
b
b
```

```yaml
1
onlyonefile
```

## 출 력

> 첫째 줄에 패턴을 출력하면 된다.

```yaml
config????
```

```yaml
conte?t.txt
```

```yaml
c.user.?i?e.programs
```

```yaml
:
```

```yaml
onlyonefile
```

## 코 드

- 처음 입력 받은 문자열을 기준으로 삼고, 다음 행에 오는 문자열과 비교하면서 틀리면 '?'를, 맞으면 해당 문자를 StringBuilder를 사용하여 Append 해주었다.

<div class="code-example" markdown="1">

```csharp
using static System.Console;
using System.Text;

namespace Algorithm
{
    class Program
    {
        static void Main(string[] args)
        {
            int N = int.Parse(ReadLine());
            string[] str = new string[N];
            StringBuilder sb = new StringBuilder();

            for (int i = 0; i < N; i++)
                str[i] = ReadLine();

            for (int i = 0; i < str[0].Length; i++)
            {
                string s = "";

                for (int j = 1; j < N; j++)
                {
                    if(str[0][i] != str[j][i])
                    {
                        s = "?";
                        break;
                    }
                }

                if(s == "")
                    s = str[0][i].ToString();

                sb.Append(s);
            }

            WriteLine(sb);
        }
    }
}

```

</div>
```
