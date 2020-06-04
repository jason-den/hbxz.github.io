---
layout: post
title: "Course content review -- Cyber Security"
subtitle: ""
date: 2020-05-02 12:54:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - Foundation - security
  - review
  - UNSW 6441
---

> 05.02 plan to do
>
> - ~~week 1 A~~, week1 B; week 2;
> - [exam center checking](https://www.openlearning.com/unswcourses/courses/sec-2020/exam/); 
>   - see the useful link and dummy exam there.
>   - try dummy exam decryption
> - ~~change blog fav-icon~~

### Week 1

---

> Summary

Terms

- mind of attacker vs mind of defender ; Asymmetry
- Vulnerabilities - many different types

- A confirmation bias is a type of cognitive bias that involves favoring information that confirms your previously existing beliefs or biases.
- Separation of powers: if you give one body the authority to control everything they will abuse it.

mi

- Analysis: what it is and how to do it

Vulnerabilities 

> inclusion attacks: LFI, RFI

- LFI -- Local File Inclusion 
- RFI - remote File Inclusion

---

#### Case study -1- False security across the Mooney Mooney bridge

Driving across the Mooney Mooney bridge, it is possible to be supremely, maybe naively confident in its safety. Why can it be easy for us to be so confident about this?

1. You don't have many options. It's kind of a risk that you have to bear. Considering all low possibillity risks that you cannot do much is distractive and distructive.

   > If you don't trust this bridge, there might be one or two more roads that can lead you to your destination, but that's it. On the contrary, you might have dozens of similar online services to pick.

   > Similar to the risk of car accident when you go out for grocery. You just don't have that many choice; it's kind of unaffordable to control that risk.

2. Bridges are designed to work under normal workload (the cars, wind, sea wave) and some possible disasters (earth quake with limited level), these can be calculated beforehand and keep a safety margin. While a terrorist suicide bombing or level-15 earth quake are normally not in scope and it cannot defends.

> more discussion from class

2. Many other cars have driven across it without any incident - but why do we do so? Think about the Deep Water Horizon, or volcano eruptions, or a lot of catastrophic events, where sometimes it really is the first time (even with low probability).
3. We trust the engineers that build it - but what makes an engineer so special? Is an engineer’s financial interest, responsibility for their actions, difficulty to reach accreditation and competency enough? At the end of the day, we find it difficult to make devices which are even secure.

#### mind set -- attacker v.s defender

> “There’s an asymmetry of attack and defense.”

> “Everything is flawed, every solution has flaws.”

| Attacker                                                            | Defender                                                                              |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Only need to attack 1 channel                                       | Need to defend all channels                                                           |
| Finding flaws in a system                                           | Defending can breed complacency; (Difficult to criticise yourself or your own system) |
| black box; (most of the time; except insider-attack or open source) | white box; have more information; (most of the time)                                  |

#### Defender complacency

When you pay a lot on the defence, or even worse, you build the defence, it's tempting to boast the features and be complacent with what you have.

But attackers only need to find one vulnerability.

##### physical security

Without physical security, cyber security isn’t necessary. Social engineering and stealing can be much more efficient techniques to obtain the information you want.

> Book recommendation ‘The Art of Deception’.
>
> I heard of it long time ago, it still sleep in my someday list. Wish it good sleep.

Physical access = game over

E.g. Attackers infiltrated a firm's office cleaners, granting physical access which was used to complete the attack.

#### Case study -2- internet mailing list

> from a past exam question

An example of how easy passive data collection can be, just from what you post - Internet mailing list post was flagged as SHA-245, poster mentioned he was relatively new to cryptography, and was asking about sending encrypted messages. When approaching a question like this, instead of focusing on his incorrect usage of protocols, focus instead on the vulnerabilities in the context such as:

- Sending a message from his company email address about sending information
- He demonstrated he knew nothing about cryptography, suggesting it would not be - implemented properly
- He also shared about the strategy he was using

#### Discussion - how do you erase data?

Removing physical traces of critical information is harder than you think

Conventional methods such as shredding and burning may not work as thoroughly as we hoped for.

> In movie [Argo](<https://en.wikipedia.org/wiki/Argo_(2012_film)>), children labor was used to reconstruct the shredded paper documents.

Buckland suggests disposing of different parts of sensitive documents in different locations and different times.

#### Difference between passive recon and active recon

- Active reconnaissance: it involves being present on a target network or server, leaving a trail in the hacker's wake
- Passive reconnaissance: computers and networks are still targeted, but crucially without actively engaging with the systems or infrastructure. Subsequently, few clues are left which lead back to an IP address.

  - Dumpster diving is an example of passive recon.
  - A typical passive recon is to get access to the target’s old computer and try to find some useful info or data from it.
  - While doing passive recon, untraceable is important.

- Fiber optic cables leading to potentially confidential data centers

#### case study -3- Halifax Explosion

> Largest man-made explosion before atomic bomb. 16th December 1917, in the port of Halifax. It caused a tsunami that destroyed a native Indian island nearby.

Two ships were sailing towards each other. Tooting at each other due to miscommunication about which lane they would like to take, they both swerve out, then swerve in, then bump along their ship’s metal cladding, which causes a spark. The crew quickly rowed into the town of Halifax, warning them to escape.
Patrick Coleman, a train dispatcher, initially running away from the town, ran back to the train station where there was an approaching train to the town. He sent messages which alerted the train of the incident and prevented the casualties of the 300 passengers onboard. After the explosion, his messages (sent prior to the explosion) also helped mobilise aid quickly, such that there were available empty trains at the station ready to move patients to the hospital.
Here, on the surface fault might have been laid on the ships’ miscommunication, but a deeper look into the root cause would reveal that - the town of Halifax was probably to blame for the severity of the incident. Had there been protocol for dealing with a ship in the harbour on fire (either by putting it out or alerting people to flee), there would have been much less casualties.

> It turns out a great predictor of whether people evacuated or not was what their neighbours chose to do.

You are in charge of the inquiry of the follow-up. What are your top 5 precise, concrete recommendations for the City of Halifax? What are the most important things to do? Prioritise recommendations in order.

> What's wrong; What can be improved; Justification;



> ### BS
>
> #### History of Hacking
>
> - 200,000 BC - Homo Sapiens
> - 1970 - Phreaking, universal ideas, Asleep at the Wheel
>   in band - John Draper - 2600Hz
>   https://www.youtube.com/watch?v=8lN4TSslz-0
>   Complexity
>   Out of spec
>   Easy hacking eg my first hack
>   2000 - Value O (Microsoft Money 1994, millions of users in US)
>   200? - Complex Cells 2005?/7?9? Stuxnet
>   2005- Specialisation - Gold hats
>   Now - Can't be asleep anymore
>
> 
>
> 







####  Local File Inclusion (LFI) Vulnerabilities

> What it is:

- https://dzone.com/articles/what-is-local-file-inclusion-lfi

> protection

The best way to eliminate Local File Inclusion (LFI) vulnerabilities is to avoid dynamically including files based on user input. If this is not possible, the application should maintain a whitelist of files that can be included in order to limit the attacker’s control over what gets included.

#### Remote file inclusion (RFI)

> What it is:

- https://www.imperva.com/learn/application-security/rfi-remote-file-inclusion/
- https://www.acunetix.com/blog/articles/remote-file-inclusion-rfi/

> protection



### week 2

#### The problem of security

- Mixing data and control: When both data and control messages are transferred on the same stream, allowing for the risk of data messages being interpreted as control messages, which enables malicious attackers to control the system.

- Asymmetric nature of attacker vs defender: The defender has to cover all points of attack but has a sort of herd immunity. Once an attack is seen then every other defender is aware of it and is thus immune to it. Attackers only need to successfully attack a single point but can only succeed once with any given attack due to herd immunity. E.g. Attacking a bank, the back detects the attack, then bank tells all the other banks, the attack is rendered useless
  - Hubris: Thinking like a defender
  - Out of spec: Programmers write secure systems to comply with a spec. Attackers can bypass security simply by creating behaviours that aren't defined in the spec.
  - Weakest link: You’re just as strong as your weakest link (as good as your weakest security measure)

- Abuse of trust: Security is all about trust. As soon as you trust something (e.g. a certificate-chain) an attacker has the opportunity to turn your trust against you

- Human Weakness: Most issues come from human error (to some degree?)





#### Type I and Type II Errors

![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/ERHrr65U0AAcq78.jpeg)

There will always be unintended consequences as a result of a change. This can be because it was overlooked during the formation of the change or because the system incorrectly classifies people (and there is not much you can do about it - edge cases)

Examples:

- Police pursuit: Police in Britain will not enter a high speed pursuit with people riding on motorbikes if they are not wearing a helmet for fear of them getting injured or dying. The unintended consequence was the emergence of criminals not wearing helmets to avoid the police. 

- Refugees: 
  - A refugee comes to a country and needs help -> gets kicked out
  - A refugee comes to a country and doesn’t need help -> can stay in country 

Note that, positive/negative depends on context.

For example, "A refugee comes to a country and needs help but gets kicked out" can be considered as `false positive` in context of `fraud detection`; but you can also say it's a false negative in context of `refugee legitimacy validation`.

> Type 1 type 2 error - attempting to reduce one increases the other



#### Weakness of the Week - Gullibility

• People are very easy to trick! Think about how people can be tricked and why they can be tricked. (Multiple reasons such as laziness, embarrassment, respect for authorities/hierarchical organisations/uniforms, confidence of the opponent, lack of information, greediness)

• Simplifications and shortcuts, if everything is in spec then everything is ok. If an attacker then exploits this they will be overlooked by others. Generally it is too much effort to analyse everything.

• Eagerness to believe something can override the use of intuition and/or logic.

• If you trust someone, you are more likely to believe them or follow along with them (and disregard your own opinions/inhibitions)

• Example: Has your credit card been stolen? Enter it here to see if you’re right.

• Tailgating: sometimes referred to as piggybacking, is a physical security breach in which an unauthorized person follows an authorized individual to enter a secured premise. Tailgating provides a simple social engineering-based way around many security mechanisms one would think of as secure. Humans will tend to let it happen since they don't want to stop people. This is why mechanical systems exist.





#### Social Engineering

- What ways are people trickable? How can people be trained not to be tricked?

- Case study: The Chasers at APEC 

- - People can be tricked by pure confidence
  - security was looking “outwards” - told not to look at motorcades
  - met expectations

- Case study: The Chaser’s Trojan Horse
  
  

- Your biggest threat is usually in

- People make poor decisions when they’re in a hot state - i.e. flustered, stressed, off balance etc.

- People follow the decisions made by others before them.

- Negotiators get people in the habit of saying yes. If they have already done one thing, they are more likely to do things to keep helping you.

-  Get people started. Have something that people can agree to at the beginning like who sits where? Just get people in the habit of saying yes and then you can ask harder and harder questions and they will eventually say yes.

- High vis vest can get you anywhere! Appearances and claims to authority.

- Recommended Reading: The Art of Deception is a book by Kevin Mitnick that covers the art of social engineering

- Homework - find some examples





#### Case study -- Movie 12 Angry Men

There is a focus in the movie "12 Angry Men" on the careful balancing act of type 1 and type 2 error. The movie begins with a focus on reducing the error of letting a guilty man go free and ends on reducing the error of sentencing an innocent man to death. It is also seen that throughout the movie, the quality of the test for such errors are also increased, which is rare to see.

Relating the reason of having a jury to security terms, it is to reduce a single point of failure in the judge by having independent people act as a cross section of society. It is also an attempt to reduce bias, especially confirmation bias which is seen in the last character to yield who had preconceived notions of young murderers due to some memory associated with his son.

The ambiguous end of the movie where we don't find out what the verdict demonstrates to us, thinking from a security perspective, that there will always be something to be improved on, as defenders get better, so too will attackers.

"Security will never be settled."

> Buckland - Somehow at every point, I was persuaded

 

##### Having a Jury -- pros

Avoiding Single point of failure (SPOF)

- Reduces chance of someone being unfairly convicted

- Reduces corruption possibility

  > Reduces individual corruption impact. 
  >
  > > Cause bribing half of them is harder & more dangerous than bribing just one person. Chance of having an informer is far higher.
  >
  > But, it increase the chance of individual corruption.
  >
  > > Cause finding a week point in 12 ppl is easier than finding one in one person.

- Cross section of society to reduce bias

- You have to be so sure that you can convince other people

- Legal system that errs on the side of innocent until proven guilty

Over the film - improvement of quality of test 

Having a Jury -- cons

- Cannot guarantee there is 12 independent checks every time

- Picking the jury!! White male dominated, one of low socioeconomic background

- Jury doesn't do what they're supposed to do

- - Philosopher - strength of the system, cannot always trust the judge entirely



### week 3

---

- Secret
- CIA properties



#### CIA

> Confidentiality, Integrity, Authentication

- Confidentiality: making sure nobody between point A and B can read what is being sent
- Integrity: making sure nobody between point A and B can alter the information being sent
- Authentication: making sure point A knows that they are talking to the right point B

  

> - I
>   - Can I do something that people can't change?
> - A: Authentication
> - How to verify someone is who he/she claims to be?



> - put cryptographic primitives together to build cryptographic systems and protocols
> - It becomes the foundation of cryptography. 
> - I.e. these forms the “primitives” of cryptography upon which everything is built.



##### Confidentiality

- How can I transmit a secret from one person to another without losing the secret?

- Steganography = hiding that the secret exists

- Sent message - cipher text, decoded message - plain text

- Code - is where words are replaced with other words

- - e.g. Caterpillar has entered the leaf = Pope has entered the Vatican



#### Information Theory

- How to measure information?
- Measure information in bits
- How much information can I extract from 1 question? 
- If questions each produce an answer with 1 bit of information, you can add those bits cumulatively to know the knowledge of the system
- How much information is there is something e.g. Is a picture worth a thousand words??? A picture will always have more information than a thousand words describing that picture
- SKILLS NEEDED: Need to convert from decimal to binary, know your doubling and rough estimate
- One word - 15 bits (or 32,000 words); In a 1000 words = 15000 bits (2^15,000 sentences)
- Most pictures are megabytes - way bigger than this



#### Brute Force Attack

- If you could brute force the password, it would take you 1000 years. So the system is really safe. 

- - Wrong! The missing bits of logic: maybe there's a faster way of getting at the brute-forcing.
  - It is very rarely the fastest way of breaking anything.
  - But just because it can't be broken by brute-forcing it doesn't mean we can relax and feel happy.

- Put the secret into a key

- The keys can be changed easily.

- It’s easy to give everyone different keys.

- Once a system is based on a key, one way of breaking it is to try all possible keys. (Brute Force Attack)

- The only thing about it is it takes time. The weakness of a brute force attack is it is slow.

- Pretty much every system is vulnerable to a brute force attack on the key.

- So when you increase complexity, you're not making something impossible to hack, you're just making it impossible to break quickly. 

- On average, will guess correctly half way through the total number of possibilities

> The following topic has been moved to become an individual posts. Check them.

#### Secret

#### Bits of security

### week 4 - humnan factors; cipher

> - Hashes and MACs
> - co-incidence index
>
> ---
>
> Castles



#### case 1 -  Castles

- Castles are a place for people to be safe

- - Continued building castles better and stronger

  - The gates are very hard to defend

  - The weakest part of the castle are the walls

  - - The weakest part of the wall are the corners as the stress concentrates in these areas
    - Hard to get to the corners so they are not that well defended and thus easier to attack
    - To stop people attacking the base of the wall they made walls overhang, then built towers in the corners to keep tops of the walls safe.

  - But everything inside the walls is vulnerable, reliant on the outer wall.

  - - "M&M theory of defence"

  - Next defense level of internal walls at different tiers - concentric castle

- Krak des Chevaliers

- - The castle fell because someone let them in
  - Forged the letter from the head of the church to let them in
  - Classic example of Social engineering being used
  - Weakness wasn't the castle but the weakness was from inside

> Trusted People ranked by occupation.
>
> What's wrong with the banks in Europe?
>
> ![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/s9F-sL0nZX2YkjDEkpvjHZYlq-2-sYnBK-ErfvgesI258Q0UmGn2btkJagvLvjUJorJVfSB9wN_gUofyl9gCMKtFtw39xMNVFtIu-GDhumT3r6b4SmMKgJxZSKpAiwUifMCedGqc.png)

#### Insider Threats

- Insiders are a bigger threat.

- Insiders are in a very privileged position.

- Insider attacks always happen recently.

- Insider attacks are the most feared attacks. 

  > E.g. Google set up insider teams to look after insider attacks.

- We never want to admit the existence of this problem.

- People who have higher authority often pose a bigger problem for insider threats as they are both less suspected as well as have a higher overview of everything.

#### Defense in Depth

- Defence in depth = the need for multiple components to fail in order to compromise the system.

  > number of defence layers

- One of the solution to SPOF (single point of failure)

- Limits scope of disaster

- e.g. Concentric walls in a castle 

- - Second walls limit the scope of the disaster as a mitigation technique

- e.g. bulkheads in submarines

#### Interest conflict

> People are assumed to look after themselves

- Self-interest and organisation interest conflict is insidious. 

  > In Snowden's case, it's self-safety+organisation's interest v.s public constitutional right.

- It happends everywhere and all the time. 

  > I would say, misalignment is normal. Alignment of local and global interests requires careful design and continuously maintenance.

- That's the problem we've got with insiders: they have a duty to the organization, and they also have a duty to themselves.

##### Examples - Double Agents

- British double agents are motivated by idealism and think socialism was good

- American double agents motivations were hard to work out Eg: money, power

- Double agents are usually made because of their values, greed, power, ideologies

- Double agents usually do these to keep themselves safe:

- - Staying anonymous
  - Setting up a dupe
  - Establish a secret code
  - Find an escape route
  - Prove your loyalty
  - Expose every mole on every other side

##### Examples - Snowden

- Ex CIA employee, an insider who leaked NSA secrets with respect to his duty to the public, conflicting with his duty to NSA or personal safety

##### Examples - Chelsea Manning

- Worked for US Army, came across atrocities and war crimes and eventually leaked her knowledge
- She disclosed to WikiLeaks nearly 750,000 classified, or unclassified but sensitive, military and diplomatic documents.
- Collateral murder: kill the innocent civilians

##### Example: Stealing clients from colleague.

- It hurts the trust. 

  > As a result, sales men/women need to spend time to watch over their "enemies".

- But it's tempting for most sales men/women because clients means sales KPI, thus, money. 

- Lot's of CRMS (Client Relations Management System) put effort to help this. But I don't think it is a problem can be fully solved by software alone.



#### Whistleblower 

- Are a particular type of inside attack
- Someone who (anonymously) gives away sensitive information
- Tend to give away information when they aren’t powerful 
- Motivated by moral code or financial incentives
- Values conflict with the duty to their organization
- Big consequences for whistleblowing 
- Powerful people try and lockup and keep the person who leaked the information (the whistleblower)



#### Examples of Whistleblower 

- Andrew Wilke - ONA Iraq War based on a lie (WMD)

- My Lai Massacre - Thompson

- - blew the whistle on it
  - Landed his helicopter and told the soldiers to stop killing people
  - Tried to keep women and children safe in his helicopter

- Afghan War Documents Leak

- - Military wanted to keep these documents very secret
  - Someone inside smuggled these documents out
  - Civilian Deaths

- Afghan Files

- - Australian troops killing unarmed men and children

- East Timor - Witness K

- - Witness K revealed the bugging operation in 2012 after learning Foreign Minister Alexander Downer had become an adviser to Woodside Petroleum, which was benefiting from the treaty.
  - The identity of Witness K must be kept secret under the provisions of the Intelligence Services Act and any person in breach of this could face prosecution.

Exercise - document 1 whistleblower whose actions mean something to you, what motivated them, how successful were they, how could they have done it better, what lessons learned, what changed?



#### **Human Weakness** - greed corruption, moral hazard, self interest

**Corruption**

- Always going to happen

- "Good" corruption exists too

- - e.g. police doing favours to protect their friend



#### Ciphers

- Nomenclature 

  > Can lead to confidentiality through a shared secret


##### Symmetric cipher

Symmetric algorithm uses the __same key__ to encrypt data as it does to decrypt data.

> For example, a symmetric algorithm will use key _k_ to encrypt some plaintext information like a password into a ciphertext. Then, it uses *k* again to take that ciphertext and turn it back into the password.



##### Polybius cipher

- “Prequel” to a cipher
- Turn the big alphabet to a smaller alphabet
- Change in the lexical representation of a message
- In jail, in the pipes try and knock to exchange messages
- A very old Cipher 
- Example: below works by replacing each character with its coordinate on the square e.g. ‘A’ -> ‘11’

￼![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/2lUDDqI5QkyZ2Hj6b8QTiPeCsvqjDotIccrTdxhZnCYeJ5FJzLp2yfFzeHh-Ufgr1FaI8eiqxGvwCKbaCXRv3BK2nq8MhB-dJ8-mssoRoBJbk4tkXRINz26Gb2hScXUrE72JkzF--20200507145853984.png)



##### Substitution ( and Vigenère cipher )

Taking the letters and changing them into a new oneCan substitute one letter with two letters instead (diagrams), increase entropy

**Vigenère cipher**

26 * 26 Substitution Cipher which uses different substitution code book for every letter. Shifting each letter differently.

> Video for vigenère cipher -- encryption and decryption: 

<iframe width="560" height="315" src="https://www.youtube.com/embed/SkJcmCaHqS0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



<iframe width="560" height="315" src="https://www.youtube.com/embed/LaWp_Kq0cKs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/8p3XBpfoESQcvvvMMqKTkSAuA0c14EabH-6bFCctZFA4bUGUWdARUVMZ8yQh0cH_5Eo-IlHH64_gytpIg_Z_Ahd2NviWMejqCEB3SVSN_Yt2_RwBk5SRzypIOSKf8I57sniVCeEV.png)


> E.g If the code is “APPLE” : HIGH => HXVS    
>
> H	I	G	H        
>
> A	P	P	L	E  
>
> H	X	V	S

![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/xPhJz2uxhOIuAL5s-ncxeLQtCgxjQ6t-4U3SaphqJ3gasWu8LE15MLZgJzqL7JdteuNYhoGvY1ujkx6ZDZ_TruvfJdjE0FJxRnUhzf_ynJgUKTdSwPL7DTzJzNh9-a4dAWdpe7rx.png) 

##### Transposition cipher

Leave the letters the same, permute the order (simple transposition) E.g: Words backward![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/lLYjJA-wPRIqMTzfcnMw3xjNUZ0DrYyxll8egJeFBpevJua2xUoRE_NSQrveGIvR8TDlzr4HdmKMRot0Sr5yQZEGT5HG0tbOKBTVH3h2vAxvLb23dtgYNtklyN5CqrQww17U_cvd.png)![img](https://lh6.googleusercontent.com/hscmnVHGNLjVN73OtwUC1NL3ccaotE1lQJbno6lXHux5UTLPGp6Ijn1Uo4iODg_sr2fhFx1idG9dFvc3-DXjcfzgJTGBtcz0AhkoVG5DG4nqE7N2JHwYiV904dt4eHlAboWsIMLx)







#### [DES; Block vs stream cipher](https://hbxz.github.io/2020/04/28/AES/)



- use of XOR In cryptography

> the simple XOR cipher is a type of additive cipher, an encryption algorithm that operates according to the principles:
>
> ![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/cptqnbzshS33rBYPM2i0c66cafwF8FsvKZqqcxAqcCHl7n_HMy6GqhCodaBuDIVAtsDlDaed9QqcrHmIr9OkOcIuqiq3kEzy1UmsYxIb1eBKTZSZV94jGtAQy_YQyl5SFB5_bpn8.png)



**Coincidence Index** 

> Early way for people to work what language the message was inThe frequency distribution for letters in a language is the same no matter the text



##### OTP

- A one-time password (OTP), also known as a one-time pin or dynamic password, is a password that is valid **for only one login session or transaction**, on a computer system or other digital device.
- Advantage:
  - comparingt to static passwords, it's **not vulnerable to replay attacks**. 
  - A second major advantage is that a user who uses the same (or similar) password for multiple systems, is not made vulnerable on all of them if the password for one of these is gained by an attacker. 
- A number of OTP systems also aim to ensure that a session cannot easily be intercepted or impersonated without knowledge of unpredictable data created during the previous session, thus reducing the attack surface further.



**Confusion and Diffusion (Shannon)** - Wikipedia blurb below:

- Confusion

  > key-ciphyertext connection blurring

- - Confusion means that each binary digit (bit) of the ciphertext should depend on several parts of the key, obscuring the connections between the two.
  - The property of confusion hides the relationship between the ciphertext and the key.
  - This property makes it difficult to find the key from the ciphertext and if a single bit in a key is changed, most or all the bits in the ciphertext will be affected.
  - Confusion increases the ambiguity of ciphertext and it is used by both **block and stream cipher.**

- Diffusion

  > Avalanche effect of plaintext-ciphertext

- - Diffusion means that if we change a single bit of the plaintext, then (statistically) half of the bits in the ciphertext should change (sometimes called Avalanche effect), and similarly, if we change one bit of the ciphertext, then approximately one-half of the plaintext bits should change. Since a bit can have only two states, when they are all re-evaluated and changed from one seemingly random position to another, half of the bits will have changed state.
  - The idea of diffusion is to hide the relationship between the ciphertext and the plain text.
  - This will make it hard for an attacker who tries to find out the plain text and it increases the redundancy of plain text by spreading it across the rows and columns; it is achieved through the transposition of algorithm and it is used by **block cipher only**.



### week 5

---

- Authentication
- hashing
- password 
- one time pad

---

#### Authentication

> Unsolvable in a perfect sense and very hard, very important

- - Straddles both the virtual world and the real world

- How do you make sure the person sending you a message is the person you think they are?

- How do you authenticate people in real life?

- - You know something specific about the person - face, voice, behaviours

  - - Defeated by: 
      - genetically identical
      - **impersonation** through acting and makeup

      - not being able to see them properly

      - expecting to see a particular person

  - Shared secret/knowledge

- How do you authenticate people as a computer?

  - Computer is like a person who sits in a dark room and only receives information through bits of paper shoved in through a hole and can send information out
    - Can't see or hear or smell anything

  - This person that you can't see and aren't connected to in any way is saying that they are someone. Are they?

    - Not a fair question to ask a computer because all they know about is data and computation - can't prove something that's outside the system

- Man in the middle attack

  - Don't have to understand what's going on, you can just use the data sent from one end to authenticate
    - E.g. Americans sent a ping with a challenge to determine if the ship was American or not.
    - Russians forwarded the challenge to an American ship, listened to the reply and sent it back to the Americans

- Factors of authentication

  - What you know

    - Secret
      - e.g. password

    - Issues:

      - Hard to keep secret
      - Can be guessed
      - People forget

  - What you have

    - E.g. credit card
    - Piece of technology

    - Issues:

      - expensive
      - hard to understand
      - normally defended by obscurity

    - Has to be turned into data by a transducer before being sent to the computer

    - Don't need a card to attack the system, can just inject information into the data being sent to the computer

    - Basically just a secret

  - What you are

    - Just another secret - information that is converted into data and stored as a hash

    - Issues: 

      - You can't change if it's stolen and thieves will have it forever 

        > e.g. can’t change fingerprint.

    - **Biometrics are no better than a secret but are more convenient**

      - Easier to trick, make mistakes both ways
      - Bought for the obscurity because it's a fancy bit of technology

        - Buy the technology because you want it to solve all your problems so you imagine that it did

- Type 1 and Type 2 error - authenticate the wrong person or fail to authenticate the right person



- End to end security
  - Goes from the real world, through the computer and then back into the real world

- - Can't make only some of the channels secure because then someone will just attack the weaker channels.

- Problem with authentication is that one of the ends is in the real world and one of the ends is in the computer world



##### 2FA

2 factor isn't actually 2 factor authentication - **just one factor (secrets)**

- Smartphone 2 factor authentication with a banking app on the phone means that it's the recipient of the SMS message and running the software - only need to compromise **one device**

#####  Authentication of websites through PKI

- Infrastructure which involves digital certificates based on hashing

- Rely on being able to develop new hashes to keep the internet up

- MD5, SHA0, SHA1, SHA2 and now SHA3 which all work on the same principles



#### Command and Control

- Nuclear weapons created to assert dominance over the enemy. But what are the risks?

- Accidental mistakes can be devastating:

- - Broken Arrows: Accidents involving nuclear weapon, 32 have occurred since 1950, examples include:

  - - Thule 1968: B52 crashed near Thule air base, onto sea ice in North Star Bay, Greenland causing the nuclear bombs to detonate, resulting in radioactive contamination. The contaminated areas had to be dug up and stored away safely.
    - Dropping the bomb example.
    - US military was more concerned about nuclear bombs being misused (accidentally, or intentionally, as seen in Dr Strangelove), rather than the enemy using it against them.

- These accidents above prove that nuclear weapons are not being looked after properly.

- Command and control = a situation in which managers tell employees everything that they should do, rather than allowing them to decide somethings for themselves.

- - e.g. Nuclear bombs cannot be launched without the approval of the president.

- Kennedy wanted the American nuclear arsenal to be safe and under his control. 

- - Poorly-gaurded lone jet in Turkish airfield armed with nuclear weapons.
  - One of the domes containing nuclear weapons were guarded by only one soldier (armed with a bolt action rifle).

- How could the president enforce command and control when there are mistakes, accidents and people doing stupid things? How can we design a nuclear bomb to be safe, but also detonate when we want it to (what if it hits the ground but does not detonate)?

- - Weapons Safety: What does it take for the bomb to go off? 

  - - No single point of failure resulting in the bomb going off
    - Balanced with using these weapons in a war, the bombs actually do go off.
    - Type 1 and type 2 errors.

  - Bomb pin code: nuclear weapon only detonated when president releases a pin code to the military personnel.

  - The president could be sure that the bomb would not go off without their approval. 

  - Would only work if the bombs all had different pin codes when in reality, they all had the same pin code, therefore, this was a poorly executed mechanism.

##### command and control: One person has absolute control over everyone else.

Example of command and control: Generals command army, army will follow command unquestioned upon request by the general. E.g. if the general says attack hill, soldiers attack hill. This gives the general enormous power, as long as soldiers follow orders without question, but what if the soldiers said no, or can we do it later? This will compromise command and control.

Command and control follows a **pyramid structure**, where the person on top commands the people below them and “has the strength of one million people”. But the person on top still only has the brain of one person (their brain). 

Strengths:

- Ability to work in unison
- Suitable to times of crisis when control is needed

Weaknesses:

- Could lead to the rise of dictators
- Single point of failure on the person at the top



##### Power structure B: Everyone has equal power or power is split amongst many small subgroups

Strengths:

- Allows for more brain power than command & control
- Allows individual creativity
- If one person becomes corrupt, others can keep them in check

Weaknesses:

- Harder to come to an agreement



When someone takes power, they want to keep it and to advance their aims. The ancient Greeks had a solution for this: by having 2 rulers with equal power. They ensured that they had conflicting interests and therefore, the 2 keep each other in check and prevent the other from gaining more power. They also ensured that the rulers could govern for no longer than 2 years.

Usually, a person in power has **checks and balances** limiting their power, e.g. laws and the constitution. E.g, they cannot appoint judges. However, once taking power, they want to undermine all their constraints. The estates, e.g. president, judiciary, public service, the media, etc are all independent of each other. If the president goes corrupt, then society would be safe (unless everything goes corrupt at once).



##### Richard Buckland Ice-example

 Richard went to buy ice-cream but the person serving told him that he must order from the counter. The person at the counter would print a receipt and hands it to Richard, who would hand it to the server. Although this may sound silly, from a security perspective, it makes sense as the 2 people are watching each other, to prevent each other from treating one of their friends more favourably, therefore to corrupt this system, you must corrupt both people. Furthermore, the person on the counter cannot steal money as it is on record (the receipt), which is then handed to the server. This is an example of double entry book keeping.

##### Double entry bookkeeping

Amount of money must be recorded in a minimum of two accounts. Both accounts need to be equal, otherwise it will indicate something is wrong. To break this system, both accounts need to be broken (dual control). This is good, as long as the process is not comprisable.

##### Dual Control

Two people need to cooperate in order to gain access to a system (data, file, device).

Dual control is good for minimising mistakes and corruption. Example in war games: during the sequence where the base was being closing off, one guy pressing the switches and another guy watches and checks them. During the sequence where the keys were turned, the keyholes were placed far apart from each other to prevent the same person from turning the keys, therefore 2 people would need to turn the keys simultaneously. Another example (a real life example) is when confirming a number, one person reads the number and the other person checks if the number is being read correctly.





#### Assets

intro example - Team America World Police. 

Although Team America stopped the terrorists, they blew up the Eiffel Tower, the Arc de Triumph and the Louvre (the main terrorist appeared to want to blow this up in the first place). 

What is it we are trying to protect? What are our assets? 

In the above example, there was only one thing Team America were carrying out (stopping terrorists), everything else was unimportant.

Should we abandon and risk losing everything else (that may be more important) just to achieve a goal?



##### How to identify Assets:

- Regularly surveying all the people in the organisation what they consider to be the assets.
- Develop a sensible plan: Have a strategy to get information from the people (they may not know or tell you what you want to know). Strategy may involve showing them a list of assets, and hearing their feedback on it (humans are very good at critics).
- Periodically revise current lists of assets.



##### What are the assets ?

- university?

Students, staff (the safety of the previous 2 are very important), reputation (if people think this university is a joke, students won’t come here), the buildings (lots of money went into building them), intellectual property, the university’s bank account, communication channels.

- Richard Buckland Syringe Example:

Richard Buckland had a syringe stuck in his throat, for refusing to give his wallet. Although he protected his wallet asset, his life asset was compromised.

- Car Doorbell

Richard Buckland’s friend had an indicator on his car when someone attempts to break in, although it can protect the car, Richard’s friend may need to fight the thieves (and put his life asset at risk).

> Better solution is keeping the window open

- Coke

Although people think their recipe is their most important assets (deliberately done to give it value), but their most important asset is the brand (an attack on them that may make them look like Pepsi would be devastating).



##### Valuing the Assets - Defining what is important

**Categorising types of assets**

- **Tangible Assets**: Those that are **easily given a value**

- - A gold chain valued at some relatively static amount
  - The jewellery in a jewellery store.

- **Intangible Assets**: These **cannot be easily and objectively be valued**

- - Employee Morale & Security
  - Customer information
  - Company secrets
  - Availability of services

- Monetary + psychological/emotional costs

- **Difficult <> Don't do**

##### Strategies for assigning values to assets

**Survey what many people think**

- no single person or group should be solely evaluating the assets;

- Examples of the information that should be gathered are as follows:

- - "How much money would you lose if this data center went down for 24 hours?".
  - "How much will you lose if your company is disconnected to the internet for 3 hours?".

**Examples**

- In assessing the value of a park
- Picasso



### week 7

#### BS

##### Information

- Information having value in itself is a fairly new concept

- Historically having information was a means to an end - didn’t have value in itself

- Identity Theft

- - When people have enough information (secrets) about you to pretend that they are you
  - It is extremely distressing, suddenly you are very vulnerable
  - Value of information > Value of all the oil reserves in the world
  - Facebook, Google, etc. make money from selling our information and data

##### Data

- The value of a piece of information increases with every extra piece of information that is known (e.g value of 100 pieces of information > value of 100 x 1 piece of information) 

- 20 questions game

- - No and yes is equally valuable if it’s cutting the search space in HALF
  - NO for “Is it a dog only” cuts out only 1 possibility
  - “Is it bigger than …” cuts out a lot of possibilities
  - From the start to the end: 2^20 possible things at the start
  - All the answers put together is worth MORE than a single answer

- __Data by itself is useless but in aggregation is useful.__

##### Open Government

- Should the government's data be accessible to the public?

- Transparency of the government’s actions and decisions

- - More scrutiny

- Naturally the government wants to hold onto power

- - Less scrutiny is better



#### RSA

**Form of Asymmetric Encryption.**
**Asymmetric ciphers:** Turning strings into numbers, and performing math upon it(a^b)^c = (a^c)^b = a^(b*c)	
Rather than getting chaos/randomness from jumbling the message, get chaos/randomness from the mathematicsBase the cipher upon a currently unsolved math problemCan be more assertive about how hard it is to crack something 

##### example

1 person works out pair of numbers

Tells everyone 1 number - to encrypt message and send to you (public key)

Keeps the other number secret that no-one can work out - to decrypt message that’s being sent to you (private key)

Keys can be used in both directions

*Plaintext = m*

*Private key = a*

*Public key = b*

*Size (?) = n*

*Ciphertext = c*



(m^a)mod(n) = c - get ciphertext from message

(c^b)mod(n) = m - get back original message from ciphertext



#### Symmetric Encryption

- When the same key is used to both encrypt and decrypt messages.

- Difficult to get key across to other party

- Would need a key for every interaction.

- If there are n people

- - You only need (n^2)/2 keys since you don’t want to double count the keys [Handshaking lemma]

#### Asymmetric Encryption

*Idea:What if everyone has a letter box that only they can unlock*

​	- You can put things in the letterbox

​	- But you can't get it out

​	- We only need to keep track of one key rather than a key for each interaction.



#### [Essential 8](https://www.cyber.gov.au/publications/essential-eight-explained)

#### read more

General Reference:

- 2 card monte reveal

<iframe width="560" height="315" src="https://www.youtube.com/embed/22oae2tciwo?start=72" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- 3 card monte reveal

<iframe width="560" height="315" src="https://www.youtube.com/embed/QJv44-Ghj_Y" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- white van scam
  - [wiki](https://en.wikipedia.org/wiki/White_van_speaker_scam)
  - [some history](https://www.digitaltrends.com/home-theater/dont-be-a-sucker-the-white-van-speaker-scam-explained/)

<iframe width="560" height="315" src="https://www.youtube.com/embed/i3B_KKyntQE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



Reference/Homework:

- [Padding Oracle Attack](https://en.wikipedia.org/wiki/Padding_oracle_attack)



### week 9

#### BS

**Is/Ought**:

- Is: What things are in the present.
- Ought: What things should be.
- Usually, people mix these two up.
- This can be applied to authentication. The ‘ought’ is what the computer perceives to be the right person. But the computer can’t see the real world so it can’t access the ‘is’ component.





#### Mitnick’s attack

- TCP handshake

- - Send chunks across the internet, reassemble chunks of data at the other end to get the full stream of data
  - Not a security protocol, just a way of doing things

1. Information gathering - by recon/observing the communications between an x-terminal and trusted server, he figured out the behaviour and sequence number generator between the two.
2. The flood - by operating a denial-of-service type of attack, with a multitude of half-open SYN connections, while acting as a trusted source, stopping the server from responding to any other requests
3. Trusted relationship hijacking - Mitnick then proceeded to act as the server and interacted with the x-terminal 
4. Remote command pump - By installing a “backdoor”, and adding his own computer to the list of trusted computers (host file), he would be able to return later without repeating the hijack attempt
5. Clean up - by sending RESET commands to the server, all the half-open SYN connections were closed and the server was free again.

#### TOCTOU attack

A race condition where a problem/attack occurs between when a resource is checked and when it is actually used.

- E.g. someone going through a macca’s drive through, and collecting an order they didn’t ask or pay for.

#### Blockchain 

- Nice solution to bitcoin problem - can we have virtual money? Because what if we can’t trust the banks?

- How can we not have to trust someone? Trust free protocols

- - E.g. someone cuts, the other chooses! puzzle: is it possible to replicate this for three people?

- We come up with a puzzle that’s hard to solve, because it takes work. I have a block/letter with information in it, to be hashed, and to end in N many 0s. What if 20 random bits are added to the end of the block ? 2^20 creates a million more possibilities that must be tested.

- But who is trusting those that write the blockchain software?

Bugs

- Check course slides for actual code
- Example 1: buffer overflow
- Example 2: memcpy gets executed because of bad scoping and indentation

#### Review

- How to hatch an egg? From Horton hears a who. 
- Horton principle: you should say what you mean, mean what you say, and check what you check. 
  - E.g. blockchain, the hash stored is the hash of the block
  - TOCTOU, don’t misalign what you’re checking 



- [ ] Homework - look up DOS, DDOS, reflected DOS
- [ ] PKI blogging
- [ ] HTTPs setting

### week 10















### Sample Exam

9. ECB; plaintext key;
10. 

- reasoning
- solving problems

calcualtions/estimate

- what about upper bound
- what about lower bound
- estimate method



