---
layout: post
title: "Zero-Knowledge proofs"
subtitle: "Hey, where is the basic trust, bro?"
date: 2020-04-30 16:00:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - security
  - zero knowledge proof
  - sudoku
  - protocol design challenge
---

> Today I learned about **Zero-Knowledge proofs**. In the name of the Feynman Technique, I want to share my understanding here. Wish you can have fun and gain something!

## Zero-Knowledge proofs

### what it is

Let's see the illustration from my favorite guys. I also provide summary after it.

<iframe width="560" height="315" src="https://www.youtube.com/embed/HUs1bH85X9I" frameborder="0"         allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> Some digest:
>
> - It's a privacy enhance tech that you can have both privacy and enjoy the tech.
>
> - He provides several good examples:
>   - validation for online voting without revealing who you vote for.
>   - proving the poker card is red by showing the complete set of black cards.

Here is my understanding.

There are two parties, let's name them: **K**, the secret-keeper, and **V**, the secret-verifier. Zero-knowledge-proof is such a scenario:

K can **prove** to V that K has a **secret**, and some **property** about it, **without** letting V knowing any other details of this secret.

> In another way of saying: proving the existence and some properties of a secret while hiding other details of this secret.

He mentions three criteria of Zero-knowledge-proof:

To prove so, K makes an achievement that can be achieved if and only if his claim stands.

- correctness
  - V can verify this achievement, that it is not a fake one.
- soundness
  - the impossibleness of making such achievement while the claim is false.
- zero knowledge about the real secret
  - V cannot retrieve any other information about the secret from this achievement.

> Okay, when I wrote these three rules, I reckon I don't quite know the `diff correctness soundness`. Let me go to the re-learn process and come back to you.

> Okay, enough for these wordy and fuzzy. Let's get the idea by doing.

### Challenge --- sudoku solution proof protocol

Come up with your own zero knowledge proof to prove that you have solved a `sudoku` puzzle.

- without revealing the solution to the other person.

- post your protocol in the comments below.

> However, unlike in the video, your solution must be able to be implemented in a **software program** - that is to say it should use cryptography and maths instead of any physical means.

So "cutting papper" or "putting it in your pocket" does not fit here.

Spoiler allert --- My solution is list following. Welcome to “dissect” it and let me know my bugs!

### Jason's protocol

#### 1. In running environment, export an key for encryption and decryption, named `KEY`

#### 2. Present the puzzle of suduku as a 9\*9 matrix of numbers, named `pzzl_matrix`, such that:

- `pzzl_matrix[i][j] = 0` if `(i+1)`row and `(j+1)`col in puzzle is empty,
- `pzzl_matrix[i][j] = x` if `(i+1)` row and `(j+1)`col in puzzle is `x`; `x` stands for number in `[1-9]`.

#### 3. secrete-keeper does the following:

1.  present the solution as a matrix, named sltn_matrix
2.  encrypt `sltn_matrix` with KEY as `sltn_matrix_encrypted`
3.  give `sltn_matrix_encrypted` to secret-verifier

`sltn_matrix` is design to be:

- `sltn_matrix[i][j] = 0` if `(i+1)` row and `(j+1)` col in puzzle is **not** empty
- `sltn_matrix[i][j] = x` if `(i+1)` row and `(j+1)` col in puzzle is empty; `x` stands for the number for this spot in the solution.

#### 4. `sltn_matrix` should fit every single rule of `Sudoku` to be a correct solution.

So, base on the data structure of 2 and 3, `sltn_matrix` is correct **if and only if** such properties stands:

1. Solution should only fill in the empty spots.

   ```Python
   For i, j in [0, 8]:
     assert (pzzl_matrix[i][j] == 0 ) ^ (sltn_matrix[i][j] == 0 )
     # ^ stands for xor
   ```

2. The sums of any row of two matrix adding together, is `27`;

   ```Python
   for i in [0, 8]:
     sum = 0
     for j in [0, 8]:
       sum += pzzl_matrixi + sltn_matrixi
     assert sum == 27
   ```

3. The sums of any col of two matrix adding together, is 27;

   ```Python
   for j in [0, 8]:
     sum = 0
     for i in [0, 8]:
       sum += pzzl_matrixi + sltn_matrixi
     assert sum == 27
   ```

4. Every row only contains number from 1 to 9;
5. Every row not contains repeat number;
6. Every row only contains number from 1 to 9;
7. Every row not contains repeat number;
   > Properties 4-7 can be implemented by code as well.
   >
   > I skip them to save the trouble.

#### 5. Function `encrypted_solution_verify(sltn_matrix_encrypted)`

- It is open source to both secret-verifier and secret-keeper.
- It does the following:
  1. read `sltn_matrix_encrypted` as input
  2. get `sltn_matrix` by decrypting `sltn_matrix_encrypted` with `KEY`
  3. verify the correct of `sltn_matrix`:
     - return true if **all** properties in section 4
     - false if **any** property got violated

#### 6. Verification

secrete-verifier can run `encrypted_solution_verify(sltn_matrix_encrypted)` and check whether the sulotion is correct or not without konwing the sulotion.

### Review

Let's check this protocol agains the 3 rules of zero-knowledge:

1. correctness
   Function `encrypted_solution_verify` can verify any solution correctly

2. soundness
   The soundness is guaranteed by the correctness of function `encrypted_solution_verify`. And it is open source to both party. The secret-verifier has the right to verify this verification code.

3. zero-knowledge
   This part is guaranteed by the encryption method and the zero-access to KEY of secret-verifier. As long as secret-verifier don't have the KEY and encryption method is sound, no other information can be infered from `sltn_matrix_encrypted`.

### Ending

Coooool~ What protocol do you come up with?

If you share your version on comment, we can try to find bugs or analysis.
