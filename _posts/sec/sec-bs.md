

## Terms to define and discuss; Glossary of concepts;

- 2FA

- - Two-factor authentication (also known as 2FA) is a type, or subset, of multi-factor authentication. It is a method of confirming users' claimed identities by using a combination of two different factors: 1) something they know, 2) something they have, or 3) something they are.
  - Multi-factor authentication (MFA) is an authentication method in which a computer user is granted access only after successfully presenting two or more pieces of evidence (or factors) to an authentication mechanism: knowledge (something the user and only the user knows), possession (something the user and only the user has), and inherence (something the user and only the user is).

- Mobile phone number Porting

- - Mobile number portability is the ability to take your existing mobile number to a new service with a new provider. 'Porting' is the act of transferring your number to a new service, either with a different network or a different provider, or both.

- Key

- - A key is data that is used to lock and unlock cryptographic functions such as encryption, authentication and authorization.

- Password

- - A password is a user created secret phrase that is used to verify identity or generate cryptographic keys.

- Brute forcing

- - In cryptography, a brute-force attack consists of an attacker submitting many passwords or passphrases with the hope of eventually guessing correctly. The attacker systematically checks all possible passwords and passphrases until the correct one is found. Alternatively, the attacker can attempt to guess the key which is typically created from the password using a key derivation function. This is known as an exhaustive key search.

- Entropy

- - Information entropy, often just entropy, is a basic quantity in information theory associated with any random variable, which can be interpreted as the average level of "information", "surprise", or "uncertainty" inherent in the variable's possible outcomes. 

- dictionary attack

- - In cryptanalysis and computer security, a dictionary attack is a form of brute force attack technique for defeating a cipher or authentication mechanism by trying to determine its decryption key or passphrase by trying hundreds or sometimes millions of likely possibilities, such as words in a dictionary.



- Complexity
  - The numbers of components in a module, the numbers of modules in a system, the numbers of abstract layers in a system.
  - You want to design something to be as simple as possible, but not simpler.
  - Any extra complexity leads to errors
- Coherence
  - Each thing in a well written/designed system has one job and one job only that you can articulate really well
  - application should have many components that do one job each really well
- Coupling
  - dependency on something else
  - a small change in one part of a system will change/effect another part of the system
  - Avoid systems that are tightly coupled
  - Decreasing coupling increases resilience
- Resilience
  - if something goes wrong the system 'degrades gracefully' rather than collapsing
  - Related to coupling in that if one thing goes wrong it won’t affect the rest of the system. 
- Single points of failure
  - A single point of failure (SPOF) is a part of a system that, if it fails, will stop the entire system from working. SPOFs are undesirable in any system with a goal of high availability or reliability
  - Don’t want multiple points of entry - means it can be attacked from multiple angles 
- DOS
  - Denial Of Service
  - A type of attack on machines or a network that makes the resource unavailable for the intended user, usually by flooding the machine or network with requests in an attempt to overload the system 
- DDOS
  - Distributed Denial Of Service
  - A DOS attack that originates from many different sources
- Tamper Proof
  - The computer system must not be able to be altered while operating in its intended setting
  - Don’t want people to have access to it, or to tamper with it.
- Tamper Evident
  - If something has been tampered with, show this clearly/evidently
- Supply Chain
  - A network between a company and its suppliers to produce and distribute specific product to the final buyer. 
- Malware
  - software that is specifically designed to disrupt, damage, or gain unauthorized access to a computer system
- Ransomware
  - a type of malicious software designed to block access to a computer system until a sum of money is paid.





- 

## BS

#### Defensive programming

- Designing Against an Adversary: Write your code as if you're against an 'adversary' at all times to protect against actual adversaries, as well as nature, chance, probability. 
- Proof against an adversary is proof against nature too.
- As a security designer you must focus not just on ‘inspec’ behaviour but also behaviour that is not mentioned in the spec (i.e. out-of-spec), something that a hacker will try to manipulate. Eg. the security auditor driving into the petrol station with a drop table as a licence plate.
- Don’t take chances: assume ‘the adversary will align the holes.’

