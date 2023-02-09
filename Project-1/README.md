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

  ```
  
  Truth table images generated using https://web.stanford.edu/class/cs103/tools/truth-table-tool/
  
  (a) (¬A→B)∨((A∧¬C)→B) 
  
 
  
  ![image](https://user-images.githubusercontent.com/80927159/217919322-bc74663f-d623-4059-97c9-cd2aefe7ddae.png)
  
  Tatology

  (b) (A→B)∧(A→¬B)
  
  ![image](https://user-images.githubusercontent.com/80927159/217920278-676f99bb-fcf7-4b4f-8dee-5e83c0902925.png)
Contingent
  (c) (A→(B∨C))∨(C→¬A) 
  
  ![image](https://user-images.githubusercontent.com/80927159/217920327-abfb4f8d-fa66-4e4d-83ac-ed869a875f1c.png)
Tautology
  
  (d) ((A→B)∧C)∨(A∧D) 
  
  ![image](https://user-images.githubusercontent.com/80927159/217920381-e9b4e3a0-5d6e-4f5a-9b38-d52e7eac1564.png)
Contingent
  ```
	
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
  (b)  A that says that x is an aunt of y
  (c)  C that says that x and y are cousins
  (d)  O that says that x is an only child  
  (e)  T that says that x has exactly two brothers 
  ```


5. Select two formulas defined in ALC from question 4 to form the basis of a T-Box. Supplement this T-box with whatever other axioms you like, as well as an A-box, so that you ultimately construct a knowledge base K = (T,A). Provide a _model_ of K. This may be graphical or symbolic or both. 

6. Explain the difference - using natural language - between the first-order prefixes:
  ```
  (a) ∃x∀y and ∀x∃y
  (b) ∃x∀y∃z and ∀x∃y∀z 
  (c) ∀x∃y∀z∃w and ∃x∀y∃z∀w
```
	
7. Show that the following sentences are not equivalent by exhibiting a graph that models one but not both of these sentences:
```
∀x∃y∀z(R(x,y) ∧ R(x,z) ∧ R(y,z))
∃x∀y∃z(R(x,y) ∧ R(x,z) ∧ R(y,z))
```
	
8. Using an online tableau proof generator - such as the one found here `https://www.umsu.de/trees/` - provide tree proofs of the following entailments, which are known as the De Morgan's laws:
  ```
  (a) ∀x∀y(¬(Px ∧ Qx) → (¬Px ∨ ¬Qx))
  (b) ∀x∀y(¬(Px ∨ Qx) → (¬Px ∧ ¬Qx))
  (c) ∀x∀y((¬Px ∨ ¬Qx) → ¬(Px ∧ Qx))
  (d) ∀x∀y((¬Px ∧ ¬Qx) → ¬(Px ∨ Qx))
```
	
9. Using a natural deduction proof generator - such as the one found here `https://proofs.openlogicproject.org/` - provide natural deduction proofs for each of De Morgan's laws. 

10. Compare and contrast the proofs provided for (a) in your answers to questions 8 and 9. Explain the different assumptions, strategies, etc. exhibited in tree proofs vs natural deduction proofs. 
 
