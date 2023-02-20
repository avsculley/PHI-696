# Project 1 Assignment

Your first project will require you to answer each of the 10 questions below.  You will be expected to open a pull request with your initial answers by the second class meeting, giving you one week to work on these problems. You and your peers will then have one week to work together to refine your respective initial answers, so they are ready for final submission. Once your pull requests have been reviewed and merged to the development branch, I will review them, then merge to the master branch. 

```
Tip #1: Carefully study the Hedman selections assigned, as several of the questions are taken directly from the textbook. 
Tip #2: Google is your friend. An important skill to pick up in this class is recognizing when to think hard and when to think smart. You might find answers to some of the questions below simply by googling; you might find pieces of answers to parts of some question below, which will need to be combined; then again, you might not find any help at all because the questions are more novel than they initially appear. I encourage you to use existing resources as guidance, but be careful. My reputation for asking students tricky questions is well-earned. 
Tip #3: Work _together_ to solve these problems, even for initial submissions and when you do, document this in github. For example, you might feel like you nearly have answers to question 1, but would love another pair of eyes. You can then open a post in your local github account, and tag folks from class requesting they check out your work. 
Tip #4: The work we do is challenging; that should be assumed. You are smart enough to be here; that should also be assumed. We have neither time nor space for shaming, but all of time and space for praising. Be cognizant of how your messages might be received, and err on the side of caution. It is hard to surmise intent from text alone. For my part, I treat text only communications the way modern musicals are written: Little subtext; emotions on the sleeve. 
```

Note: The standard interpretation of the logical symbols - "∨", "∧", "→", "¬", "∀", "∃" - is assumed throughout. 

