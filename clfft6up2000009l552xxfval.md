---
title: "TSwizzle: How Taylor Swift inspired me to create my own tiny esolang"
datePublished: Sun Mar 19 2023 19:46:42 GMT+0000 (Coordinated Universal Time)
cuid: clfft6up2000009l552xxfval
slug: tswizzle-how-taylor-swift-inspired-me-to-create-my-own-tiny-esolang
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679128721236/e9067712-28a3-46d3-92c2-117435ed8a89.png
tags: python, development, beginner, esolang, wemakedevs

---

# Introduction

Hi! For those who are new to my blog, I'm Abhilipsa, and today I'm going to take you on a ride with me through my experimentation with designing (my first-ever!) esolang using Python, inspired from Taylor Swift's lyrics.

You can always refer to this blog as a resource for creating your own esolang with minimal work.

# What's Esolang?

An Esolang or Esoteric Language is a computer programming language designed to experiment with weird ideas, to be hard to program in, or as a joke, rather than for practical use.

These esoteric languages are sometimes built using one or more of the mainstream programming languages.

## **Purpose**

There are several reasons behind the creation of an Esolang, some of which are:

* To introduce minimalism in the number of instructions required to execute a program, i.e., Brainf\*ck, OISC, and Lazy K.
    
* To explore alternative ways of designing a programming language.
    
* To follow a non computer related (perhaps pop culture based) theme, i.e., ArnoldC (inspired from Arnold Schwarzenegger's famous quotes), Hodor (drawing inspiration from Game of Thrones), etc.
    
* To complicate stuff sometimes (!?) so that programmers can collectively give up and throw their computers away lol.
    

# Inspiration for TSwizzle

I began listening to Taylor Swift in around 2015 when my friend introduced me to one of her popular songs from 'Red', "I knew you were trouble". That was when I started rooting for her new albums, and was *Enchanted* by her versatility and lyricism (saw what I did there? 😉). Her albums 'Folklore' and 'Evermore' got me through the pandemic and inspired to me write several poems. Well, this was just the regular literature enthusiast side of me. But how can a Computer Science undergrad pay tribute to her art of telling stories that resonate with the audiences through her songs, and the creative process behind it?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679165409180/34de56aa-b970-4ae3-b44c-c46f50de53db.jpeg align="center")

(Picture Credits: Taylor Swift on Instagram)

I came across esolangs about a year ago, when I came to know about ArnoldC, an Arnold Schwarzenegger based programming language written in Scala. Some months later, a toy programming language called BhaiLang based on an inside joke was designed using TypeScript. I also came across some others like FreakC (implemented in Batch) and Brainf\*ck (smallest Turing-complete language implemented in several mainstream programming languages such as Python, etc). This piqued my interest in discovering new meanings of Taylor Swift lyrics by the means of Computer Science.

# Turning my terminal into The Eras Tour

I'm a 6th semester CSE undergraduate student who is going to study Compiler Design in the current sem. I do have sound knowledge in Formal Language and Automata, but do not have the experience of implementing it practically in a project. Although, for this one, I decided to set it all aside and step into Swift's shoes, that is, to keep the project small and accomplish it using the simplest of means available.

The biggest dilemma was to choose a programming language that can enhance my experience in designing a toy language like TSwizzle, even with little to no knowledge of the same. When I chose Python, I knew that most of my work was done, then and there. However, there is no perfect tutorial or blog available on internet to guide a total beginner on how and where to start in order to execute the idea of esolang that I had come up with successfully, so I simply began to list different features and implement them one at a time, taking help from bits and pieces of references from various tutorial websites when stuck.

## Creating a virtual environment

I used VSCode for this project. I first created a workspace folder, then inside that, a project folder and within that, set up a virtual environment using the command:

`python -m venv my_venv`

I then noticed a similar dialog:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679167967340/73bfd38b-08c3-4eea-b644-311340bc82ce.png align="center")

I clicked Yes. Then I opted for Python 3.10 under `Python: Select Interpreter` by clicking:

`Ctrl + Shift + P`

To activate my Python virtual environment in my Windows CMD, I navigated to the project folder where the my\_venv folder is located, and typed:

`my_venv\Scripts\activate.bat`

And, Eureka! My virtual environment was ready for the concert!

## Creating a session

So I created a `.py` file that will contain my main code to enable the terminal for welcoming new users, locating and reading a `.tswizzle` file line by line, printing the lines of code in the file on the terminal, sending it for translation and executing it.

> Why TSwizzle of all names?
> 
> It's a nickname that fans use for Taylor Swift as a term of endearment.

However, I decided that each time the main code is run, a session will be created and during this session, the user can:

1. directly write the TSwizzle code or command and execute it to receive output (like interactive Python IDLE)
    
