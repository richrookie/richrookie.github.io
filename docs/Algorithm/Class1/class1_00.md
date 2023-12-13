---
layout: default
title: "[백준] C# : 검증수 (2475번)"
parent: Class1
grand_parent: Algorithm
nav_order: 1
permalink: /docs/Algorithm/Class1/class1_00/
---

```yaml
using System;

namespace algorithm
{
    class Program
    {
        static void Main(string[] args)
        {
            string[] input = Console.ReadLine().Split();
            int sum = 0;

            for (int i = 0; i < input.Length; i++)
            {
                sum += (int)Math.Pow(int.Parse(input[i]), 2);
            }

            int result = sum % 10;

            Console.WriteLine(result);
        }
    }
}

```
