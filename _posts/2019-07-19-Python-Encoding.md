---
layout: post
title: Python Encoding
subtitle:
date: 2019-07-19
published: True
tags:
  - Python
  - Python Encoding
---

# Basic Information

**ASCII**
**Unicode**
**GBK**： an extension of the GB2312 character set for simplified Chinese characters
**ISO-8859-1**
**Encode**: Unicode $\longrightarrow$ a byte string 
**Decode**:  bytes string $\longrightarrow$ characters.



Some Bullet points
1. ASCII is subset of Unicode
2. Standard Python strings are really byte strings,

# Code sample
## Encode
Both for Python2 and Python3
```
# Convert Unicode to plain Python byte string: "encode"
unicodestring = u"Hello world"
utf8string = unicodestring.encode("utf-8")
asciistring = unicodestring.encode("ascii")
isostring = unicodestring.encode("ISO-8859-1")
utf16string = unicodestring.encode("utf-16")
gbkstring = unicodestring.encode("gbk")
for string in [utf8string, asciistring, isostring, utf16string, gbkstring]:
    print(string)
```
Output
```
b'Hello world'
b'Hello world'
b'Hello world'
b'\xff\xfeH\x00e\x00l\x00l\x00o\x00 \x00w\x00o\x00r\x00l\x00d\x00'
b'Hello world'
```

## Decode
Python 2: 
```
# Convert plain Python string to Unicode: "decode"
plainstring1 = unicode(utf8string, "utf-8")
plainstring2 = unicode(asciistring, "ascii")
plainstring3 = unicode(isostring, "ISO-8859-1")
plainstring4 = unicode(utf16string, "utf-16")
plainstring5 = unicode(gbkstring, "gkb")
assert plainstring1 == plainstring2 == plainstring3 == plainstring4 == plainstring5
```
Python3:
```
plainstring1 = utf8string.decode("utf-8")
plainstring2 = asciistring.decode("ascii")
plainstring3 = isostring.decode("ISO-8859-1")
plainstring4 = utf16string.decode("utf-16")
plainstring5 = gbkstring.decode("gbk")
assert plainstring1 == plainstring2 == plainstring3 == plainstring4 == plainstring5
```

# Length of different string
For Chinese charactor, 

Input: 
```
unicodestring = u"哈"
utf8string = unicodestring.encode("utf-8")
gbkstring = unicodestring.encode("gbk")
for string in [
                unicodestring,
               utf8string, 
               gbkstring]:
    print(len(string))
```
Output:
```
1
3
2
```