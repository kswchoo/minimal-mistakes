---
layout: post
lang: en
title:  "Swift and C plays together" 
translation_id: ec02199e1cdbe81577f9c401091ce172
redirect_from:
  - /en/blog/Swift-and-C-plays-together/
---

<span class="dropcap">T</span>oday, Apple released [Swif](http://swift.org) by open source.
I thought that "If can, writing Apache module in Swift must be a cool idea!", so I did some experiment.

First of all, configure Swift development environment. [Getting Started](https://swift.org/getting-started/) section of Swift homepage is great starting point. (Actually untaring the package is everything I did...)

Now let's write simple Swift file. I named this as `function.swfit`.

{% highlight swift %}
public func sayHello() {
	print("Hello, swift!")
}
{% endhighlight %}

Compile this Swift file.

{% highlight bash %}
$ swiftc -c function.swift -parse-as-library
{% endhighlight %}

At first attempt, Swift compiler added unnecessary `main` symbol into object file when i didn't add `-parse-as-library` flag.
Anyway, the problem was solved by using this flag.

Now let's find the name of `sayHello` function in object file. We can use objdump tool to do this.

{% highlight bash %}
$ objdump -t function.o

function.o:     file format elf64-x86-64

SYMBOL TABLE:
0000000000000000 l    df *ABS*	0000000000000000 function.o
0000000000000000 l     O .rodata.str1.16	0000000000000011 .L__unnamed_1
0000000000000000 l    d  .text	0000000000000000 .text
0000000000000000 g     F .text	000000000000009e _TF8function8sayHelloFT_T_
0000000000000000         *UND*	0000000000000000 _TFSSCfT21_builtinStringLiteralBp8byteSizeBw7isASCIIBi1__SS
0000000000000000         *UND*	0000000000000000 _TFs5printFTGSaP__9separatorSS10terminatorSS_T_
0000000000000000         *UND*	0000000000000000 _TIFs5printFTGSaP__9separatorSS10terminatorSS_T_A0_
0000000000000000         *UND*	0000000000000000 _TIFs5printFTGSaP__9separatorSS10terminatorSS_T_A1_
0000000000000000         *UND*	0000000000000000 _TMSS
0000000000000000         *UND*	0000000000000000 _TTSg5P____TFs27_allocateUninitializedArrayurFBwTGSax_Bp_
{% endhighlight %}

We can find out that the compiled name of the function is `_TF8function8sayHelloFT_T_`.
Now write simple `main.c` C code to call this symbol.

{% highlight C %}
#include <stdio.h>

void _TF8function8sayHelloFT_T_();

int main() {
    printf("Hello from C!\n");
    _TF8function8sayHelloFT_T_();
}
{% endhighlight %}

Now compile C code and link with Swift object file that we rolled before.

{% highlight bash %}
$ gcc -c main.c
$ swiftc function.o main.o -o hello -L/usr/local/lib
{% endhighlight %}

Execute.

{% highlight bash %}
$ ./hello
Hello from C!
Hello from Swift!
{% endhighlight %}

It worked. C can call Swift code. 

<strike>Now what shell I do?</strike>