2. compile and execute a `.tswizzle` type file to retrieve output
    

The session takes input from the user their favourite Taylor Swift era and displays it as a unique name for the session:

```plaintext
SESSION CREATED.
What is your favourite Taylor Swift era? 1989
1989 (Taylor's Version) >>> <enter command>
```

To make the session a bit more interesting and welcoming, I used funky texts along with the text art that I generated from my favourite pictures of Taylor Swift and her album titles.

## Making sure my interpreter recognizes only `.tswizzle` type files

So I decided to write a piece of code that would make my interpreter recognize and execute only those files that end with `.tswizzle` extension. I also customized the error message that would show up when the user tries to run a file of any other type.

I also dedicated a Taylor Swift lyric as a command to run the file, so when I'd run a `test.tswizzle` file, I'll have to do something like this:

```plaintext
1989 (Taylor's Version) >>> DARLING, LET'S RUN test.tswizzle
```

The `test.tswizzle` file looks like below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679251479792/6365145c-518d-42f9-81c6-88d7c013dc35.jpeg align="center")

What the program does is that it takes two integer values and prints its sum.

## How does my interpreter work?

Most of the work done by the main code or interpreter is done by a loop of following activities:

extracting the entire user input code from the terminal or code from the `.tswizzle` file line by line —&gt; sending it to translator method —&gt; locating if a term (phrase/command/etc.) is present in it at the right place —&gt; if YES, mapping it to corresponding if-elif block that will replace with and/or append new Python equivalent code, and if NO, it will throw a customised error message —&gt; executing the revised code using exec()

## Handling Errors and Interrupts

Along with customising error messages for not being able to recognize the file type or command, I also added try-except-else blocks to handle several other types of errors and interrupts. Some of the errors and interrupts that I have come across till now are EOFError, ValueError and KeyboardInterrupt. I also customized the messages that user would receive upon coming across the said errors and interrupts.

## Commands and Keywords

As I have decided to keep this esolang small and simple, till now I've only designed the following commands and keywords:

| Commands and Keywords | What they do |
| --- | --- |
| DARLING, LET'S RUN &lt;filename.tswizzle&gt; | Executes filename.tswizzle file. |
| GOODBYE GOODBYE GOODBYE | Marks the EOF when specified within the file, but when specified in the terminal directly, it acts as `pass` keyword. |
| I JUST WANNA SHOW YOU &lt;message&gt; | Prints &lt;message&gt; on the output screen/terminal where &lt;message&gt; can be anything the user wants to print, i.e., string, numbers, etc. Example: `I JUST WANNA SHOW YOU "Hello World"` |
| NUMBER ON ME | Converts user input to number type. Basically an &lt;input\_type&gt;. |
| INVISIBLE STRING TYING ME TO YOU | Converts user input to string type. Basically an &lt;input\_type&gt;. |
| SPEAK NOW OR FOREVER HOLD YOUR &lt;input type&gt; &lt;variable\_1&gt;, &lt;variable\_2&gt; | Takes one or multiple user input. Usually input type is specified along with it followed by the user input, i.e., `SPEAK NOW OR FOREVER HOLD YOUR INVISIBLE STRING TYING ME TO YOU x,y` |
| ARE WE IN THE CLEAR YET? | Clears screen, whether specified within the file or directly in the terminal. |
| IF YOU'VE GOT A (condition\_1) I'M JEALOUS OF &lt;statement\_1&gt; BUT IF YOU'RE (condition\_2) THAT'S HONESTLY &lt;statement\_2&gt; CAUSE YOU'RE SO GORGEOUS IT ACTUALLY &lt;statement\_3&gt; | Python's If-Elif-Else equivalent of conditional statements. |

# Demo

So, I ran the above shown test file and this is how it went:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679252003384/8767cd1a-0b7c-49c4-902f-767a220df9d9.jpeg align="center")

(Spot my favourite TS Album?)

Always ready for a Taylor Swift concert in my terminal! 🥳

# Conclusion

After tweaking a bit here and there, I managed to add the above mentioned functionalities to the esolang. Currently, the TSwizzle code can only take as input different string and integer values, operate on them and print the value. Other than that, it can clear the terminal screen. Through the interpreter, you can locate your TSwizzle file, run it, find the number of lines of code present in the file, execute and receive the output on the terminal. Plus, I have managed to achieve this much without importing or using any additional package.

The project is still under progress, as I'm aiming to add more functionalities such as loops, and improve code readability, therefore I'll keep you updated with a series of blog posts (and I'll attach GitHub link soon!)

This is Taylor's sign for you to get started with your own tiny esolang without waiting to rely on tutorials or guides.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679254492249/055691ec-299c-4a6f-b7b6-dea512430ef7.gif align="center")

Thank you for reading! ❤️