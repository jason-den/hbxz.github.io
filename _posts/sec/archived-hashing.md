---
layout: post
title: "Hashing"
subtitle: "Sec topic -- hashing"
date: 2020-04-28 16:00:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - sec
  - hashing
---

Hashing is a process that reduces any amount of text or data into a fixed output.

A cryptographic hash has some extra properties -

The same text will always result in the same hash (deterministic)

- Its quick to compute
  > Should not be too quick to prevent brute-force method.
- It should be hard to reverse
  > Preimage Resistance - Given the hash, it should be hard to find the original message
- It's hard to find two different texts that has the same hash
- If you make a small change to the text, it will change lots of things in the hash

#### Preimage Resistance

- Given the hash, it should be hard to find the original message

hash ( ??? ) -> pzz
Can you guess what word would hash to `pzz`?

#### Second Preimage Resistance

- Given the hash and the original message, it should be hard to come up with a second message that has the same hash

hash(hill) => hll
hash(???) => hll
what word other than hill would hash to hll?

> Hint: the greeting word we use everyday?

#### Collision Resistance

- It should be hard to choose any two messages that result in the same hash

hash(worship) => wrshp
hash(warship) => wrshp

world
Using the "naive Hash" above, come up with your own 'hashed words' and post them in the comments below for us to solve.

For example, to challenge us with a

Preimage Attack : Just post the hash (e.g. pzz) and we will try to guess the word that created it
2nd Preimage Attack : Post the hash (e.g. pzz) AND the original word (e.g. pizza) and we will try to come up with another word that also hashes to to the same hash. Make sure there actually is another word with the same hash though!
Collision Resistance : Describe or give the definition of the two words (without saying which words they are) and we can see if figure out the two words. For example - 1) An alternative person during the 70s and 80s who loved peace and flowers; and 2) the word that describes you when you smile all the time. For these two descriptions the words would be : 1) hippy and 2) happy
