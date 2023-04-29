---
title: "ESOLANG 101: Cracking the Code of a Codeless language

Introduction"
datePublished: Sat Apr 29 2023 13:26:08 GMT+0000 (Coordinated Universal Time)
cuid: clh20ndjb000b09jp9rpy4sq5
slug: esolang-101-cracking-the-code-of-a-codeless-language-introduction
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682747461616/dff34dca-603e-4d6c-865f-9ff5fc55feb1.jpeg
tags: algorithms, programming-blogs, coding, esolang

---

Hi everyone! I'm back with another blog on Esolang. Diving into this topic has been a great journey for me, that I have been sharing with you since I started the **Esolangs** series. Since then, I have shared with you my attempts of creating *TSwizzle* without using any concrete grammar or lexer and parser packages. Then, I covered why Python is the best programming language for beginners to begin their Esolang journey and implement certain concepts from Compiler Design.

However, recently the professors in my college assigned us (the students of 6th semester batch) the task to present a thoroughly researched seminar on any interesting topic related to computer science: whether it be one of the new & emerging technologies or a journal article/research paper that interests you, etc. Many of my friends chose topics like Quantum Computing, Metaverse, Touchless Technology and more. Upon being approached by a confused friend on what topic to choose, I even suggested that Fog Computing (and perhaps a detailed comparison with Haze Computing) could be an intriguing theme.

But I chose the path I had been longing to take for quite a while, and decided to introduce my batchmates and professors to the beguiling, fascinating and thought-provoking world of Esolangs. Almost right then and there was born the title: **Cracking the Code of a Codeless Language**.

# Preparation

Although I had previously come across several esoteric languages such as ArnoldC, BhaiLang, FreakC, and more, I knew it wasn't enough to showcase the versatility of conceptual programming languages (a brand new term I came across in this journey) and their applications. So, I decided to read a few research papers on conceptual programming languages, took inspiration from them as well as from my own knowledge and work, and included the following in my flow of talk:

• a detailed introduction into Esolangs, some examples, difference between conceptual programming and experiential programming language

• case studies on Befunge and ArnoldC

• an insight into how I created TSwizzle without using any external lexer or parser package, challenges I faced and how to overcome them using the said packages

• basics of Compiler Architecture, what are lexers & parsers, what is lex & YACC

• why Python is an exemplar language for beginners to consider in order to learn the ABC's of Compiler Design and create their own esolang with concrete grammar, SLY vs PLY packages

• Advantages, Disadvantages and their potential (Future Scope)

![This is me excitedly speaking about Esolangs.](https://cdn.hashnode.com/res/hashnode/image/upload/v1682770050713/1ae10c4a-cb0d-48a4-9649-28bec842db50.jpeg align="center")

## A research paper by Daniel Temkin that piqued my interest

I read several research papers on this area at ResearchGate website, yet only one of them intrigued not only my programmer/developer self, but also my inner creative writer/poet/artist. This was a paper published by Daniel Temkin in the "**Journal of Science and Technology of the Arts**, Volume 9, No. 3 – Special Issue: xCoAx 2017" called **Language Without Code: Intentionally Unusable, Uncomputable, or Conceptual Programming Languages**, and it somehow coincided with the type of content I was looking forward to include, to keep my audience engaged and help them learn something new (the uncanny similarity between the title of the paper and that of my presentation is noteworthy).

### Befunge

When I came to read of Befunge in this paper, I felt like I got a Déjà Vu: something I knew I had come across before but don't remember when and how. It took me around 20 minutes to figure out that the time I had registered myself at *esolangs.org* to create a dedicated page for TSwizzle, I bumped into a CAPTCHA test that required me to enter the output of a Befunge code for verification. That was when I had also discovered an online Befunge93 interpreter to help me with the CAPTCHA.

I hadn't put much thought into it back then, but this seminar provided me with an opportunity to understand Befunge in a better and even deeper way, so I decided to do my first case study on it.

Befunge is actually a two dimensional, stack based, reflective esoteric programming language developed by Chris Pressey. You can say it takes inspiration from Pushdown Automata which is a finite automata augmented with an extra stack memory operating on LIFO principle. In Befunge, the code of the program is arranged in a 2D grid and a pointer is used to keep track of the current element. The syntax of Befunge consists of several symbols which perform different operations related to characters, pointer, stack and printing output as integer/character onto the screen.

The syntax table is attached below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682757507506/809c7ff4-48d9-4003-8ca2-62948f59a13c.jpeg align="center")

I included a "Hello World" example in Befunge to demonstrate how the interpreter works. The boilerplate code for "Hello World" looks like this:

```plaintext
vv"Hello World!"<
>               ^
 >,,,,,,,,,,,,@
```

But, in this, it was difficult to write a customised message to the output screen without modifying the number of "," as it is associated with popping the corresponding ASCII values of each character of the message and displaying them as characters. I had to find out a way in which we can keep all the symbols constant and only change the message according to our needs. After several trials and errors, I could write the following optimized version of the above boilerplate code:

```plaintext
<>:#,_@v<"Hello World!"
 ^     v       
 ^<<<<<<
```

Below is a demo video of how it works:

