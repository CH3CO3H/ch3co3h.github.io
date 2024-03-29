---
title: 一副牌组合五
layout: post
category: study
date: 2020-03-31
mody: 2020-03-31
---

# 一副牌组合五

一副扑克牌，去掉两张王是 52 张。从中选取 5 张自由组合，符合特定模式的组合数是多少呢？

全部的组合数：
$$
\Big(_{5}^{52}\Big)=2598960
$$

## 4 个同点

13 个点数，加上任意一张牌，结果是
$$
13\times(52-4)=624
$$

## 同花顺

同花顺和下面的大顺都是指五张牌点数连续。同花顺还要再加上花色相同这一条件。由于不能循环（比如 Q, K, A, 2, 3 是不能算作大顺的），顺子的可能性有 9 个。  
花色有 4 个，同花顺的组合数为
$$
4\times9=36
$$

## 葫芦

13 个点数排列 2 （注意是排列而不是组合），再乘上花色的组合数，结果是
$$
13\times 12\times \Big(_3^4\Big)\times \Big(_2^4\Big)=3744
$$

## 3 个同点

13 个点数中选取 1 个作为 3 张相同的点数，再从剩下的 12 个点数中组合 2，三张点数相同牌的花色组合和一张牌的花色组合数都是 4 ，所以结果是：
$$
13\times \Big(_2^{12}\Big)\times 4^3=219648
$$

## 大顺

点数组合有 9 种，每张牌有 4 种花色选择，再去掉同花顺的情况，结果是
$$
9\times 4^5-36=9180
$$

## 同花小顺

小顺指五张牌中有 4 张点数连续并且不是大顺的情况。同花小顺还需满足五张牌花色相同的要求。  
花色相同时，点数组合有两种情况：连顺点数位于两端（2，3，4，5 和 J，Q，K，A）；连顺点数位于中间（有 8 种可能）。由于不能构成大顺，位于两端时余下的那张牌点数有 8 种选择，中间时余下的那张牌点数有 7 种选择。  
最后乘以 4 种花色，结果为
$$
(2\times 8+8\times 7)\times 4=288
$$
也可以这样计算：4张牌点数连续有 10 种可能，再在剩余 9 个点数里选取 1。这样选取后正好多出了大顺点数组合数（ 9 ）的两倍，因为每种大顺点数组合都被计算了两次。去掉这一数目，最后乘以 4 种花色，结果为
$$
(10\times 9-9\times 2)\times 4=288
$$
点数各不相同的小顺点数组合数为 72，下面计算小顺时会用到这一数据。

## 小顺

小顺的点数组合不能按照同花小顺的方法来计算，因为可能出现点数相同而花色不同的情况。我们按点数组合将小顺分为两种情况：小顺带一对；点数各不同。 
后一种情况点数组合数上面已给出。每张牌有 4 种花色选择，再去掉同花小顺的情况，结果为  
$$
72\times 4^5-288=73440
$$

小顺带一对，点数组合数为 4 张点数连续的 10 种可能，乘上重复点数的 4 种可能。花色组合情况，三张不重复点数的牌每张有 4 种可能花色，2 张重复点数的牌花色组合数为 4 组合 2。最终的结果为
$$
4\times 10\times 4^3\times\Big(_2^4\Big)=15360
$$
将两种情况相加，得
$$
73440+15360=88800
$$

## 两对

13 个点数组合 2，再从剩余 11 个点数中选取 1。乘上花色的组合数，结果为
$$
\Big(_2^{13}\Big)\times 11\times\Big(_2^4\Big)\times\Big(_2^4\Big)\times4=123552
$$

## 同花

13 个点数组合 5，去掉大顺和小顺的点数组合数，乘以 4 种花色，结果为
$$
(\Big(_5^{13}\Big)-9-72)\times4=4824
$$

## 一对

13 个点数选取 1 作为一对的点数，乘以剩余 12 个点数组合 3，去掉小顺带一对的情况，再乘以花色的组合数，结果为
$$
(13\times\Big(_3^{12}\Big)-40)\times\Big(_2^4\Big)\times4^3=1082880
$$

---

按顺序排列一下。

| No. | Type | Count | Rate |
| --- | ---- | ------- | -------------------- |
|1| 同花顺 | 36      | 1.38516945239634E-05 |
|2| 同花小顺 | 288     | 0.000110813556192    |
| 3 |4 个同点   | 624     | 0.000240096038415    |
| 4 |葫芦   | 3477    | 0.001337842829439    |
| 5 |同花   | 4824    | 0.001856127066211    |
| 6 |大顺    | 9180 | 0.003532182103611 |
| 7 |小顺   | 88800   | 0.03416751315911     |
| 8 |2 对   | 123552  | 0.047539015606243    |
| 9 |3 个同点   | 219648  | 0.084513805522209    |
| 10 |1 对   | 1082880 | 0.41665897128082     |