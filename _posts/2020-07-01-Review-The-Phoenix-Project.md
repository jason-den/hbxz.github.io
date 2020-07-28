---
layout: post
title: "What I learn from The Phoenix Project"
subtitle: "Wow, Bill is such a loving person!"
date: 2020-07-01 00:00:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - Engineering
  - DevOps
  - Infrastructure
  - Book Note
---



### Points Take Way

#### WIP - work in process

> I consider this as inner-pipeline inventory. 

There are tow parameters that mater: The size and the time length.

- The bigger the size

  => the bigger chunk of cash stuck in the process

  ​	=> the bigger biz risk.



- The longer the length

  => the longer time untill it reach customer (or test team) 

  ​	=> the longer feedback loop

  ​		=> bigger biz risk

Example: two week agile spint vs. 6 month dev-test peroid.

Surely if you only test after 6 month of code developing, you will have much bigger number and more complex bugs than you regularlly check and fix.

#### Constraint

> The fleet speed limited by the slowest ship.

What it is -- Any section/component in a pipeline (architect) that limits the whole throughput.

What can you do?

- Minimize reliance on the constraint

- Protect the performance of the constraint

  > Don't let non-essential job occupy the contraint



#### The Three Way

![image-20200728140001553](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200728140001553.png)

![image-20200728140042501](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200728140042501.png)

![image-20200728140113920](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200728140113920.png)

Continual improvement (on constraints)

- repetition leads to mastary

  > Reminds me of deliberate practice

- Example the [netflix chaos mokey](https://netflix.github.io/chaosmonkey/)



#### The four type of task

- Biz task

- IT task

- Mantainence task

- Unplaned task

> Unplaned task is not cheap. The costs is you sacrifice the resources for other three to do it.



### Comments

I read *the Goal* years before. It's very engaging and interesting. I feel TOC is far more applicable than other consultancy dark magics. So when I heard that this DevOps book copies the style of *the goal*, I felt excited.

Proving to be the "smartest" person in the team can be self-satisfying. But just like Brent becoming the firefighter while constantly generating new chaos, locally high performance doesn't necessary help building up the architect nor the busniess. 

It's thrilling to watch Bill struggle in the chaos, play in the team, diognose the problem, optimise the process, shines the light to the project. Look at those crafty and loving communication and Marine-style burden carrying!  I love such a hero builds up his team and accomplishs bigger goal together!

It reminds me of this verse

> We know that “We all possess knowledge.” But knowledge puffs up while love builds up.





### Other resources

<iframe width="560" height="315" src="https://www.youtube.com/embed/aYy5OdUifqc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



<iframe width="560" height="315" src="https://www.youtube.com/embed/ukHCYxWwNUY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ao87epknEbw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



