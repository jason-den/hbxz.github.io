## DATA and CONTROL Distinction

NOTE - Extremely difficult to **separate and distinguish DATA and CONTROL**

- **Use/Mention  (philosophical notion)**

  > E.g. "May" is a 3 letter word VS May is a month

- Use/Mention Distinction - one of the main sources of attack in all of the cyber world

  > Other examples: 
  > In computing, the distinction between the pointer and the thing it’s pointing to. A toilet sign is not the toilet itself



- In old operational payphones: 2600 Hz = frequency was discovered to be exact frequency required to make a call; Captain Crunch Whistle was exactly 2600 Hz - whistles were bought so that hackers could get free calls!; **Problem**: Control signal is sent on the same channel as the data signal

- Mentions are theoretically **safe**; where uses are mistaken for mentions, then those uses become vulnerable to attack and exploitation

  > Mentions are in quotations while uses are not
  > People exploited this by the examples above, such as adding extra code into inputs on forms to get program to interpret as code

- Escaping is making sure mention remains a mention, when you have to construct your control from the unsafe data.



The distinction between use and mention can be illustrated for the word cheese:

3 classic examples:

- **Buffer Overflow**
  Smashing The Stack For Fun And Profit 
  http://www-inst.eecs.berkeley.edu/~cs161/fa08/papers/stack_smashing.pdf
  It’s very difficult to say “you can’t” in a complex system

- Realtek audio driver vulnerability
  Driver runs on a privileged level; one of the DLLs the driver loads in is for language (entirely data - linguistic translations); allow this DLL to execute by realtek; you can override this and control the system essentially (good example of use/mention)

- Person carries the message that can be used as the control: [Life of Brian (Monty Python)](https://www.youtube.com/watch?v=8lN4TSslz-0)