#### Failure & Complexity

- things fail because they are complex and things will keep failing because we will keep writing more complex things
- As languages evolve, many layers of abstraction (from machine code to high level code) have been created; resulting in high levels of complexity.
- The lack of distaste on complexity marks a novice.

#### Physical control:

  - physical is everything. If you don’t have physical control, you don’t have anything. But in some cases its unavoidable for example: The person that makes your phone and puts the parts together has physical control and it is basically impossible for you to build a phone from scratch so you have to trust that they haven’t done anything to the device. 
Snowden leaks revealed an arrangement between Amazon and NSA. When an NSA target purchases electrical equipment from Amazon, the package is intercepted by the NSA. Hardware is installed onto the product and backdoored. Package arrives on time and hence does not arouse suspicion.
supply chain: things that occur before considering security
  - counterfeit: Physical things can also be counterfeited, not only the digital. Like money.



#### history of cyber

-        Old days there wasn’t much to do, not many computers and they weren’t really connected to anything important and people were trying little things. There was no incentive to hack. A lot of people used to store recipes and create games.
-          Year 2000, Microsoft came out with a product called Microsoft money and you could use that to do banking. Computers connected to money are like oxygen so people became interested in hacking so you can get the money. All different techniques and strategies appeared everywhere.
-         The image of a lone hacker in their basement etc etc is not really true representation anymore, more about criminal gangs rather than hacking away as a lone hacker. (Now, very little hacking is done by hackers and little kids. Most of it is now happening in organisations in crime. Cyber is now the fifth domain of war. Nation states and the military are getting involved now.)
-        Next phase is specialization. Someone writes a dropper to deliver it to the target person ,someone who works out how to collect money, creating the virus and so on. It's now possible for an organisation to launch an attack.They had the skill to assemble and hire people who can do all the bits and all those bits available on the internet for money so you don’t even physically need to assemble anyone. Basically hacking started happening everywhere.



#### Anatomy of typical attack

- Reconnaissance - discovers vulnerability level

  > aka recon

- Vulnerability is exploited

- Once an attacker is in the system, it’s approximately 200 days the attacker spends inside the system

- Zero day: Vulnerability that the owner doesn’t know about aka “O-Day”

- If you had an 0 day for an apple iphone, you wouldn’t use the vulnerability unless you had to. Because every time you use it, there is a chance someone will find it and tell Apple who will fix it. So you waste a whole lot of money in buying that vulnerability. 

- Always use the lowest level of attack if you get an O-day! You want to minimise the possibility of someone else discovering that vulnerability

- Most successful entry for an attack = HUMANS!

- Diverges from stereotypical Hollywood portrayal (massive complex endeavors - in reality, discretion is often achieved through simplicity)

**Example and how it escalates**: 

Suppose someone is targeting a medium corporate and they want to get something. The attacker does some recon and finds a particular person and gets details of them in the company. They send them a targeted letter. Spearphishing email (only for one person). The person opens the email and does something like click on the link, download a document, look at a pdf etc. That’s all it takes. Now they are compromised. The attacker comes in and gets access to their machine. From their machine they either privilege-escalate up that machine or send emails to other emails to do other things. It is called pivoting, moving from one machine to another, to a high level of privilege on a machine. Then they get into the network and it's done. They might want persistence, like when the machine is turned off or if someone tries to get rid of them, they are still able to stay in.

#### Recommended Reading:

- The Art of War, Sun Tzu

- **“Against the Gods”** (Arthur Randolf; rocket scientist): **“The real world provides you with a leaky valve. It is up to you, how much leaking you can tolerate”** - Essence of *risk*

  



- Type 1 / type 2 errors
  - Results that are out of bounds eg. False positives
  - reducing one type of error will increase the other type of error
  - no-one really knows how to reduce both errors
  - Want to aim to REDUCE type II error (?????? please correct this if wrong) over type I error
