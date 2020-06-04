---
layout: post
title: "Bits of security: what it is and how to calculate"
subtitle: "Brute force is not the only force!"
date: 2020-05-02 12:54:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - Foundation - security
  - Bits of security
  - UNSW 6441
---

#### Bits of security

### what it is

“Bits of security” is just an easy way of measuring things. In the security industry, it's the way we discuss how much 'security' a particular system has - or more specifically, __how much protection there is against a "brute force" attack__.

For many systems, there can be billions of possible keys or passwords to brute force, and it can be hard to talk about those large numbers easily. 

For example, the total number of possible keys for AES-128 is 340,282,366,920,938,463,463,374,607,431,768,211,456 unique keys.

That is a very large number! And it's very hard to communicate easily. There are some other ways of representing that (some easier than others) ... 

- Words : 340 undecillion 282 decillion 366 nonillion 920 octillion 938 septillion 463 sextillion 463 quintillion 374 quadrillion 607 trillion 431 billion 768 million 211 thousand 456
- As an approximation : 340 undecillion
- As a power of 10 : 3.4028237e+38 or 3.4028237 x 1038
- As a power of 2 : $2^{128}$

- As 'bits' : 128

You can see that the last option ('bits') is one of the easiest way to represent the number. When we are using 'bits' to measure security, we call it 'bits of security'.

You can also probably see that 'bits of security' is related to the fourth option "As a power of 2", and that the bits of security is simply the exponent (the 128 part) of the power of 2 calculation. This is because most computer security algorithms are based on binary, so a counting system with a base of 2 makes a lot of sense! 

### How to Calculate Bits of Security

1. Find the total number of permutations (ie total number of possible passwords, keys etc).
2. Find the nearest power of 2 number (ie. 1, 2, 4, 8, 16, 32, 64....)
3. Convert the into exponential form, with a base of 2. 
    (e.g. 2 -> $2^1$, 4 -> $2^2$, 8 -> $2^3$ ... 128 -> $2^7$ ...  1024 -> $2^{10}$ ... )
4. Take the exponent value - that is the number of bits of security

> Formula

Bits of Security = $log_2$ ( total number of permutations )

Commonly used numbers and their 'bit' equivalent : 

- 1000 ≈ 1024 = $2^{10}$
- 1 million ≈ $2^{20}$
- 1 billion ≈ $2^{30}$



### examples/practices

#### Q1 - My padlock accepts 3 digits. How many bits of security are there?

1. Number of permutations : 10 x 10 x 10 = 1000
2. The nearest power of 2 number : 1024
3. Exponential form of 1024 = 2 ^ 10
4. Exponent = Bits of security = 10

There are 10 bits of security. 



#### Q2 - On average, how many bits of security would it take to brute force the padlock?

An attacker may guess the key correctly on their first guess, or they may get it correct on their last guess... but on average, they will guess correctly half way through the total number of pins. 

Hence number of permutations to brute force ON AVERAGE is : 1/2 x 1000 = 500

1. Number of permutations : 0.5 x 10 x 10 x 10 = 500
2. The nearest power of 2 number : 512
3. Exponential form of 512 = 2 ^ 9
4. Exponent = Bits of security = 9

The average bits to brute force a system will always be one less than the total bits of security. This is because every time you increase the bits of security by one, it has the same effect as multiplying by 2, and every time you take away a bit of security, it has the effect of dividing by two. 



#### Q3 - In the attacker's worst case scenario, how many bits of security would it take to brute force the padlock?

In the worst case scenario, the attacker has to try all of the 1000 pincodes, which is 10 bits, so the worst case scenario bits of security is 10 bits.



#### Q4 - If the attacker can do 2 bits of work per minute (ie test 4 combinations a minute) - how many minutes will it take to brute force the padlock? 

> Give your answer to nearest power of 2 number.



The question doesn't stipulate if it is the worse case scenario, or the average case, so I will assume the average case. 

Attacker can guess 4 pins per minute : 

4 pins / minute = 2^2 pins / minute = 2 bits of work / minute

Number of minutes to brute force the padlock : (1000 pins) / (4 pins/min) = 250 min

or using bits: (10 bits) / (2 bits/minute) = 8 bits of minutes = 2^8 minutes = 256 minutes

Since the question for the answer to the nearest power of 2 number, I take the calculation based on bits.... 256 minutes.

Since the question implies AVERAGE brute force time (not worst case) I halve the time required... (Equally I could have just used 9 bits instead of 10 in the calculations above).

Average time = 0.5 x worst case time = 0.5 x 256 minutes = 128 min 

Final answer : 128 minutes



#### Guessing a sentence per letter, letter given after wrong answer:

> There is redundancy in English (to say many less letters) 
>
> Let's say, there is only 1 bit of information per letter in English language

​	**The supreme art of war is to subdue the enemy without fighting.*

> This was done in class. The mate made it by 31 right guesses, 31 wrong guesses

Attackers will try to bruteforce the sentence? (62 letters)



This is always measured in bits of security or work instead of time, this is because the amount of work required to brute force something will always be constant. If we measure in time, this can vary due to the improvements in CPU architectures providing us better times but not does not describe the amount of work required to break a password. 



How much work will the attacker have to do?
 62 bits worth of work, $2^{62}$ combinations

$2^{10}$  ≈ 1,000 

$2^{20}$  ≈ 210 * 210 ≈ 1,000 * 1,000 = 1,000,000

$2^{62}$ ≈ 1 followed by 6 lots of 000 = 1 000 000 000 000 000 000 - 1 quintillion combinations



How long will it take us to try all 1 quintillion combinations?

Assume speed of computer is 4 gigahertz, giga is billion, 

4GHz ≈ 4 * $2^{30}$  = $2^{2}$  * $2^{30}$  = $2^{32}$ 

Assuming it takes  $2^{7}$  operations to try one combination

Can try  $2^{32- 7}$   =  $2^{25}$  combinations per second

If we have 8 cores on computer, we can try   $2^{3}$  *   $2^{25}$  =   $2^{28}$  passwords per second

This would take   $2^{62-28}$   = $2^{34}$ ≈ 16 * 10$^9$ seconds or about 544 years to crack. ($2^{62}$ total combinations)









What if someone has a mining rig with tons of GPUs?

Assume they have 1000 computers each with about 1000 cores

Would then take $2^{62}$/$2^{25}$ / $2^{10}$ / $2^{10}$ = $2^{17}$  = 131,072 seconds ≈ 36 hours





### more

we measure the amount of work it takes to brute force something in bits (i.e. in a log base 2 scale) exploiting space / time tradeoff can roughly halve the effective number of bits.estimate of how many bits of security to get a few months of security from different types of hackers: ![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/M4J9fmtxRKRgoEfxY7igUmVNtMsrxVqd9csv2wiUESGjjGLkTZWl8mhSohDq8KvXnbyV6Merq4NdQYwEL9e7bOvJSjKNqwPTjQxDh5TSY3o0uLSiZ5VcMCwN5sbskJuN-ySyeSsj-20200504211049200.png)


