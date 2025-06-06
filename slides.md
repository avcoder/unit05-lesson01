---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Algorithms and Data Structures
Algorithms and Structural Foundations - part 1/8

- [ ] Importance of data structures and algorithms
- [ ] Computer Memory, Data Structures, Arrays
- [ ] Bubble Sort

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
-->

---
transition: slide-left
---

# Preview

- Lesson 1 to 4 will be theoritical fundamental concepts about algorithms and data structures
- Lesson 5 to 8 you'll get a development problem, and you'll have to gather resources , research, read and implement a possible solution.  
- See DSA Assignment
- Brain Teaser: the 8 Golden Weighted Spheres
   - The golden spheres are identical in weight, colour, texture etc... except 1 of the 8 is imperceptibly lighter than the others.  You're given a traditional balance scale?
   - What questions might you ask to clarify problem?
   - What steps would you do to find that odd one out?
   - How many steps would you need to solve it?
- "Big O" Notation: Big O is a way to categorize your algorithm's time or memory requirements based on input.  It is meant to generalize growth of your algorithm.


---
transition: slide-left
---

# Importance of Algorithms

- You need a way to determine with certainty if the coding instructions you've written to solve a problem is more efficient and scalable over other alternatives
- Examples include:
   - when searching and filtering large data sets
   - managing queues like chat apps, job queues
   - implementing features like autocomplete, recommendation systems, or calendar schedulers
- "But I just ask the DB to filter/search for me so why learn DSA?"
   - You'll still need to understand performance by knowing when a search is efficient
   - Plus you often work with data after the db such as combining multiple data sources in the browser 
 - As you build real-time features, personalized recommendations, analytics dashboards, you move beyond CRUD into an area where efficient algorithms matter