- Want a balance or middle ground of reducing both type I and type II errors, and understanding that both can occur
- Depends on the situation if one type of error is prioritized over the other. 
- Type I (False positive): rejection of a true null hypothesis as the result of a test procedure (e.g. convicting an innocent defendant)
- Type II (False negative): failure to reject a false null hypothesis as the result of a test procedure (e.g. acquitting a criminal



- price of vulnerability

![img](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/5dhq5sI3C9AwdgC2gFiqsF1KgFJqPMtHo_JTOV-HhsYY5WcDxFADY3WGPxpz2o5ZGiWergqffUbfG9smSdzEW9wVEa1jS9JkdH5y-hBHAfSxciEm-uhm_9NdOxs5Mes2POTSXrjO.png)



#### Security names

**Information :** Flow of information/properties of the information, focus on the CIA-triad (confidentiality, integrity, authentication - main objectives in the security world).

**IT-Security:** Not as applied as the other two (but very similar otherwise).

**Cyber-security:** Applied Information security -> securing things that are vulnerable through ICT.



#### the insiders

Read about (why they did it, what and how they did it, how they got around the mechanisms that would prevent breaches, how were they discovered):

- [Oleg Gordievsky](https://en.wikipedia.org/wiki/Oleg_Gordievsky) 

- - Who? A Russian who gave British inside info after rising to a senior position!

  - What? Leaked secrets: 

  - - Averted a potential nuclear confrontation with the Soviet Union, when NATO exercise [Able Archer 83](https://en.wikipedia.org/wiki/Able_Archer_83) was misinterpreted by the Soviets as a potential first strike!
    - Identified [Mikhail Gorbachev](https://en.wikipedia.org/wiki/Mikhail_Gorbachev) as the Soviet heir-apparent long before he became publicly important.

  - Why? He became disillusioned with the KGB after the [Soviet invasion of Czechoslovakia](https://en.wikipedia.org/wiki/Warsaw_Pact_invasion_of_Czechoslovakia). Afterwards recruited by MI6.

  - How discovered? [Aldrich Ames](https://en.wikipedia.org/wiki/Aldrich_Ames) leaked his name back to the USSR!

  - Outcome? Smuggled out of Russia after interrogation.

- [Aldrich Ames](https://en.wikipedia.org/wiki/Aldrich_Ames)

- - Who? Former Central Intelligence Agency officer turned KGB double agent.
  - What? Leaked secrets to USSR after gaining access to all CIA operations in Russia.
  - Why? Financial gain first, then kept going as he could never “go back”.
  - How discovered? After people suspected his extravagant lifestyle with his new money, an investigation uncovered him.
  - Outcome? Sentenced to prison for life, responsible for the deaths of agents.

- [Klaus Fuchs](https://en.wikipedia.org/wiki/Klaus_Fuchs)

- - Who? A German theoretical physicist and atomic spy.
  - What?  Supplied information from the American, British, and Canadian Manhattan Project to the Soviet Union during and shortly after World War II. 
  - Why? A communist himself, he idealised Russia and their views.
  - How? Communication through a courier so he wouldn’t have to travel.
  - How discovered? The [Venona project](https://en.wikipedia.org/wiki/Venona_project) indicated to [GCHQ](https://en.wikipedia.org/wiki/GCHQ) that Fuchs was a spy. Possibly tipped off Kim Philby!
  - Outcome? Served nine years and four months of his sentence (as then required in England where long-term prisoners were entitled by law to one-third off for good behaviour in prison) then emigrated to the [German Democratic Republic](https://en.wikipedia.org/wiki/German_Democratic_Republic).

- [Kim Philby](https://en.wikipedia.org/wiki/Kim_Philby)

- - Who? British intelligence officer, double agent for the Soviet Union and a member of the Cambridge Five. Quite the resume!

  - What? Leaked info!

  - - Leaked an [Anglo-American plot](https://en.wikipedia.org/wiki/Albanian_Subversion) to subvert the [communist regime of Albania](https://en.wikipedia.org/wiki/People's_Socialist_Republic_of_Albania)
    - Tipped off two other spies under suspicion of espionage, [Donald Maclean](https://en.wikipedia.org/wiki/Donald_Maclean_(spy)) and [Guy Burgess](https://en.wikipedia.org/wiki/Guy_Burgess), both of whom subsequently fled to Moscow in May 1951.

  - Why? Possibly recruited (along with other Cambridge 5) at university of cambridge during studies. (reason below)

  - How discovered? The defections of his fellow agents cast suspicion over him (1951), then he was exonerated (1955), but FINALLY pinned down as a double agent. (1963)

  - Outcome? Defected to Russia, where he lived out the rest of his life.

- [Cambridge five ](https://en.wikipedia.org/wiki/Cambridge_Five)

- - Who? A ring of spies in the UK that passed information to the Soviet Union during World War II and in the early stages of the Cold War.
- What? Leaked info to USSR from 1930’s to 1950’s.
  - Why? All of the five were convinced that the [Marxism–Leninism](https://en.wikipedia.org/wiki/Marxism–Leninism) of [Soviet Communism](https://en.wikipedia.org/wiki/Soviet_Communism) was the best available political system, and especially the best defence against the rise of [fascism](https://en.wikipedia.org/wiki/Fascism). Recruited by Russia as a result.
- How discovered? 
  - - After [Donald Maclean](https://en.wikipedia.org/wiki/Donald_Maclean_(spy)) and [Guy Burgess](https://en.wikipedia.org/wiki/Guy_Burgess) disappeared due to Philby’s tip-off, Philby was soon under suspicion.
  - Philby defected after being discovered in 1963
    - Anthony Blunt was revealed by [Michael Whitney Straight](https://en.wikipedia.org/wiki/Michael_Whitney_Straight), someone he had unsuccessfully tried to recruit into the spy ring.
  - [John Cairncross](https://en.wikipedia.org/wiki/John_Cairncross) (1913–1995) confessed to spying in 1951 and was publicly accused of being the "fifth man" in 1990. He was also accused by Anthony Blunt during Blunt's confession in 1964.
  - Outcome? Each one avoided prosecution. Some defected, some lost jobs, but none went to prison.



#### Never roll your own

Never invent your own cryptography, you will get it wrong.



#### The Tragedy of the Commons 

- Back then everyone used to graze in this common area so on and so forth, and then land ownership came about and everyone wanted to own it! 

- The left-over lands were known as the common but there was so little; it was fixed. 

- - Maybe fine for every family to have one goat 
  - If one family gets two goats, then it's not too bad. That family gets TWICE the happiness, but the **cost is shared across everyone!** 

- The land of the commons was bound to fail because someone does the self-interested thing. 



 

#### On Electrical Boxes

- You could easily open the electrical box from outside. It's all based on public trust.  

"There are two things in particular that I can't say because they're such a vulnerability they have such impact and scale. So think about the impact" 

- I'll tell you in the party we'll have at the end of the term. 

- There was a famous attack carried out, and he made a book called 'Takendown', where he caught Kevin Mitnick about how he caught Mitnick. But the thing that's funny is why he caught Mitnick. 

- - Mitnick knew that this guy was after him (Tsuoto)) 
  - The night before Christmas day he did the attack. Why? 
  - Because everyone was away on Christmas. There'd be no one to stop him. 
  - No one is expecting anything. 
  - a.k.a SUN TZU! 

- When's the best time to attack a company?  

- - **During a merger! --> distracted. New employees.** 

  - **Bankrupt --> everyone's sad and doesn't care** 

  - **Corona Virus --> if you were an APT, you would attack during weak periods such as this**. 

  - - People are buying new equipment, etc. 

- It's like the Bangladesh Bank Heist! 

- - Everyone should know about this! 
  - It's like that Bangladesh Bank Heist. They hacked the bank, arranged transfers the day before a public holiday, from their money in the US. The day after there was a public holiday in the US. They took advantage of the banks not being able to communicate over those days 

- **Ross Henderson** is like the Father of Cyber Security 







#### Books:

- Command and control 

- - Inspired the creation of Docker 

- The right stuff - Tom Wolfe

- - About the ability to think rationally in a situation of crisis

- Frames and mindsets

- - People discussing the chicago fires

- 5 days at memorial

- - About hurricane katrina’s aftereffects 

- - 