---
title: 双注输入法教程
category: study
layout: post
---

# 双注输入法教程

「双注」的含义为「双拼」+「注音」，即指此输入法兼有类似注音输入的切音法与双拼输入法的便捷性。此输入法在全拼的基础上加以改动，修正了全拼中我个人认为有问题的点，实际使用感受为学习时间短，输入效率高。希望大家都能来尝试并提出意见。

全拼中的韵母 ü 在本文档中的表示以及输入的键码均为 v。

本输入法有如下设计：

1. 去掉声母 y, w，在双注输入法中由 i, u 代替。将 yu 还原为 v。

2. 如果声母的发音与汉字相同，去掉拼音中多余的韵母。如下所示。
   
   | 全拼   | 双注  |
   | ---- | --- |
   | bo   | b   |
   | po   | p   |
   | mo   | m   |
   | fo   | f   |
   | de   | d   |
   | te   | t   |
   | ne   | n   |
   | le   | l   |
   | ge   | g   |
   | ke   | k   |
   | he   | h   |
   | ji   | j   |
   | qi   | q   |
   | xi   | x   |
   | zhi  | zh  |
   | chi  | ch  |
   | shi  | sh  |
   | ri   | r   |
   | zi   | z   |
   | ci   | c   |
   | si   | s   |
   | yi   | i   |
   | wu   | u   |
   | yu   | v   |
   | yuan | van |

3. 改写全拼中的某些韵母，使其更加符合发音规律。
   
   | 全拼         | 双注   |
   | ---------- | ---- |
   | iu         | iou  |
   | ui         | uei  |
   | (j,q,x)un  | ven  |
   | un         | uen  |
   | in/yin     | ien  |
   | ing        | ieng |
   | (j,q,x)u   | v    |
   | (j,q,x)uan | van  |
   
   如果 un 的声母为 j, q, x，则其改为 ven，否则改为 uen。另外将 ju, qu, xu 还原为 jv, qv, xv。

4. 将多个字母表示的韵母分配到单个按键。
   
   | 全拼  | 双拼  |
   | --- | --- |
   | ai  | d   |
   | ao  | c   |
   | an  | j   |
   | ang | h   |
   | ei  | w   |
   | en  | f   |
   | er  | r   |
   | eng | g   |
   | ou  | z   |
   | ong | s   |

5. 将 zh, sh, ch 也重新分配键位。
   
   | 全拼  | 双拼  |
   | --- | --- |
   | zh  | y   |
   | ch  | e   |
   | sh  | w   |
   
   使用双拼的人应该很熟悉这种分配。经此操作，一个发音只需按一个按键表示，但同一个按键可能表示多个发音。可通过以下汉字辅助记忆: "谁(shei)更草菅分走送代航"。当然"谁"字的正确拼音是 shui，双注输入法键码为 wuw。

若要开启超级简拼模式，取消 wuhyu.schema.yaml 中 speller/algebra 的以下项的注释：

```
- derive/^([bpmfdtnlgkhjqxzcsyewiu]).+$/$1/
```

经此操作后，即可用单个汉字键码的第一个按键表示全部由此码开头的字。比如输入「卧虎藏龙」不必输入 `uohuchls` 而只需输入 `uhcl`。

我尝试过使用 abbrev 指令，但不知为何并不生效。

最后，我们试着用双注输入一段汉字。

```
理性就像贞操，失去了就不会再有；只要碰上了开心的事，乐观还会回来的。
——王小波《积极的结论》
```

以上汉字的输入码位如下：

```
li'xig'jiz'xih'yf'cc, w'qv'l'jiz'bu'huw'zd'iz; y'ic'pg'wh'l'kd'xif'd'w, l'guj'hd'huw'huw'ld'd.
uh'xic'b<j'j'd'jie'luf>
```

符号 `'` 用于码位间的分隔，实际输入时都可以忽略。