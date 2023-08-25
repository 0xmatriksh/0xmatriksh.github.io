---
layout: "../../layouts/BlogLayout.astro"
title: "Django Supports Concurrency"
pubDate: 2023-08-25
description: "This post is about how concurrency is achieved in django."
author: "0xmatriksh"
tags: ["Python", "Concurrency"]
---

We know that Python is not concurrency friendly language(until 2023 August at least), which is because of the **GIL**(Global Interpreter Lock) in the language which was basically for preventing the python program from unnecessary problems of race condition with **reference counting**(how many time object is referenced) for memory management. It effects the CPU bound tasks as reference count of object need to shared among processor and if two processor update them at a same time race condition will occur. But it has no effect on IO bound tasks.

On the other hand, concurrency in Django would have helps the web service to handle the requests concurrently utilizing every processor in the machine. But thanks to the engineers, we have the facility to attain the concurrency with the workaround. To achieve concurrency in Django, basically what is done is we have multiple python interpreter for every processor so despite of GIL we can achieve concurrency. This is done with WSGI server like Gunicorn.

Gunicorn is a popular server for running Django. With Gunicorn you can configure the number of workers and it will automatically spawn your Django site over multiple processes /threads accordingly.

Apart from concurrency other things that makes Django faster are:

**Threading**: With threading we inside a processor leverage threads for I/O bound operation using the parallelism support to achieve better performance.

**Asynchronous Support**: With asynchronous support in Django after 3.0 version, in the single thread processing I/O bound tasks can be waited and the processing can continue without blocking which makes the performance more better.

In conclusion, with threading multiple threads for multiple I/O bound operation to do task faster even if blocked in a thread but now with async single thread can do I/O bound task without being blocked.
