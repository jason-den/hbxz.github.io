#### Problems with passwords

- People forget their passwords, so any system that relies on passwords has to have a password recovery mechanism, and it's rare that that's as strong as the password mechanism.

- - The process of recovering the password is quite weak and someone can fake that system.

- Passwords are not random collections of letters. They are actually meaningful in some way to the person because people forget them. So they try and pick ones that they won't forget. 

- - If you try and rely on the semantics of the language, there's much less entropy and less viable passwords. 
  - So people have password lists, lists of possible passwords that people might use, and this password generation engines that just combine these lists in different ways to try plausible passwords.
  - Brute forcing normally finds weak passwords quite quickly. 

- The right number of people to know a secret is 0. 

- - If someone else knows the secrets, they could tell someone else.
  - Passwords are always being stolen and lost.
  - Data breach

- People often reuse passwords in multiple systems.

- - Never use a password more than once.

- The hash of the password

- - Jumble the origin password up in some way and store the jumbled up password, which is called the hash of the password. 

  - Hash function

  - Store the passwords as hashes. When data breaches occur, attackers will only have jumble of passwords. 

  - - Attackers need to unjumble the password: brute forcing
    - This makes it harder to uncover the key.

- Data breach

- - A data lake is a system or repository of data stored in its natural/raw format, usually, object blobs or files.
  - Just lie about the information in case a data breach happens.
  - Breach happens all the time.

> Password, anything good?

| Advantages                                                 | Disadvantages                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Decouples secrets from the system                            | People create passwords with common phrases. Attackers exploit this |
| Classical design; There are plenty of libs for developing a web application with this authenticatio method. | People often reuse passwords in multiple systems. A breach for a user in one system can result in a breach in another because of this. |
|                                                              | People tend to forget the passwords, and the system to recover password is much easier to crack |

#### Password Cracking

A system that uses passwords decouples secrets from the system. Passwords integrate the key and secret. If one key is compromised, the system is not necessarily undermined.

Companies usually store the passwords as hashes. When data breaches occur, attackers will only have jumble of passwords. This makes it harder to uncover the key.

> But if you don't add salt, attacker can just Google the hash and get many of the original text (the password!).



> How to not store your password - Tom Scott

<iframe height="400" src="https://www.youtube.com/embed/8ZtInClXe1Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



### How to choose a good password?

#### NIST 800-63 [2019 password guidelines](https://pages.nist.gov/800-63-3/sp800-63b.html#sec5):

- 8 character minimum when a human sets it
- 6 character minimum when set by a system/service
- Support at least 64 characters maximum length
- All ASCII characters (including space) should be supported
- Truncation of the secret (password) shall not be performed when processed
- Check chosen password with known password dictionaries
- Allow at least 10 password attempts before lockout
- No complexity requirements
- No password expiration period
- No password hints
- No knowledge-based authentication (e.g. who was your best friend in high school?)
- No SMS for 2FA (use a one-time password from an app like Google Authenticator)