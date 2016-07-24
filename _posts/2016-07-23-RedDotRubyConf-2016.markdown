---
layout: post
title:  "RedDot Ruby Conf 2016"
date:   2016-07-23 19:47:41
categories: conf
---
I recently had a chance to attend RedDot Ruby in Singapore, and I have to say it was an amazing experience in my career. I had never attended a Ruby conf before, but I watched a lot of them online. Getting to meet such great people like Matz, and Aaron Patterson in person was like a dream come true.

If you are interested in the talks given at RedDot Ruby this year, you can check out [this great gist](https://gist.github.com/cheeaun/43843c8b1c764825b9f3d63ed8f5bd78) that has the videos of all the talks.

When I talked to Matz I thanked him for Ruby and the great community. He is a very down to earth type of guy and extremely friendly. He reminded me of a saying that rubyists have: `Matz is nice so we are nice`. That was the point I realised how accurate that is.

Same goes to Aaron, very friendly and nice, plus he has stickers of his cats (haha).

Since all the talks are available online I just want to briefly share about my favourite talks. I should mention that they can get a little bit technical.

First up was Matz’s. He talked about new things and improvements in future Ruby versions.

There are different kinds of typing, for example:

- Strong Dynamic (Ruby)
- Weak Dynamic (Perl, Haskel)
- Strong Dynamic (Hskell)
- Weak Dynamic (C)

There’s a design policy which is duck typing and it's very important in ruby.

In dock typing we:

- Do not classify
- Do not check types
- We just ask objects to behaves

Static Typing basically lacks flexibility. Some other programming languages offer gradual typing or optional typing, and they are fundamentally static. Ruby wants something that is similar to staic typing (powerful), but it should allow duck typing. For example, GO is a static typed language that allows duck typing. it is called structural subtyping.

Matz calls this soft typing for Ruby.  Soft Typing is a type system that is defined by behaviour. Behaviours are sets of methods (and argument types), thus inferred types don’t have names. However, this is still just a concept and a part of Ruby3 project.

Here is what Matz wants for Ruby3:

- Soft typing
- 3 times faster
- Real concurrency

He also talked about Ruby 2.4 and some of it’s changes are listed below:

**FixNum / BigNum Unification**

There will be no longer fixnum and bigness, just integers. There should not be so many compatibility issues, but if your program cares about the size of integers then you might have some issues.

**Smarter Conversions**

Some methods like upcase and downcase worked only for ASCII characters. With a lot of people using Unicode, Ruby now handles unicode case mappings. If you want to stick with ASCII you can do  `.upcase(:ascii) `.

That was it for Matz.

I am now going to cover Aaron’s talk which I really enjoyed. It is about Ruby GC algorithms in MRI. His talk stated as usual with some jokes, and he demonstrated different types of typing with his mechanical keyboard.

What is GC in high level?

You can think of objects as a tree and GC finds nodes in the tree that aren't referenced from the root anymore and then frees them up. It uses different algorithms to find nodes that are not referenced.

What types of collectors MRI has?

Here is a list:

**Mark & sweep**

Theres a Mark phase that starts from the root and marks all of the objects, then sweep phase frees everything that is not marked, and at the end we unmark them all.

![marksweep](http://deborah-digges.github.io/images/gc.png)

Pros:

- Very easy

Cons:

- Too slow
- Stops the world
- Visits all the objects everytime

**Generational**

To improve  the speed of Mark&Sweep it divides the objects into old and new gens. Good thing is that this does not visit the old objects everytime and only on full GC. Theres a _remembered list_ to keep track of interesting references such as when an old gen object points to a new gen. This is to avoid bad references.

![gen](http://patshaughnessy.net/assets/2013/10/30/ruby-gen5.png)

Pros:

- Faster

Cons:

- Not as easy:
- Stops the world

**Incremental**

To get around Stop the World there is Incremental GC. It uses Tri Color Marking:

- White: will be collected
- Black: No reference to white objects, but reachable from root
- Gray: Reachable from root, but not yet scanned.

![tricolor](http://adamansky.bitbucket.org/slides/gc/img/gc-tricolor.png)

The way it works is that:

- It picks an object from gray and and moves it to black.
- For each object that the object references, they get moved to black as well.
- Keep repeating this until gray is empty.

A big advantage is it can be interrupted at each step. Each step can be performed incrementally and halt time reduces. Although it has a similar problem with generational, and theres a _remembered list_ to avoid bad references.

In Ruby, GC:

- Is not parallel
- Is not real-time
- Is not compacting

Now as for allocation we have a heap that contains all of our objects. There are big chunks of memory that are called pages and each has a linked list (each page is 16k). They have slots which contains ruby objects (each object is 40bytes). when object is garbage collected it's taken out from the page.

As a problem there is poor reclamation in the process of GC. When we have a few pages and garbages get collected, objects won’t move to free up pages. We are basically left with some pages that have holes in them. This is one of the areas that Aaron is trying to improve.

As for the last part of the talk, here are some tools to use for inspections:

GC Inspection:

- GC::Profiler.enable
- GC:Profiler.report

Heap Inspection:

- ObjectSpace.dump_all
- ObjectSpace.dump

You can turn on tracing for objects. if you have problems finding where the object came from, you can use that:

- trace_object_allocations

That's it. I hope you enjoyed this post.
