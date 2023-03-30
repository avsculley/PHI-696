# Project 3

Your third project will require you to answer each of the 10 questions below.  You will be expected to open a pull request with your initial answers by the second class meeting, giving you one week to work on these problems. You and your peers will then have one week to work together to refine your respective initial answers, so they are ready for final submission. Once your pull requests have been reviewed and merged to the development branch, I will review them, then merge to the master branch. 

```
For any question involving the use of Protege, please be sure to import:
1. Basic Formal Ontology (https://raw.githubusercontent.com/BFO-ontology/BFO/v2019-08-26/bfo_classes_only.owl)
2. The Relations Ontology (https://raw.githubusercontent.com/oborel/obo-relations/master/ro.owl)
```

1. In BFO and RO identify at least one object property for each of a-e that _should have the listed property, but which does not_; argue for your case, using examples. Note: It will be easiest to view the object properties in BFO and RO using Protege. 
```
  (a)  Reflexive: 
  ```
  simultaneous_with
  An object property R is reflexive just in case, for all x, xRx. When R = 'simultanious_with', xRx is true for all x. That is, everything is simultanious_with itself. In other words, for all x, x occurs at the same period of time as x. For example, the final of the 2020 world cup occurred at the same period of time as the final of the 2020 world cup.
  ``` 
  (b)  Transitive : 
  ```
  causally_influenced_by
  
  An object property R is transitive just in case, for all x, for all y, for all z, xRy & yRz -> xRz. When R = 'causally influenced by', xRy & yRz -> xRz is true for all x, for all y, for all z. That is, if x is_causally_influenced_by y and y is_causally_influenced_by z, then x is_causally_influenced_by z. For example, if this act of violence is causally influenced by that act of violence, and that act of violence is causally influcenced by this publication of a cartoon, then this act of violence was causally influenced by this publication of a cartoon.
  ```
  (c)  Symmetric: 
  ```
  'reciprocal_of'
  
  An object property R is symmetric just in case for all x, for all y, xRy <-> yRx. When R = 'reciprocal_of', xRy <-> yRx is true for all x, for all y. That is, x is_reciprocal_of y iff y is reciprocal_of x. For example, 'spermatocyte lacks asters' iff 'asters absent from spermatocyte'.
  ```
  
  (d)  Functional : 'differnet in magnitude relative to'
  (e)  Symmetric and Reflexive : correlated_with
```

2. In BFO and RO identify at least one object property for each of a-e that _should not have the listed property, but which does_; argue for your case, using examples. Note: It will be easiest to view the object properties in BFO and RO using Protege.
```
  (a)  Irreflexive : has_role_in_model
  (b)  Transitive : alligned_with
  (c)  Asymmetric: 
  (d)  Functional : phenotype_of
  (e)  Inverse Functional : has_characteristic
```

3. Model the following natural language expressions using terms from BFO and RO; you are welcome to introduce new terms where needed:  
```
  (a) Sally has an arm Tuesday but does not have an arm Wednesday. “Sally has_part at least one arm on Tuesday precedes Sally has_part no arms on Wednesday”
  (b) Every liver has some cell as part at all times it exists. Liver has_part_at_all_times some cell.
  (c) John was a child, then an adult, then a senior. 
  
  (d) Goofus and Gallant are married at each point in a three year span. 
  
  “Three years span 1” is an instance_of one-dimensional temporal region.
Notice that the original phrase doesn’t say anything about Goofus and Gallant being married to each other, and we won’t represent such a fact.
T1 is an instance_of zero-dimensional temporal region.
If zero-dimensional temporal region t1 is part_of the one-dimensional temporal region “three years span 1”, then Goofus participates in marriage at t1 and Galland participates in marriage at t1.

Goofus spouse_of Gallant at t1

  
```

