## Hashes, MACs and length extension attack

### Hashing



- Hashing 

  - A 'regular' hash function is described as any function that can easily be used to convert data of **any size** down to data of a **fixed size**. 

- - Use hashing to give us random access in data structures where sequential access or structured access is too slow
  - Summarises the entire file
  - Often used for integrity

- Function - one input, one output

- - Output doesn't have to be the same size - want to convert a big amount of data into a small amount of data

  - - Used as a fingerprint (unique to users)

    - Used to check that something is the same - hasn't been changed (**integrity**)

    - - Compute the hash before and after and compare
      - Causes **avalanche effect** - one bit of change in the input changes about half the bits in the output

  - Hash function isn't a secret

- Hash collision - two inputs give the same output













### Cryptographic Hashes



A '***cryptographic*** hash' function is a hash function (also known as digests, or fingerprints) which also has the properties of being :

1. difficult to **reverse**

   > - Preimage attack - being able to figure out the file from the hash
   > - To be resistant 
   >   - can't find a preimage with less than the amount of work needed to brute force a hash
   >   - Given a hash, you can't work out the file in a feasible amount of time
   >   - Amount of work for brute force - normally half the size of the hash space


2. rare Hash collision

   > unlikely that any two messages will have the same hash. 

Ideally a cryptographic hash displays a property called the '[avalanche effect](https://en.wikipedia.org/wiki/Avalanche_effect)', wherein if an input is changed slightly (for example, flipping a single bit), the output changes significantly (e.g., half the output bits flip).

![Cryptographic_Hash_Function](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/Cryptographic_Hash_Function.png)



People like to think as cryptographic hashes as a form of key-less encryption, but cryptographic hashes have two key (excuse the pun) differences :

1 - A hash always results in the **same length output**
2 - it should not be possible to **reverse** a cryptographic hash 

**Common Hashing algorithms**

