---
layout: post
title: Regular Expression and Python re Module
date: 2020-04-06
published: True
mathjax: True
catalog: true
tags:
  - Python
  - IT tools
  - regular expression
---
# TOC
1. Introduction
{:toc}

# Introduction
As a machine learning engineer, sometime I need to retrieve information from string or text file. Besides the basic functions of Python build-in string, regular expression is an important tool.

I will summarize some basic knowledge of regular expression and Python re module in this post. We can get more informations from the references listed in the last section.

# Regular Expression Basics

## Metacharacters

Basics:

| Metacharacters |                                    Matching                                    |
|:--------------:|:------------------------------------------------------------------------------:|
|        .       |                         All charactor except a newline                         |
|        ^       |                               Start of the string                              |
|        $       |                                End of the string                               |
|       \w       | Unicode word characters including English, Chinese numbers and underscore etc. |
|       \s       |              Unicode whitespace characters including " \t\n\t\f\v"             |
|       \d       |                                     Numbers                                    |
|       \b       |                                  Word boundary                                 |
|       \W       |              Any character which is not a word character             |
|       \S       | Any characters which is not whitespace, equivalent of [^ \t\n\t\f\v] |
|       \D       |                              not numbers                             |
|       \B       |                           not word bounday                           |
|      [^x]      |                       any word which is not 'x'                      |


Repeating things:

| Metacharacters |          Matching         |
|:--------------:|:-------------------------:|
|        *       | Repeat zero or more times |
|        +       | Repeat once or more times |
|        ?       |    Appear zero or once    |
|       {n}      |       Appear n times      |
|      {n, }     |   Appear n or more times  |
|      {m,n}     |    Appear m to n times    |


## Group and Backreference

Group:
```python
p = re.compile('(a(b)c)d')
m = p.match('abcd')
m.group(0)
# "abcd"
m.group(1)
# "abc"
m.group(2)
# "b"
```

Backreference:
```python
p = re.compile(r'\b(\w+)\s+\1\b')
p.search('Paris in the the spring').group()
# "the the"
```

## Lookahead Assertion

Refer to Ref[2].

# Python re Module

## Basic Methods

### Matching String

|   Method   |                               Description                              |
|:----------:|:----------------------------------------------------------------------:|
|   match()  |        Determine if RE matches **at the begining of** the string       |
|  search()  | Scan through a string, looking for **any location** where the RE match |
|  findall() |            Find all substrings that matches, return as list            |
| finditer() |          Find all substrings that matches, return as iterator          |

### Modifying String

|  Method |                                       Description                                      |
|:-------:|:--------------------------------------------------------------------------------------:|
| split() |           Split the string into a list, splitting it whereever the Re matches          |
|  sub()  |      Find all substring where Re matches, and replace them with a different string     |
|  subn() | Does the same thing as sub(), but returns the new string and the number of replacement |

## Common Problems

### Raw String Notation
For example, you want to match the string `"\section"`, since `\` is a metacharactor in regular expression, you should put backslash before `\` which resulting in `"\\section"`.

**However, to express this in Python string literal, both backslash need to be escaped which will resulting in `"\\\\section"`.** This will definitly leads to duplications of backslash and makes the result string hard to understand

To solve the problem, regular string notation is introduced in Python. Below is the mapping from Python regular string to raw string notation string:
1. `"ab*"` $\rightarrow$ `r"ab*"`
2. `"\\\\section"` $\rightarrow$ `r"\\section"`
2. `"\\w+\\s+\\1"` $\rightarrow$ `r"\w+\s+\1"`

### Greedy VS Non-greedy Fasion
Non-greedy qualifiers such as `*?`, `+?`, `??`, `{m, n}?` will match text as little as possible.

Code examples are as follows:
```python
begin = "<"
end = ">"
string = "<hah><ffd>"

pat = re.compile(begin+'(.*?)'+end,re.S)
non_greedy_result = pat.findall(string)
pat = re.compile(begin+'(.*)'+end,re.S)
greedy_result = pat.findall(string)
print(f"Non-greedy result: {non_greedy_result}")
print(f"Greedy result: {greedy_result}")

## Output:
# Non-greedy result: ['hah', 'ffd']
# Greedy result: ['hah><ffd']
```

# Ref
1. [Python re Official Documentation](https://docs.python.org/3/library/re.html)
2. [Regular Expression HOWTO (re tutorial in python.org)](https://docs.python.org/3/howto/regex.html#common-problems)
2. [Regex101, online regular expression tester (used as tester and cheatsheet)](https://regex101.com/)
3. [正则表达式30分钟入门教程](https://deerchao.cn/tutorials/regex/regex.htm#lookaround)