<iframe src="https://veed.io/embed/9a93f953-275b-4d6c-8a5a-134a69acfb92" width="744" height="504"></iframe>

What happens here:

Pointer moves right to left —&gt; Stores “Hello World” right to left with “H” on top of the stack —&gt; Pointer moves down, then left, then up, then right —&gt; Then the pointer enters a loop ⤵️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682765618031/318f6ab1-cbe3-4449-8964-c0bd72e40a10.jpeg align="center")

### Malbolge

I also learnt about Malbolge, a public domain esoteric programming language developed by Ben Olmstead in 1998. Its complexity draws its inspiration from its own name which is derived from the eighth circle of hell in Dante's Inferno, the Malebolge. It was specifically designed to be almost impossible to use, via a counter-intuitive 'crazy operation', base-three arithmetic, and self-altering code.

> Fun fact:
> 
> Malbolge is so difficult that even its creator didn't write a single program in it. In fact, it took two years post the creation of Malbolge to develop a search algorithm that could write the first-ever program in Malbolge. This search algorithm was written in Lisp.

### Other Esolangs with bizarre syntax

Besides Befunge and Malbolge, I got to learn about various other esoteric languages with weird syntax. These esolangs used less to no text, let alone code. For example, Whitespace is a Turing-complete esolang that contains only whitespaces as its syntax. Piet is a stack based programming language and its programs look entirely like images, especially abstract paintings, because its syntax includes colours. Another esolang prints its own program's source code as the output. Brainfuck has been an inspiration for hundreds of derivative languages, in part due to its simplicity of design: an easy way to get to Turing Completeness.

### Applications & Future Scope

Despite the complexities the Esolangs contain in their syntax, they have a great potential to be implemented in several domains. Although their main purpose is entangled between educational purpose (programming puzzles), artistic expression and pop-culture representation, Esolangs can be of great use because of **Code Obfuscation** which can protect source code of several softwares from being reverse-engineered, and provide an extra layer of security.

Therefore, the future scope of Esolang Designing includes areas such as Quantum Computing, Blockchain, AI and Cybersecurity.

> Fun Fact:
> 
> Why in Quantum Computing, you ask?
> 
> IBM released QISKit, a Quantum Information Software Kit that sits between quantum algorithms from one side, and the physical quantum device from the other. It can translate Python into Quantum Machine Language.
> 
> Similarly, in 2017, Microsoft introduced Q-Sharp (Q#) , an open-source, high-level programming language for developing and running quantum algorithms, as a part of Quantum Development Kit (QDK).

## My own input

To be honest, I only cherry-picked a few portions from the paper that felt relevant to my presentation and uncomplicated to explain to learners who are new to this aspect of programming languages. If you're interested in learning more with regard to Esolangs and their designing, I'd suggest you to patiently read the entire paper. I have provided a link to my copy of the paper below:

[Language Without Code: Intentionally Unusable, Uncomputable, or Conceptual Programming Languages](https://drive.google.com/file/d/1HCaa04Dyj_kFilALTR-584cLhg8FOsB2/view?usp=drivesdk)

So, this was all about the inspiration I drew from the paper. But, I also showcased my own work that I did on TSwizzle including the blog that I wrote on it in the **Esolangs** series, the challenges I faced in implementing loops without using any concrete grammar and how one can overcome it by using external packages provided by Python: PLY and SLY, which I had previously covered in my **Esolangs** series.

### ArnoldC

My second case study was on ArnoldC, an esolang inspired by Arnold Schwarzenegger's famous lines, developed by L Hartikka. This esolang is written in Scala, and therefore it can be executed using Java Virtual Machine (JVM).

Here is a program that I used as an example to explain its syntax. This program takes two numbers as input and prints its sum.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682770821421/854e0a7b-f626-4e05-a72e-a953e00fef05.jpeg align="center")

The Syntax table is as follows:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682771500603/e364eb72-c1a9-4183-8f10-bf50505bb77b.jpeg align="center")

### Other Esolangs

I demonstrated the syntax of "Hello World" program in BhaiLang as an example of a programming language created entirely in the way we talk to our friends. As an example of writing programs in our mother tongue, I explained about O-Lang, an esolang with syntax written in Odia, which can be imported as a Python package and used. FreakC is an example of a multi-paradigm esoteric programming language which looks like Batch, written in Batch and compiles to Batch as well. We have several other Esolangs inspired by pop-culture, gaming lingo, and more, such as Hodor (inspired from Game of Thrones), Among Us Esolang (inspired from the Among Us game), etc.

# **Glimpse of me and my thoughts**

Here is a glimpse of me explaining languages:

%[https://youtu.be/BRXoaChVshk] 

Although, I don't have the recording of the entire session, yet if you're interested, feel free to take a look at the slides I made:

%[https://docs.google.com/presentation/d/1HHM5PXjrSKqb9Vwmng-ZBuCC90hsURsG/preview?usp=drivesdk&ouid=113922024806172039880&rtpof=true&sd=true] 

# Conclusion

I believe Esolang design can be used to create even more efficient, effective and powerful programming languages in the future that can revolutionize the way we look or perceive data structures and algorithms. It can bridge the gap between creativity and technology. And this is my small contribution to taking a step further towards achieving the same.