- [Big O cheatsheet](https://www.bigocheatsheet.com/)

---
transition: slide-left
---

# Importance of Data Structures

1. Different problems require different ways of organizing and accessing data
   - Picking the right data structure makes your app faster and more memory-efficient
2. Improves App performance
   - at first you may be using arrays for filtering a list of thousands, showing recent notifications, sorting large sets etc., but without knowing better structures (ex: tries, heaps, sets), your app can slow down as it grows
   - ex: React's virtual DOM is a tree, Browser rending uses stacks and queues
3. Enables problem solving
   - Data structures provide the foundation you build solutions on top of and are essential to solving algorithmic problems (sorting, searching, pathfinding etc.)
4. Needed for Job Interviews
   - may be asked to solve coding challenges: Big O + choose the right data structure
- Example Data Structures: array, linked list, stack, queue, binary tree, hash table, graph etc.

---
transition: slide-left
layout: center
class: text-center
---

# How does Computer Memory Work?
You can't have data, without any structure to put it in

---
transition: slide-left
---

# 1. Electricity

- Understand basic electricity (series vs parallel circuits, voltage, current etc.)
   - ex: Switch a light > turns on the light
<img src="/assets/switch.jpg">
- Q: Can we control or manipulate basic electricity?

---
transition: slide-left
---

# 2. Electronics

- Understand [logic gates / truth tables](https://images.theengineeringprojects.com/image/webp/2023/08/symbols-truth-tables-of-common-logic-gates.jpg.webp?ssl=1)
<img src="/assets/truth.jpg" width="500">
- Q: Now that we can manipulate electricity, can we use electronic components to remember (on/off)?

---
transition: slide-left
---

# 3. Electronic Memory

- Imagine a room where a light switch turns on a fan. Once the fan is running, it blows on a switch that keeps itself turned on. That’s the feedback loop — once activated, the circuit maintains itself.
- Understand electronics (controlling and manipulating electricity using components)   
   - Watch 30 sec of https://www.youtube.com/watch?v=I0-izyq6q5s#t=0m35s
   - So there is an electronic way to remember state (on/off) 
   - Continue watching until 2:30 to learn more about logic gates
   - Q: if 1 represents `on`, and 0 represents `off`: 
      - How many numeral possibilities can we represent with only one `bit`?  
      - How about with two `bits`?
- Q: Now that we can get electronics to remember state (on/off), can we represent numbers with it? 

---
transition: slide-left
---

# 4. Binary

<img src="/assets/binary1.jpg" width="500">

- 8 bits = 1 byte
- What's the maximum number 1 byte can hold?
   - Does that max value remind you of anything?  (hint: [hexadecimal](https://miro.medium.com/v2/resize:fit:1400/1*xngYaMqb1JL6PaTb8NXDpA.jpeg))
   - What if we wanted to hold bigger numbers? (see: [data types in C](https://fastbitlab.com/wp-content/uploads/2022/05/Figure-1.png))
- Now that can represent numbers with 8 bits, can we represent letters?

---
transition: slide-left
---

# 4b. ASCII

<img src="/assets/ascii.png" width="470">

<!--
- Do you now understand why sorting always thinks capitals comes before lower case letters?
-->

---
transition: slide-left
---

# 5. Computer Memory
Storage space in a computer where data and instructions are stored

- According to Moore's Law, we should be able to double our electronics component will double in capacity each year
- Q: What does computer memory look like today?
   - Watch 1 minute of: https://www.youtube.com/watch?v=7J7X7aZvMXQ#t=0m43s
   - Watch 2 minutes of: https://www.youtube.com/watch?v=7J7X7aZvMXQ#t=12m09sdram
<img src="/assets/dram.png" width="300">
- We now have a physical understanding of memory where data (and data structures) can reside
- `Addresses` are used to identify a particular memory block where data resides

---
transition: slide-left
---

# Exercise: Visualizing Memory
Given the following memory cell with its address and its corresponding char

| Address | Value |
| ------- | ----- |
| 1000    | A     |
| 1001    | a     |
| 1002    | Z    |

- Q: What binary value is stored at address 1000?
- Q: If an integer takes 4 bytes and starts at address 1010, what are the addresses it occupies?

---
transition: slide-left
---

# Exercise: Visualizing Memory in C

```c
// hello.c
#include <stdio.h>

int main() {
  printf("Hello world\n");

  char a = 'A';
  char b = 'a';
  char c = 'Z';
  printf("size of %zu\n", sizeof(a)); // output how many bytes this data type uses
  printf("Address is: %p\n", &a); // output the hexadecimal memory address
  printf("which in decimal is %lu\n", (unsigned long)(uintptr_t)&a); // convert address to decimal

  return 0;
}
```

- to compile run `gcc hello.c` which produces an executable named `a.out`
- run it `./a.out`
- try changing data type from `char` to `int` or some other data type
- FYI: Run `otool -tV a.out` to see how code turns into assembly / bytes 

---
transition: slide-left
---

# Data Structures: Arrays

- We are now at a point to talk about our first data structure -- arrays
- Q: How might an array be naturally arranged in memory blocks?
- Q: Given the following declaration, how might you locate/arrange this array in memory?
  ```c
  #include <stdio.h>

  int main() {
    int numbers[3] = {10, 20, 30};
    return 0;
  }
  ```

- Q: Given numbers array above, and base address = 2000, what is the address of array[2]
   - Prove it in C

<!--
- contiguous
-->

---
layout: image-right
transition: slide-left
image: /assets/lydia.png
backgroundSize: 400px 330px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:
- 💻 [leetcode](https://leetcode.com/)
- 🕵️ [hackerrank](https://www.hackerrank.com/)
- 🚦[codeSignal](https://codesignal.com/)
- 📡 [interviewBit](https://codesignal.com/)
- 🏫 [Harvard Algorithms Lecture](https://www.youtube.com/watch?v=iCx3zwK8Ms8)
- 🏫 [Harvard Data Structures Lecture](https://www.youtube.com/watch?v=0euvEdPwQnQ&list=PLhQjrBD2T381WAHyx1pq-sBfykqMBI7V4&index=6)
- 🧮 [THE classic CS Textbook](https://edutechlearners.com/download/Introduction_to_algorithms-3rd%20Edition.pdf)

<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

---
transition: slide-left
---

# Sorting

---
transition: slide-left
---

# Bubble Sort

---
transition: slide-left
---

# Homework

- I'll create breakout rooms which you can freely choose to enter
- Opportunity to work on midterm in class
- Opportunity to have 1:1 with me re: midterm or any questions 
   - DM me if you want to meet in a breakout room
- Work on your "Note-taking" midterm app due June 15 midnight EST
- Exercise: summarize our unit by creating a [Movie Ratings and Review app](https://courses.circuitstream.com/d2l/le/lessons/9514/topics/49843)