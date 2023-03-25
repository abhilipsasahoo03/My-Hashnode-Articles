---
title: "Want to PL(a)Y or SL(a)Y the esolang game?: Choose your Python Parser package"
datePublished: Sat Mar 25 2023 20:28:27 GMT+0000 (Coordinated Universal Time)
cuid: clfofbnd7000109l4fieack3t
slug: want-to-play-or-slay-the-esolang-game-choose-your-python-parser-package
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679775958983/e8a1daf7-dfb8-4e83-8a07-eb5986ea1759.png
tags: python, development, esolang, wemakedevs

---

# Introduction

Hi everyone! I'm Abhilipsa and I have been summoned by the ghosts of all the esolangs you're yet to make, to help you make this crucial decision for your (perhaps, first-ever?) esolang.

Several modules have been designed to ease the development of an esolang on top of Python. This includes PLY and SLY, both of which work like possible alternatives to ANTLR — well mature and better supported.

PLY (Python Lex-Yacc) and SLY (Sly Lex-Yacc) are both Python packages that provide tools for creating parsers and lexers in Python.

## But first, basics!

To understand what's about to come in a better way, let us first understand the basic concept of lexers and parsers.

### Throwback to my fourth class of Compiler Design

The basic flow to depict the Phases of a Compiler goes like this:

Source code —&gt; Lexical Analysis —&gt; Syntax Analysis —&gt; Semantic Analysis —&gt; Intermediate Code Generation —&gt; Machine-Independent Code Optimization —&gt; Code Generation —&gt; Machine Dependent Code Optimization

Now, the terms Lexer and Parser have been derived from these phases of the Compiler—

* **Lexical Analysis**: Character stream is scanned and groups of characters are divided into meaningful sequences called "lexemes". For each lexeme, a token is produced of the form &lt;token-name, attribute-value&gt;.
    
* **Syntax Analysis**: It is the second phase of the Compiler and is also known as Parsing. Here, all the tokens produced from the previous phase are used in order to create a syntax tree, which is then sent as input to 'Semantic Analysis' phase to check the semantic correctness of the source code.
    

So for example, if we have a line of code that says:

`x = b + y * z`

Then, after lexical analysis, we end up with the following tokens: &lt;id, x&gt; &lt;=&gt;, &lt;id, b&gt;, &lt;+&gt;, &lt;id, y&gt;, &lt;\*&gt;, &lt;id, z&gt;

Next, we get the below syntax tree:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679776777036/d0a8c2e5-151e-427f-acb8-6238ac914a3b.png align="center")

Without diving any deeper into the background details, let us discuss about PLY and SLY.

# Python Parsing Packages

Let us first understand what the common abbreviation "LY" means for both the parsing packages: PLY and SLY.

## **Why the Lex-Yacc?**

Lex is a lexical analysis tool that can be used to identify specific text strings in a structured way from source text. YACC (Yet Another Compiler Compiler) is a grammar parser and parse tree generator which reads text and can be used to turn a sequence of words into a structured format for processing.

Both combine to form a pair of programs that help write other programs. Lex and YACC do the very same things that we discussed in the basics: Lexical Analysis and Syntax Analysis respectively.

## Python Lex-Yacc (PLY)

PLY is a Python implementation of both the tools, Lex and YACC, in two separate modules. These modules are named lex.py and yacc.py and work similar to the original UNIX tools lex and yacc.

PLY works differently from its UNIX counterparts in a way that it doesn’t require a special input file. Instead, it takes the python program as input directly. The traditional tools also make use of parsing tables (symbol tables and parse trees) which are hard on compiler time whereas PLY caches the results generated and saves them for use and regenerates them as needed.

Let us consider the example we previously took.

After importing the lex.py module by `import ply.lex as lex`, you can insert the below code:

```plaintext
#Token list of above tokens will be
tokens = ('ID','EQUAL','ID', 'PLUS', 'NUMBER', 'TIMES','ID' )

#Regular expression rules for the above example 
 t_PLUS    = r'\+'
 t_MINUS   = r'-'
 t_TIMES   = r'\*'
 t_DIVIDE  = r'/'
```

Then, the source line of code can be represented as the following:

('ID', 'x'), ('EQUALS', '='), ('ID', 'b'), ('PLUS', '+'), ('ID', 'y'), ('TIMES', '\*'), ('ID', 'z')

Another module of this package is yacc.py which can be used to implement one-pass compilers.

You can use the following to import yacc into your own python code by the help of `import ply.yacc as yacc`, which will provide you with the following features:

* LALR(1) parsing
    
* Grammar Validation
    
* Support for empty productions
    
* Extensive error checking capability
    
* Ambiguity Resolution
    

The explicit token generation token() is also used by yacc.py which continuously calls this on user demand to collect tokens and grammar rules. yacc.py spits out Abstract Syntax Tree (AST) as output (refer to the Syntax tree generated above).

Interpreting is a simple procedure. The basic idea is to take the tree, walk through it (through tree traversal procedures) and evaluate arithmetic operations hierarchically. This process is recursively called over and over again till the entire tree is evaluated and the answer is retrieved.

## Sly Lex-Yacc (SLY)

SLY is a rather modern flavour of PLY (derived from the latter as well), meaning that it further eases the method of lexing and parsing. However, it is justified to use SLY, if and only if your program is comparatively less complex to translate.

Here is a great resource for you to understand how SLY works and use it to implement in your own project: [Geeks4Geeks Resource on SLY](https://www.geeksforgeeks.org/how-to-create-a-programming-language-using-python/)

It also typically contains the same modules: Lexer and Parser, with the same behaviour as shown in PLY. The execution of the resultant tree is done in somewhat similar way.

You can use SLY to add more functionalities to your esolang. Loops and conditionals can be added. Modular or object oriented design features can be implemented. Module integration, method definitions, parameters to methods are some of the features that can be extended on to the same.

# If all same, why the duel?

There are some differences between the two packages from compiler design standpoint.

## Parsing Algorithm

The main goal of PLY is to stay fairly faithful to the way in which traditional lex/yacc tools work.

PLY uses a bottom-up parsing algorithm known as LALR(1) while SLY uses a more powerful parsing algorithm known as LR(1) than helps in handling wider range of grammars.

This can help you implement wider range of operations and statements in your esolang.

## Ease of Use

PLY package is not well maintained and is still under maintenance with very slow progress. SLY is a more modern package derived from PLY and is generally considered easier to use.

SLY has a simpler and more intuitive API, and it's documentation is more extensive and easier to navigate.

## Speed and Memory Efficiency

PLY is faster and more memory efficient than SLY. Speed and Memory efficiency has been traded for programmer's convenience in designing esolang.

This happens because PLY generates optimized C code for both parser as well as lexer. However, SLY generates purely Python code for the same.

## Compatibility

PLY is compatible with Python 2 and 3, while SLY is only compatible with Python 3.6 or newer. However, since Python 2 is not supported, this is less of an issue.

SLY's documentation, although, suggests not to expect any code previously written for PLY to work. That said, most of the things that were possible in PLY are also possible in SLY.

# **Conclusion**

SLY can be used to build parsers for “real” programming languages. Although it is not ultra-fast due to its Python implementation, SLY can be used to parse grammars consisting of several hundred rules (as might be found for a language like C).

However, if you have a complex grammar and are looking for optimized performance, I suggest you go for PLY.

Thank you for reading my blog!❤️