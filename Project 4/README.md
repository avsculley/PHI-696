**The SPARQL Library of Buffalo**

[Codewars](https://www.codewars.com/dashboard) is a website designed to facilitate algorithmic training for various programming languages. Users supply problem statements and others provide coding solutions to those problems. For example, you might find a problem for Python such as: 

```
Define a function that returns the length of a given string. 
```

With a solution like: 

```
def length_of_string(s):
	return len(s)
```
	
Codewars is not limited to traditional programming languages like Python, but also facilitates training for languages like SQL. As you have learned, SQL and SPARQL are both query languages, but what might surprise you is that there is currently no option for training SPARQL in Codewars. This project will go some way to remedy that. 

For this project, you will be tasked with constructing SPARQL problems for the codewars site. 

```
Note #1: Completion of this task will not require you to actually have your SPARQL problems successfully posted to codewars. Adding problems to codewars takes more time than we have for this project. Additionally, you are only allowed to add propose problems to codewars if you have a certain amount of experience (specifically, you need 300 of what they call 'honor points', which is acquired by solving problems). At some point, assuming you permit it, I will post your problems to codewars (giving you credit of course). 
Note #2: The potential for this project to directly impact the ontology community is clear. SPARQL can be challenging, and there are few opportunities for drill practice like this. 
Note #3: You will not be required to learn a programming language, though you will likely need to expand your comfort with computer science jargon; if you hit a wall, ask your peers for help; if the wall persists, ask me. 
Note #4: Codewars provides a guidebook - https://docs.codewars.com/authoring/tutorials/create-first-kata/ - for creating problems; I strongly encourage you to read it, since the standard provided there is how I will be evaluating success. 
```
**Assignment Details**

Problems on Codewars are ranked in terms of difficulty. The lowest "kata" - 8 - indicates a rather easy problem, while the highest kata - 1 - indicates a very challenging problem. 

For our purposes, harder kata will be worth more points than easier kata, and you are required to submit enough kata to acquire 100 points according to the following point system: 

  |   **kata**    |  **points**   |
  | ------------- | ------------- |
  |       1       |      35       |
  |       2       |      25       |
  |       3       |      20       |
  |       4       |      10       |
  |       5       |       5       |
  |       6       |       3       |
  |       7       |       2       |
  |       8       |       0       |

You're probably thinking, "why would I submit a level 8 kata if they're not worth any points?" Great question. Because everyone had to submit at least one level 8 kata. Otherwise, you're permitted to submit kata in any distribution you choose. For example, you might submit 2 problems for kata one (70 points), one for kata 3 (20 points), one for kata 4 (10 points), and one for kata 8 (0 points but required). 

It is your responsibility and the responsibility of your peers reviewing your submission in PR to determine whether your submission is ranked appropriately. In the event that consensus is reached that your kata is ranked inappropriately, you must work with your peers to revise the submission so that it is either more or less challenging, accordingly. You are not permitted to submit new problems with different strengths after PRs are open, but must instead revise your PRs. So, think hard about how challenging your submission is. 

There is one other option for those desiring a different sort of challenge. If you provide alongside your SPARQL submission a translation of the same problem into SQL, complete with documentations, solution, etc. then you may receive half points extra at that kata level (rounded up). For example, if you submit a SPARQL problem that is kata rank 1 and also submit a SQL version of that same problem, you  will receive 35+18=53 points. 




The following Kata 2 prompt-answer pairs also have rdf datasets, which contain real data. The data may be inaccurate or out-of-date.

Prompt #1

```
Given an RDF dataset of books, authors, and publishers, construct a new dataset with information about the authors who have written at least two books, and their respective publishers. Additionally, find the average rating of each author's books.
```

Dataset #1

```
@prefix ex: <http://example.org/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

ex:theMartian rdf:type ex:Book .
ex:theMartian ex:title "The Martian" .
ex:theMartian ex:author ex:andyWeir .
ex:theMartian ex:publisher ex:crownPublishing .
ex:theMartian ex:rating 4.5 .

ex:artemis rdf:type ex:Book .
ex:artemis ex:title "Artemis" .
ex:artemis ex:author ex:andyWeir .
ex:artemis ex:publisher ex:crownPublishing .
ex:artemis ex:rating 3.7 .

ex:toKillAMockingbird rdf:type ex:Book .
ex:toKillAMockingbird ex:title "To Kill a Mockingbird" .
ex:toKillAMockingbird ex:author ex:harperLee .
ex:toKillAMockingbird ex:publisher ex:harperCollins .
ex:toKillAMockingbird ex:rating 4.3 .

ex:andyWeir rdf:type ex:Author .
ex:andyWeir ex:name "Andy Weir" .

ex:harperLee rdf:type ex:Author .
ex:harperLee ex:name "Harper Lee" .

ex:crownPublishing rdf:type ex:Publisher .
ex:crownPublishing ex:name "Crown Publishing" .

ex:harperCollins rdf:type ex:Publisher .
ex:harperCollins ex:name "HarperCollins" .
```


Answer #1

```
PREFIX ex: <http://example.org/>

CONSTRUCT {
  ?author ex:name ?authorName .
  ?author ex:hasPublisher ?publisher .
  ?author ex:averageRating ?avgRating .
}
WHERE {
  {
    SELECT ?author (COUNT(?book) AS ?bookCount) (AVG(?rating) AS ?avgRating)
    WHERE {
      ?book ex:author ?author .
      ?book ex:publisher ?publisher .
      ?book ex:rating ?rating .
      ?author ex:name ?authorName .
    }
    GROUP BY ?author
    HAVING (COUNT(?book) >= 2)
  }
}
```

Prompt #2

```
Given an RDF dataset of movies, directors, actors, and genres, construct a new dataset containing only movies of the 'Science Fiction' genre directed by directors who have directed at least three movies in this genre, including the movies' titles, release years, and directors' names.
```
Dataset #2
```
@prefix ex: <http://example.org/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

ex:interstellar rdf:type ex:Movie .
ex:interstellar ex:title "Interstellar" .
ex:interstellar ex:genre "Science Fiction" .
ex:interstellar ex:releaseYear "2014" .
ex:interstellar ex:director ex:christopherNolan .

ex:inception rdf:type ex:Movie .
ex:inception ex:title "Inception" .
ex:inception ex:genre "Science Fiction" .
ex:inception ex:releaseYear "2010" .
ex:inception ex:director ex:christopherNolan .

ex:thePrestige rdf:type ex:Movie .
ex:thePrestige ex:title "The Prestige" .
ex:thePrestige ex:genre "Mystery" .
ex:thePrestige ex:releaseYear "2006" .
ex:thePrestige ex:director ex:christopherNolan .

ex:theMatrix rdf:type ex:Movie .
ex:theMatrix ex:title "The Matrix" .
ex:theMatrix ex:genre "Science Fiction" .
ex:theMatrix ex:releaseYear "1999" .
ex:theMatrix ex:director ex:lanaWachowski .
ex:theMatrix ex:director ex:lillyWachowski .

ex:christopherNolan rdf:type ex:Director .
ex:christopherNolan ex:name "Christopher Nolan" .

ex:lanaWachowski rdf:type ex:Director .
ex:lanaWachowski ex:name "Lana Wachowski" .

ex:lillyWach
```
Answer #2
```PREFIX ex: <http://example.org/>

CONSTRUCT {
  ?movie ex:title ?title .
  ?movie ex:releaseYear ?releaseYear .
  ?movie ex:director ?director .
  ?director ex:name ?directorName .
}
WHERE {
  ?movie ex:genre "Science Fiction" .
  ?movie ex:title ?title .
  ?movie ex:releaseYear ?releaseYear .
  ?movie ex:director ?director .
  ?director ex:name ?directorName .
  {
    SELECT ?director (COUNT(?movie) AS ?movieCount)
    WHERE {
      ?movie ex:genre "Science Fiction" .
      ?movie ex:director ?director .
    }
    GROUP BY ?director
    HAVING (COUNT(?movie) >= 3)
  }
}
```