Some common forms of crypto hash are : [MD5](https://en.wikipedia.org/wiki/MD5) (old & broken), [SHA-1](https://en.wikipedia.org/wiki/SHA-1) (slightly broken), [SHA-2](https://en.wikipedia.org/wiki/SHA-2) (standard), [SHA-3](https://en.wikipedia.org/wiki/SHA-3) (future standard).



### MACs - Message Authentication Codes

As its name implies, it is a way authenticating and providing integrity to a message, [usually by using a cryptographic hashing function](https://crypto.stackexchange.com/questions/6523/what-is-the-difference-between-mac-and-hmac). 



This might be useful if you are sending a message across the internet but you want to ensure that people know the message **comes from you**, and **has not be altered**. 

>   That is, authentication & integrity

Hashes can be used to detect changes - but the concern with just using a hash to provide integrity, is that a bad guy could change your original message, AND **alter the hash** as well! Recipients would have no way of determining that the message had been tampered with.  

>   Hence the need for **MACs**. 

A MAC takes the message, combines it with a key, and then hashes the result. The new Message Authentication Code is then send along with the message. To verify to author and integrity of the message, the recipient only has to re-perform the MAC on the original message, with **the same shared secret**, and verify that the MAC matches the one sent with the transmission. A bad guy may be able to change the message, but they will not be able to recompute the MAC, as they do not know the shared secret. 

The **structure of a MAC** is critical to its security. It's not sufficient to simply perform the following: 

*   **MAC = hash(key | message)** - vulnerable to a **length extension attack**
*   **MAC = hash(message | key ) -** If collisions occur, Mallory can still forge messages
*   **MAC = hash(key | message | key)** - Also problematic!

Go out and find the best practice for the structure of MACs that is not vulnerable to the attacks above. 



### Question

A bank has invented a new way of turning a message into a number - called a CDC code, and uses this as part of a process to verify messages with so called VERIFY codes.

The bank authenticates and protects the integrity of its messages by computing a VERIFY CODE which is the CDC code of `{password, message}` I.E. The CDC code of a secret password with the message appended to then end of it.

The Bank sends the resultant VERIFY CODE along with the message (but does not send the password of course!) All messages each day use the **same password**.

Below is how a CDC code is computed:
Start with the first character of the message, convert it into a code using the following table (only some values shown)

```
{{{
 A->23
 B->47
 I->397
 L->507
 O->581
 P->635
 R->687
 U->763
 Y->901
 0->405
 1->73
}}}
```

Then multiply this by 521, mod it by 10,000, add 450, mod it by 967, then add in the code for the next character, and repeat...
For example the CDC code for the message "AU" is 216.
Working:

```
{{{
 'A' 23x521 = 11983
 mod 10,000 = 1983
 +450 = 2433
 mod 967 = 499
 +763 'U' = 1262
 x521 = 657502
 mod 10,000 = 7502
 +450 = 7952
 mod 967 = 216
}}}
```

You have intercepted the following messages and VERIFY CODES:

```
{{{
"PAYBOB100" has VERIFY CODE of 481
"BILLBOB1000" has VERIFY CODE of 573
"PAYROB1000" has VERIFY CODE of 301
}}}
```

What is the VERIFY code for `PAYBOB1000` ? 

Spoiler allert: hint & answer is 10 lines later.











#### Hint

It's a typical "length extension attack". You already have the VERIFY CODE of `PAYBOB100`, and you want the VERIFY CODE of `PAYBOB1000`, which is `PAYBOB100` and `0`.

Utilise the `"PAYBOB100" has VERIFY CODE of 481`, and add a `0` on it.

Follow the process already shown above and that's a good practice to feel this hash function.







#### Answer

I wrote a simple `JS` function and run it in `node.js`: 

`const hash = v => ((((v*521) % 10000 )+450) % 967)`

Then `hash(481+405)` gives me `122`. That's the answer.





### Merkle-Damgard Construction  -- and the Attack

> Merkle-Damgard Construction

- Take the first x number of bits alongside an initialisation vector, and put them through a function that outputs the same number of bits
- Take the next x number of bits, put it with the output and put it through the function
- Iterate - rehash

> attack

- Just change the hash

- Need to authenticate the sender through a shared secret

  - Hash the message with a secret word (Message Authentication Code) in the beginning
  - Send that hash and the message so an attacker can't change it as they don't know the key
- Length extension attack - add extra bits at the end of the message and hash it
  - Extension must be in its own block - use padding (message + padding + extension)
  - Rehash with the hash key given and the extension - will pass the MAC check without having to know the MAC







### solution to length extension attack

BTW to solves the length extension attack you can use HMAC

![image-20200417230224696](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/image-20200417230224696.png)



>   According to [HMAC wikipedia](https://en.wikipedia.org/wiki/HMAC) which refers to [RFC 2104](https://tools.ietf.org/html/rfc2104).
>
>   HMAC: hash-based message authentication code

Also recommend this video 

<iframe width="560" height="315" src="https://www.youtube.com/embed/wlSG3pEiQdc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>









### Summary and take-away

Hashing vs Encryption

1. Non-reversible
2. Fixed length
3. Non-keyed

secure hash function usually means (for a function 𝐻)

- Preimage resistance: Given a value ℎ, it is hard to find a message x so that ℎ=𝐻(𝑥)h=H(x).
- Second preimage resistance: Given a message x, it is hard to find a message x′≠x such that H(x)=H(x′).
- Collision resistance: It is hard to find two messages $x$, $x′$ such that H(x)=H(x′).

**1st Preimage Resistance**

Given small thing, hard to get big thing.

E.g. assume we have a bad hash function called adam_hash, which takes away all vowels from original input. For example, adam_hash(“pizza”) = pzz.

To attack the hash using the 1st preimage, we ask “can we reverse pzz and find the original input?” Yes, it’s not hard to reverse it and find “pizza”. 

 

**2nd Preimage Resistance**

Given small thing and big thing, hard to find another big thing that hashes to same small thing

E.g. using the same example above, we ask “can we find another word that can be hashed to the same output?”. Yes, “piazza”. adam_hash(“piazza”) = pzz. 

 

**Collision Resistance**

Hard to find two large things that have same small thing.

E.g. collision is always possible, collision resistance asks us to evaluate the collision distribution. We don’t want a biased hash function. For example, if Facebook uses a super biased hash function to store our passwords’ hash value but this hash function hashes 99% different passwords to the same hash value, it’d be so easy to login other’s accounts. To evaluate collision resistance, we ask “is it easy to find a collision?” Using the above example, hash(“it”) = hash(“to”) = hash(“at”) = hash(“tee”)...

 

Hashes give MACs - gives INTEGRITY (and also authentication)



**More on Hashes:**

- Schneier says hashes should behave like a random function. E.g. when hashing something, they should look random and there should not be any link between the message and the hash. Therefore, if you find any non randomness to a hash function, it is essentially broken.
- Brute forcing hashes. If a hash function has 2^100 possible keys (100 bits of security), it should take 2^99 possible keys to brute force (on average, you will find the key halfway through the total list of possible combinations (2^99 is half of 2^100). If it takes less than 2^99 bits of work, then this hash function is broken.
- Birthday Attack: If you have n possible birthdays , it takes the square root of n people on average to get a match (e.g. 100 people, hence it will take 10 people to get a collision). This has implications to hashing: how long until you have two different messages with the same exact hash, therefore hashes need to be collision free. If we have a 100 bit hash, it should take 2^50 hashes until we find a collision (square root of 2^100).