1. Provide the truth tables for each of the following propositional logic formulas. State whether each is a tautology, a contradiction, or contingent:

 
  
  Truth table images generated using https://web.stanford.edu/class/cs103/tools/truth-table-tool/
  
  (a) (¬A→B)∨((A∧¬C)→B) 
  
 
  
  [image](https://user-images.githubusercontent.com/80927159/217919322-bc74663f-d623-4059-97c9-cd2aefe7ddae.png)
  
  Tautology

  (b) (A→B)∧(A→¬B)
  
  [image](https://user-images.githubusercontent.com/80927159/217920278-676f99bb-fcf7-4b4f-8dee-5e83c0902925.png)
Contingent
  (c) (A→(B∨C))∨(C→¬A) 
  
  [image](https://user-images.githubusercontent.com/80927159/217920327-abfb4f8d-fa66-4e4d-83ac-ed869a875f1c.png)
Tautology
  
  (d) ((A→B)∧C)∨(A∧D) 
  
  [image](https://user-images.githubusercontent.com/80927159/217920381-e9b4e3a0-5d6e-4f5a-9b38-d52e7eac1564.png)
Contingent
  
	
2. A _literal_ is an atomic formula or the negation of an atomic formula. We say a formula is in _conjunctive normal form_ (CNF) if it is the conjunction of the disjunction of literals. Find propositional logic formulas in CNF equivalent to each of the following:
  ```
  (a) (A→B)→C
  
  A ∧ ¬B ∨ C

  
  (b) (A→(B∨C))∨(C→¬A)
  
  (¬A ∨ B) ∨ (¬A ∨ C) ∨ (¬C ∨ ¬A)

  
  (c) (¬A∧¬B∧C)∨(¬A∧¬C)∨(B∧C)∨A 
  
  (¬A ∧ ¬B ∧ C) ∨ (¬A ∧ ¬C) ∨ (B ∧ C) ∨ A is already in conjunctive normal form

  
  ```
  
3. Let V be the vocabulary of first-order logic consisting of a binary relation P and a unary relation F. Interpret P(x,y) as “x is a parent of y” and F(x) as “x is female.” Where possible define the following formulas in this vocabulary; where not possible, explain why: 
  
  ```
  (a)  B(x,y) that says that x is a brother of y  
  
  (¬F(x)) ∧ (P(p,x) ∧ P(p,y))

  
  (b)  A(x,y) that says that x is an aunt of y  
  
  F(x) ∧ (P(x,z) ∧ P(z,y))

  
  (c)  C(x,y) that says that x and y are cousins   
  
  (P(a,x) ∧ P(b,x)) ∧ (P(c,y) ∧ P(d,y)) ∧ (P(a,c) ∨ P(a,d) ∨ P(b,c) ∨ P(b,d))

  
  (d)  O(x) that says that x is an only child  
  
  Can't be done without saying that x is = to all their parents' children. However, using = :
  
  (∀y)(P(p,x) ⇒ (P(p,y) ⇒ (y = x)))

  
  (e)  T(x) that says that x has exactly two brothers 
  
  
  Can't be done without a way to say that x's number of brothers = 2. However, using =:
  
  (∃y1)(∃y2)((y1 ≠ y2) ∧ (¬F(y1)) ∧ (¬F(y2)) ∧ (P(p,x) ∧ P(p,y1) ∧ P(p,y2)) ∧ (∀z)((z ≠ y1) ∧ (z ≠ y2) ⇒ ¬(P(p,z))))

  
  
  ```

4. Let V be a vocabulary of the attribute (concept) language with complements (ALC) consisting of a role name "parent_of" and a concept name "Male". Interpret parent_of as "x is a parent of y" and M as "x is male". Where possible define the following formulas in this vocabulary; where not possible, explain why: 
  ```
  (a)  B that says that x is a brother of y
  
  ∃p (p ∈ parent_of ∧ parent_of(p, x) ∧ parent_of(p, y) ∧ male(x))
  
  (b)  A that says that x is an aunt of y
  
  ∃p (p ∈ parent_of ∧ ∃s (s ∈ parent_of ∧ parent_of(x, s) ∧ parent_of(s, p) ∧ parent_of(p, y)) ∧ female(x))
  
  
  (c)  C that says that x and y are cousins
  
  Can't be done without a way to represnet 'grandparent_of' relation
  
  (d)  O that says that x is an only child  
  
  ∃p (p ∈ parent_of ∧ ∀p' (p' ∈ parent_of → (p' ≠ p ∧ ¬parent_of(p', x))))
  
  (e)  T that says that x has exactly two brothers 
  
  ∃p (p ∈ parent_of ∧ ∀m (m ∈ male ∧ parent_of(p, m) ⇒ (m ≠ x ⇔ ∃m' (m' ≠ m ∧ m' ≠ x ∧ parent_of(p, m')))))
  
  ```


5. Select two formulas defined in ALC from question 4 to form the basis of a T-Box. Supplement this T-box with whatever other axioms you like, as well as an A-box, so that you ultimately construct a knowledge base K = (T,A). Provide a _model_ of K. This may be graphical or symbolic or both. 

(a)
T-box:
Concepts: parent_of, male
Roles: parent_of

A-box:
p ∈ parent_of
parent_of(p, x)
parent_of(p, y)
male(x)

(d)
TBox:

Concept definition: "onlyChild" is equivalent to "∃p (p ∈ parent_of ∧ ∀p' (p' ∈ parent_of → (p' ≠ p ∧ ¬parent_of(p', x))))"
ABox:

Concept assertion: "x" is an instance of "onlyChild".

6. Explain the difference - using natural language - between the first-order prefixes:
  ```
  (a) ∃x∀y and ∀x∃y
  
  ∃x∀y means "there exists an x such that for all y, some property is true." This expression asserts that there is at least one object x that satisfies the given property for all y. In other words, there is some x that is universally applicable to all y.

On the other hand, ∀x∃y means "for all x, there exists a y such that some property is true." This expression asserts that for every object x, there is at least one y that satisfies the given property. In other words, for every x, there exists at least one y that can be paired with x to make the property true.

The key difference between these two expressions lies in the order of the quantifiers. In the first expression, we first existentially quantify over x and then universally quantify over y. In the second expression, we first universally quantify over x and then existentially quantify over y. This order can make a difference in some contexts and can affect the truth of the statement being made.
  
  (b) ∃x∀y∃z and ∀x∃y∀z 
  
  Both of these are logical expressions involving quantifiers.

∃x∀y∃z means "there exists an x such that for all y there exists a z such that some property is true." This expression asserts that there is at least one object x that satisfies the given property for all y, and for each y there exists at least one z that satisfies the property. In other words, there is some x that can be paired with any y and some z to make the property true.

On the other hand, ∀x∃y∀z means "for all x, there exists a y such that for all z some property is true." This expression asserts that for every object x, there is at least one y that satisfies the given property for all z. In other words, for every x, there exists at least one y that can be paired with any z to make the property true.

The key difference between these two expressions lies in the order of the quantifiers and the scope of each quantifier. In the first expression, we first existentially quantify over x and then universally quantify over y and then existentially quantify over z. In the second expression, we first universally quantify over x and then existentially quantify over y and then universally quantify over z.

In ∃x∀y∃z, we have the most flexibility to choose a value for x first and then have some freedom to choose values for y and z that satisfy the property. In ∀x∃y∀z, we have to satisfy the property for all z for any value of x that we choose, and we have the freedom to choose a y that satisfies the property for that x.
  
  (c) ∀x∃y∀z∃w and ∃x∀y∃z∀w
  
  
 ∀x∃y∀z∃w means "for all x, there exists a y such that for all z, there exists a w such that some property is true." This expression asserts that for every object x, there is at least one y that satisfies the given property for all z, and for each z there exists at least one w that satisfies the property. In other words, for any value of x we choose, there is a y that works for all z, and for any value of z we choose, there is a w that works with that y to satisfy the property.

On the other hand, ∃x∀y∃z∀w means "there exists an x such that for all y, there exists a z such that for all w, some property is true." This expression asserts that there is at least one object x that satisfies the given property for all y, and for each y there exists at least one z that satisfies the property for all w. In other words, there is some x that can be paired with any y, and for any y we choose, there is a z that works for all w.

The key difference between these two expressions lies in the order of the quantifiers and the scope of each quantifier. In the first expression, we first universally quantify over x and then existentially quantify over y and z and then existentially quantify over w. In the second expression, we first existentially quantify over x and then universally quantify over y and then existentially quantify over z and then universally quantify over w.

In ∀x∃y∀z∃w, we have to satisfy the property for all z for any value of x that we choose, and for any value of z we choose, there is a w that satisfies the property. In ∃x∀y∃z∀w, there is some x that can be paired with any y, and for any y we choose, there is a z that works for all w.





  
```
	
7. Show that the following sentences are not equivalent by exhibiting a graph that models one but not both of these sentences:
```
∀x∃y∀z(R(x,y) ∧ R(x,z) ∧ R(y,z))
∃x∀y∃z(R(x,y) ∧ R(x,z) ∧ R(y,z))




```
	
8. Using an online tableau proof generator - such as the one found here `https://www.umsu.de/trees/` - provide tree proofs of the following entailments, which are known as the De Morgan's laws:
  
  (a) ∀x∀y(¬(Px ∧ Qx) → (¬Px ∨ ¬Qx))
  <img width="416" alt="Screenshot 2023-02-19 at 9 49 45 PM" src="https://user-images.githubusercontent.com/80927159/219998405-76db16b6-eeea-4765-b387-8fff4f42a630.png">

  (b) ∀x∀y(¬(Px ∨ Qx) → (¬Px ∧ ¬Qx))
  <img width="413" alt="Screenshot 2023-02-19 at 9 51 46 PM" src="https://user-images.githubusercontent.com/80927159/219998503-fc8fc6e3-d621-4702-80c4-4d4e262345ca.png">

  (c) ∀x∀y((¬Px ∨ ¬Qx) → ¬(Px ∧ Qx))
  
  <img width="436" alt="Screenshot 2023-02-19 at 9 52 14 PM" src="https://user-images.githubusercontent.com/80927159/219998569-d3269605-ad15-4267-8bd8-51185ed12740.png">

  (d) ∀x∀y((¬Px ∧ ¬Qx) → ¬(Px ∨ Qx))
<img width="415" alt="Screenshot 2023-02-19 at 9 52 48 PM" src="https://user-images.githubusercontent.com/80927159/219998660-ca1773c7-e396-493f-8de6-28ab0a92dcd3.png">
	
9. Using a natural deduction proof generator - such as the one found here `https://proofs.openlogicproject.org/` - provide natural deduction proofs for each of De Morgan's laws. 

10. Compare and contrast the proofs provided for (a) in your answers to questions 8 and 9. Explain the different assumptions, strategies, etc. exhibited in tree proofs vs natural deduction proofs. 
 
