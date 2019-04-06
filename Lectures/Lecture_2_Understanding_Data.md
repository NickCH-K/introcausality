---
title: "Lecture 2: Understanding Data"
author: "Nick Huntington-Klein"
date: "December 1, 2018"
output:   
  revealjs::revealjs_presentation:
    theme: solarized
    transition: slide
    self_contained: true
    smart: true
    fig_caption: true
    keep_md: true
    slideNumber: true
    
---



## What's the Point?

What are we actually trying to DO when we use data?

Contrary to popular opinion, the point isn't to make pretty graphs or to make a point, or justify something you've done.

Those may be nice side effects!

## Uncovering Truths

The cleanest way to think about data analysis is to remember that data *comes from somewhere*

There was some process that *generated that data*

Our goal, in all data analysis, is to get some idea of *what that process is*

## Example

- Imagine a basic coin flip
- Every time we flip, we get heads half the time and tails half the time
- The TRUE process that generates the data is that there's a coin that's heads half the time and tails half the time
- If we analyze the data correctly, we should report back that the coin is heads half the time
- Let's try calculating the *proportion* of heads

## Example


```r
#Generate 500 heads and tails
data <- sample(c("Heads","Tails"),500,replace=TRUE)
#Calculate the proportion of heads
mean(data=="Heads")
```

```
## [1] 0.512
```
![](Lecture_2_Understanding_Data_files/figure-revealjs/unnamed-chunk-2-1.png)<!-- -->

## Example

- Let's try out that code in R a few times and see what happens
- First, what do we *want* to happen? What should we see if our data analysis method is good?

## How Good Was It?

- Our data analysis consistently told us that the coin was generating heads about half the time
- That is describing the true data generating process pretty well!
- Let's think - what other approaches could we have taken? What would the pros and cons be?
    - Counting the heads instead of taking the proportion?
    - Taking the mean and adding .1?
    - Just saying it's 50%?
    
## Another Example

- People have different amounts of money in their wallet, from 0 to 10
- We flip a coin and, if it's heads, give them a dollar
- What's the data generating process here?
- What should our data analysis uncover?

## Another Example

```r
#Generate 500 wallets and 500 heads and tails
wallets <- sample(0:10,500,replace=TRUE)
coin <- sample(c("Heads","Tails"),500,replace=TRUE)
#Give a dollar whenever it's a heads, then get average money by coin
wallets <- wallets + (coin=="Heads")
aggregate(wallets~coin,FUN=mean)
```

```
##    coin  wallets
## 1 Heads 5.889328
## 2 Tails 5.020243
```
![](Lecture_2_Understanding_Data_files/figure-revealjs/unnamed-chunk-4-1.png)<!-- -->
