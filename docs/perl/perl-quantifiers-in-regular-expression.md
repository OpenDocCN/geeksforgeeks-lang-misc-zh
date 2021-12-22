# Perl |正则表达式中的量词

> 原文:[https://www . geesforgeks . org/perl-正则表达式中的量词/](https://www.geeksforgeeks.org/perl-quantifiers-in-regular-expression/)

Perl 提供了几个正则表达式量词，用于指定在匹配完成之前给定字符可以重复多少次。这主要用于将要匹配的字符数未知的情况。

**Perl 量词有六种类型，如下所示:**

*   ***** =这表示组件必须出现零次或更多次。
*   **+** =这表示组件必须出现一次或多次。
*   **？** =这表示组件必须出现零次或一次。
*   **{n}** =这表示组件必须出现 n 次。
*   **{n，}** =这表示组件必须至少出现 n 次。
*   **{n，m}** =这表示组件必须至少出现 n 次且不超过 m 次。

**量词表:**
以上所有类型都可以用这个表来理解，这个表有包含量词的正则表达式和它们的例子。

| 正则表达式 | 例子 |
| --- | --- |
| **/Ax*A/** | **AA， Axa， AxxA， AxxxA， .....** |
| **/Ax+A/** | **Axa， AxxA， AxxxA， .....** |
| **/Ax？A/** | **AA，AxA** |
| /ax { 1，3}A/ | **Axa， AxxA， AxxxA** |
| **/Ax{2，}A/** | **AxxA， AxxxA， .....** |
| **/Ax{4}A/** | axx xxa |

**我们来看一些举例说明这些量词的例子:**
**例-1:** 在本例中， ***** 量词用在正则表达式 **/Ge*ks/** 中，该表达式产生“Gks”、“Geks”、“Geeks”……等等，并与输入字符串“Gks”匹配，因此给出“Match Found”作为输出。

```
#!/usr/bin/perl 

# Initializing a string 
$a = "Gks";  

# matching the above string with "*"
# quantifier in regular expression /Ge*ks/
if ($a =~ m/Ge*ks/)   
{  
    print "Match Found\n";  
}  
else
{  
    print "Match Not Found\n";  
}  
```

**输出:**

```
Match Found
```

**示例-2:** 在本例中， **+** 量词用在正则表达式 **/Ge+ks/** 中，该表达式生成“Geks”、“Geeks”、“Geeks”等，并与输入字符串“Gks”匹配，因此给出“匹配未找到”作为输出。

```
#!/usr/bin/perl 

# Initializing a string 
$a = "Gks";  

# matching the above string with "+"
# quantifier in regular expression /Ge+ks/
if ($a =~ m/Ge+ks/)   
{  
    print "Match Found\n";  
}  
else
{  
    print "Match Not Found\n";  
}  
```

**输出:**

```
Match Not Found
```

**例-3:** 在本例中，**？**量词用在正则表达式中**/格？ks/** 产生“Geks”或“Gks”，并与输入字符串“Geeks”匹配，因此给出“匹配未找到”作为输出。

```
#!/usr/bin/perl 

# Initializing a string 
$a = "Geeks";  

# matching the above string with "?"
# quantifier in regular expression /Ge?ks/
if ($a =~ m/Ge?ks/)   
{  
    print "Match Found\n";  
}  
else
{  
    print "Match Not Found\n";  
} 
```

**输出:**

```
Match Not Found
```

**示例-4:** 在此示例中， **{n}** 量词用于正则表达式 **/Ge{2}ks/** 中，该表达式生成“Geeks”，并与输入字符串“Geeks”匹配，因此给出“Match Found”作为输出。

```
#!/usr/bin/perl 

# Initializing a string 
$a = "Geeks";  

# matching the above string with {n}
# quantifier in regular expression /Ge{2}ks/
if ($a =~ m/Ge{2}ks/)   
{  
    print "Match Found\n";  
}  
else
{  
    print "Match Not Found\n";  
} 
```

**输出:**

```
Match Found
```

**示例-5:** 在此示例中， **{n，}** 量词用于正则表达式 **/Ge{2，}ks/** 中，该表达式生成“Geeks”、“Geeeks”、“Geeeks”等，并与输入字符串“Geks”匹配，因此给出“Match Not Found”作为输出。

```
#!/usr/bin/perl 

# Initializing a string 
$a = "Geks";  

# matching the above string with {n, }
# quantifier in regular expression /Ge{2, }ks/
if ($a =~ m/Ge{2, }ks/)   
{  
    print "Match Found\n";  
}  
else
{  
    print "Match Not Found\n";  
}  
```

**输出:**

```
Match Not Found
```

**示例-6:** 在此示例中， **{n，m}** 量词用在正则表达式 **/Ge{1，2}ks/** 中，该表达式产生“Geks”和“Geeks”，并与输入字符串“Geeks”匹配，因此给出“匹配未找到”作为输出。

```
#!/usr/bin/perl 

# Initializing a string 
$a = "Geeeks";  

# matching the above string with {n, m}
# quantifier in regular expression /Ge{1, 2}ks/
if ($a =~ m/Ge{1, 2}ks/)   
{  
    print "Match Found\n";  
}  
else
{  
    print "Match Not Found\n";  
} 
```

**输出:**

```
Match Not Found
```