---
layout: "../../layouts/BlogLayout.astro"
title: "Pointers in Go"
pubDate: 2023-08-22
description: "This post is about the pointers in Go and how it is different from C/C++"
author: "0xmatriksh"
tags: ["Go", "Pointers", "C/C++"]
---

If you are writing Go, it may be hard to find when to use pointers and when not to, especially in initial days.

So, let's talk bit about what it is like and how does it work in Go. And to start this I will start will a major but obvious statement.

**Pointers in Go do not function the way they do in C/C++**

In Go, we have provision of garbage collection method to manage memory which is basically for managing the memory in **heap**. Here the **garbage collector** is like a built-in janitor that cleans up memory you're not using anymore. If we use pass by value approach we use **stack** for storing the data, but if we use pointers, Go needs to perform **Escape Analysis** to figure out if the variable should be stored on the heap or the stack, which adds some overhead here. But more than that, when we store the data in heap and we will lose time when heap is running- when the garbage collector is doing its cleaning.

But yeah, pointer do avoid unnecessary copying of the data all the time, especially when working with big struct.
