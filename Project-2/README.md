# Project 2

Your second project will require you to answer each of the 10 questions below.  You will be expected to open a pull request with your initial answers by the second class meeting, giving you one week to work on these problems. You and your peers will then have one week to work together to refine your respective initial answers, so they are ready for final submission. Once your pull requests have been reviewed and merged to the development branch, I will review them, then merge to the master branch. 

```
Tip #1: Carefully study the Baader, et. al. selections assigned on bisimulation; it is deceptively subtle, and quite powerful. 
Tip #2: Google is still your friend. So is stackexchange...
Tip #3: Work together to solve these problems, even for initial submissions and when you do, document this in github. 
Tip #4: Work together as a team. 
```

1. Let V be a vocabulary of ALCI consisting of a role name "P". Interpret part_of as "x is a part of y". Using this role name, define the following formulas in this language:
```
  (a)  PP that says that x is a proper part of y
  (b)  iPP that says that y is a proper part of x
  (c)  iP that says that x has y as part 
  (d)  O that says that x overlaps y
  (e)  D that says that x and y are disjoint 
```

2. Use your axioms from question 1 as the basis of an ALCI T-Box. Supplement this T-box with whatever other axioms you like, as well as an A-box, so that you ultimately construct a knowledge base K = (T,A). Provide a _model_ of K. This may be graphical or symbolic or both. 

3. Translate the following first-order logic axioms into ALCI: 
```
(a) ∀x∃y∀z(R(x,y) ∧ R(x,z) ∧ R(y,z))
(b) ∃x∀y∃z(R(x,y) ∧ R(x,z) ∧ R(y,z))
(c) ∀y(R(x, y) → ∃x(R(y, x) ∧ ∀y(R(x, y) → A(y))))
(d) (∀y)(R(x, y) → A(y)) ∧ (∃y)(R(x, y) ∧ B(y))
```
4. Provide an interpretation I<sub>1</sub> for ALC and an interpretation I<sub>2</sub> for ALCN - each distinct from any interpretation covered in class so far - and construct a bisimulation that demonstrates ALCN is more expressive than ALC. Use the [mermaid syntax](https://github.com/mermaid-js/mermaid) of markdown to provide a graphical representation of your work. Feel free to use the [mermaid live editor](https://mermaid.live/) when diagramming. 

5. Provide an interpretation I<sub>1</sub> for ALC and an interpretation I<sub>2</sub> for ALCN - each distinct from any interpretation covered in class so far - and construct a bisimulation that _does not_ demonstrate ALCN is more expressive than ALC. Use the [mermaid syntax](https://github.com/mermaid-js/mermaid) of markdown to provide a graphical representation of your work. Feel free to use the [mermaid live editor](https://mermaid.live/) when diagramming. 


6. Explain the difference - using natural language - between the description logic expressions:
  ```
  (a) ∃r.C and ∀r.C
  (b) ∃r-.C and ∀r-.C
  (c) <=nr and <=nr.C
  (d) ∃r-.C and ∃r-.{a} 
```

7. There is a delightfully helpful subreddit called "ELI5" which stands for something like "explain it like I'm 5" where users post conceptually challenging questions and other users attempt to provide explanations in simple, jargon-free, terms that presumably a 5 year-old could understand. Using this as a model, explain the _finite model property_. Be sure to provide a simple example and explain when the property might be important, and when it is not so important. 

let's say you have a really cool toy, like a set of colorful blocks. You can use these blocks to build all kinds of things like towers, houses, and even castles! But there's a catch: you can only use a certain number of blocks, let's say 10.

Now, let's say you have a friend who also has a set of blocks, but they have 15 blocks! They can build even more things than you can because they have more blocks to work with.

The finite model property is kind of like that. It says that if you have a set of rules or instructions for building things, there's a limit to how big those things can be. Just like you have a limit of 10 blocks to work with, the rules have a limit to how much they can describe.

So, if you want to build something really big, you might need more blocks or more rules. But the finite model property says that there's always a limit to how much you can have.

8. Following up on the preceding , explain the _tree model property_. Be sure to provide a simple example and explain when the property might be important, and when it is not so important. 

let's pretend that you have a big family tree! You, your parents, your grandparents, and so on are all part of this family tree. And each of you has your own place on the tree - like, maybe you're a leaf on one of the branches.

The tree model property is a bit like that family tree. It says that if you have a set of rules or instructions for something, you can represent them like a tree. The rules at the top of the tree are like the trunk, and the rules that depend on them are like the branches and leaves.

Now, sometimes it's really important to be able to represent things like this! For example, let's say you're trying to program a computer game. You might have a bunch of rules for how the game works, and it's really helpful to be able to organize them like a tree. That way, you can see which rules depend on other rules, and which ones are the most important.

But there are other times when the tree model property isn't so important. Like, if you're just making a list of things you need to do, you don't really need to organize them like a tree. You can just write them down in a list, and that's fine!

So, it all depends on what you're trying to do. If you need to organize a bunch of rules or instructions, the tree model property can be really helpful. But if you're just making a list, it might not matter as much.

9. Open the Protege editor and create object properties for each of the role names that you constructed in question 1. You should have at least 6 object properties. Assert in the editor that P is a sub-property of O, that P is transitive, and that O is symmetric. Next, add individuals - a, b, c - to the file and assert that c is part of a and that c overlaps b. Running the reasoner should reveal - highlighted in yellow if you select the individual c - that c overlaps a. Using the discussion in the selections from chapter 4 of the Baader, et. al. text as a guide, explain how the tableau algorithm is generating this inference. Also, provide a screenshot of the results of your reasoner run with c highlighted. 

10. Following up on your work in question 9, adjust/add/remove/etc. object properties and individuals in your Protege file so that when you run a reasoner in Protege, you return the following consequences: 
```
  (a) a is a proper part of b and disjoint from e
  (b) a overlaps c
  (c) a is part of b, b is part of f, and a is part of f
  (e) There are no parts between a and g in common
```
Provide a screenshot of your results here. 