4. Using the language of First-Order Logic, represent the following natural language expressions; you are welcome to introduce new terms where needed: 
```
  (a) Sally has an arm Tuesday but does not have an arm Wednesday. 
  
   ∃x (Tx ∧ ∃y (Hsy∧Ay)) ∧ ∃x (Wx ∧ ~∃y(Hsy∧Ay))
  T: Tuesday
  H: has
  A: arm
  W: Wednesday
  s: Sally

  (b) Every liver has some cell as part at all times it exists. 
    ∀x∃y(Lx→Cy∧Pyx)
  L: liver
  C: cell
  P: part of at all times

  (c) John was a child, then an adult, then a senior. 
  j = John
E (x, y) = being earlier than
C (x, t) = being a child at t
A (x, t) = being an adult at t
S (x, t) = being a senior at t
∃t1∃t2∃t3 (C (j, t1) ∧ A (J, t2) ∧ S(J, t3) ∧ E (t1, t2) ∧ E (t2, t3))

  
  (d) Goofus and Gallant have been married for three years; for each day of that span, it is true to assert they are married. 

M(x, t) = being married at t
Y(t) = belongs to 3 year span 1
g1 = Goofus
g2 = Gallant
D(t) = t is a day
∀t(D(t) ∧ Y(t)→(M(g1,t) ∧ M(g2,t)))

  
```

5. Using BFO and RO, model the following scenario: the content of an rdf file is represented in two serializations - one in Turtle, one in XML - which are sent from one computer to two distinct computers on the same network.   


6. Using Protege, place these in the BFO hierarchy where you think they fit best:

  (a) Bach's Well-Tempered Clavier: GDC
  (b) Chair of the UB Philosophy Department: is an 'object'
  (c) SARS-CoV-2: 'object'
  (d) Mexico City: is an instance of a city, which is a subclass of 'object aggregate'
  (e) The trunk of a minivan: subclass of site
  (f) Occupation: process in which some occupation role is realized
  (g) Ocean: environmental system
  (h) Lake: fiat object part bound by a 
```

7. True or False; explain your answers:
```
  (a) An instance of Material Entity can have an instance of Immaterial Entity as part. False
  (b) An instance of Immaterial Entity can have an instance of Material Entity as part.
  (c) An organization may have another organization as part. True: an organization of organizations
  (d) An organization may have no members as part. False
  (e) Any site is partially bounded by some instance of Material Entity. 
  (f) A book placed under the leg of a wobbly table has acquired a new function. False
  (g) A glass vase cushioned with packing material for all time, has the disposition to break. True
  (h) Spacetime is a class in BFO. False
  (i) The continuant fiat boundary class of BFO is closed, meaning, there are no subclasses beyond those identified presently in BFO. False becasue there can be subclasses of the subclasses of continuant fiat boundary.
```

8. Model the following scenario in BFO, introducing whatever terms are needed to do so: John runs for 3 hours, startin slowly, speeding up during the middle, then ending the run at a slower pace.  

9. The Pellet reasoner in Protege can be used in an incremental reasoning strategy. ELI5 when and why one should use Pellet for incremental reasoning. 

```
Pellet is like a really smart robot that helps computers think and learn better.

When you have a lot of information that you want the computer to process and understand, Pellet can help you do it in small pieces instead of all at once. This is called incremental reasoning.

Pellet is good at this because it can remember things it learned before, so it doesn't have to start from scratch every time. It's like when you learn your ABCs, you don't have to start from the beginning every time you want to say the alphabet. You already know the letters and can build on that knowledge.

So, if you have a lot of information you want the computer to learn and understand, using Pellet for incremental reasoning can help it do it more efficiently and accurately.
```
10. Protege reasoners will not allow you to combine certain properties, e.g. reflexivity and transitivity. If you attempt to assert such pairs of the same object property, then run the reasoner, nothing will happen. If you combine such properties while a reasoner is running, then ask to synchronize the reasoner, an error will be thrown. Provide a table or series of tables illustrating which pairs of properties cannot be combined in Protege, either because nothing happens when the reasoenr is run or because an error is thrown when synchronizing a reasoner after making such changes. Review the github docs on [creating tables in markdown](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-tables).
