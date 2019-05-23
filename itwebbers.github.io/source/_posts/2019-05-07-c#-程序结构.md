---
layout: draft
title: 'C#程序结构'
categories:
  - C#
date: 2019-05-07 22:09:00
author: 'zander'
tags:
  - C#
---


# C#程序结构

1. C#中的程序结构包括：程序，命名空间，类型，成员，程序集

```c#
using System;
namespace Acme.Collections
{
    public class Stack
    {
        Entry top;
        public void Push(object data) 
        {
            top = new Entry(top, data);
        }

        public object Pop() 
        {
            if (top == null)
            {
                throw new InvalidOperationException();
            }
            object result = top.data;
            top = top.next;
            return result;
        }
        
        class Entry
        {
            public Entry next;
            public object data;
            public Entry(Entry next, object data)
            {
                this.next = next;
                this.data = data;
            }
        }
    }
}
```