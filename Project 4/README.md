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




The following Kata 5 prompt-answer pairs also have rdf datasets, which contain real data. The data may be inaccurate or out-of-date.

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

```
Answer #2
```
PREFIX ex: <http://example.org/>

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


Prompt #3

```
Given an RDF dataset of courses, students, and their enrollment details, construct a new dataset containing students who are enrolled in at least two courses, the courses they are enrolled in, and the students' average grade across all their courses.
```

Dataset #3

```
@prefix ex: <http://example.org/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

ex:calculus rdf:type ex:Course .
ex:calculus ex:name "Calculus" .

ex:chemistry rdf:type ex:Course .
ex:chemistry ex:name "Chemistry" .

ex:physics rdf:type ex:Course .
ex:physics ex:name "Physics" .

ex:alice rdf:type ex:Student .
ex:alice ex:name "Alice" .
ex:alice ex:enrolledIn ex:calculus .
ex:alice ex:enrolledIn ex:chemistry .
ex:alice ex:grade 90 .

ex:bob rdf:type ex:Student .
ex:bob ex:name "Bob" .
ex:bob ex:enrolledIn ex:calculus .
ex:bob ex:grade 85 .

ex:carol rdf:type ex:Student .
ex:carol ex:name "Carol" .
ex:carol ex:enrolledIn ex:calculus .
ex:carol ex:enrolledIn ex:physics .
ex:carol ex:grade 95 .
```

Answer #3
```
PREFIX ex: <http://example.org/>

CONSTRUCT {
  ?student ex:name ?studentName .
  ?student ex:enrolledIn ?course .
  ?student ex:averageGrade ?avgGrade .
}
WHERE {
  {
    SELECT ?student (COUNT(?course) AS ?courseCount) (AVG(?grade) AS ?avgGrade)
    WHERE {
      ?student ex:enrolledIn ?course .
      ?student ex:grade ?grade .
      ?student ex:name ?studentName .
    }
    GROUP BY ?student
    HAVING (COUNT(?course) >= 2)
  }
}
```
 Prompt #4
 
 ```
 Given an RDF dataset of football players, their teams, positions, and goals scored, construct a new dataset containing information about the top 3 goal scorers in the 'Forward' position, along with their team names and total goals scored.
 ```
 
 Dataset #4
 
 ```
 @prefix ex: <http://example.org/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

ex:lionelMessi rdf:type ex:Player .
ex:lionelMessi ex:name "Lionel Messi" .
ex:lionelMessi ex:position "Forward" .
ex:lionelMessi ex:team ex:psg .
ex:lionelMessi ex:goals 25 .

ex:cristianoRonaldo rdf:type ex:Player .
ex:cristianoRonaldo ex:name "Cristiano Ronaldo" .
ex:cristianoRonaldo ex:position "Forward" .
ex:cristianoRonaldo ex:team ex:manchesterUnited .
ex:cristianoRonaldo ex:goals 20 .

ex:robertLewandowski rdf:type ex:Player .
ex:robertLewandowski ex:name "Robert Lewandowski" .
ex:robertLewandowski ex:position "Forward" .
ex:robertLewandowski ex:team ex:bayernMunich .
ex:robertLewandowski ex:goals 30 .

ex:kevinDeBruyne rdf:type ex:Player .
ex:kevinDeBruyne ex:name "Kevin De Bruyne" .
ex:kevinDeBruyne ex:position "Midfielder" .
ex:kevinDeBruyne ex:team ex:mancity .
ex:kevinDeBruyne ex:goals 10 .

ex:psg rdf:type ex:Team .
ex:psg ex:name "Paris Saint-Germain" .

ex:manchesterUnited rdf:type ex:Team .
ex:manchesterUnited ex:name "Manchester United" .

ex:bayernMunich rdf:type ex:Team .
ex:bayernMunich ex:name "Bayern Munich" .

ex:mancity rdf:type ex:Team .
ex:mancity ex:name "Manchester City" .
```
Answer #4

```
PREFIX ex: <http://example.org/>

CONSTRUCT {
  ?player ex:name ?playerName .
  ?player ex:team ?team .
  ?player ex:totalGoals ?totalGoals .
}
WHERE {
  ?player ex:position "Forward" .
  ?player ex:name ?playerName .
  ?player ex:team ?team .
  ?player ex:goals ?totalGoals .
  
  {
    SELECT ?player (SUM(?goals) as ?totalGoals)
    WHERE {
      ?player ex:position "Forward" ;
              ex:goals ?goals .
    }
    GROUP BY ?player
    ORDER BY DESC(?totalGoals)
    LIMIT 3
  }
}
```

Prompt #5

```
Given an RDF dataset of researchers, their institutions, research areas, and publication counts, construct a new dataset containing information about the top researcher from each research area based on publication count, including their names, research areas, institutions, and publication counts.
```
Dataset #5

```
@prefix ex: <http://example.org/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

ex:yoshuaBengio rdf:type ex:Researcher .
ex:yoshuaBengio ex:name "Yoshua Bengio" .
ex:yoshuaBengio ex:researchArea "Artificial Intelligence" .
ex:yoshuaBengio ex:institution ex:mila .
ex:yoshuaBengio ex:publicationCount 500 .

ex:geoffreyHinton rdf:type ex:Researcher .
ex:geoffreyHinton ex:name "Geoffrey Hinton" .
ex:geoffreyHinton ex:researchArea "Artificial Intelligence" .
ex:geoffreyHinton ex:institution ex:uoft .
ex:geoffreyHinton ex:publicationCount 300 .

ex:johnPreskill rdf:type ex:Researcher .
ex:johnPreskill ex:name "John Preskill" .
ex:johnPreskill ex:researchArea "Quantum Computing" .
ex:johnPreskill ex:institution ex:caltech .
ex:johnPreskill ex:publicationCount 250 .

ex:alainAspect rdf:type ex:Researcher .
ex:alainAspect ex:name "Alain Aspect" .
ex:alainAspect ex:researchArea "Quantum Physics" .
ex:alainAspect ex:institution ex:institutOptiqueGraduateSchool .
ex:alainAspect ex:publicationCount 200 .

ex:barrySmith rdf:type ex:Researcher .
ex:barrySmith ex:name "Barry Smith" .
ex:barrySmith ex:researchArea "Ontology" .
ex:barrySmith ex:institution ex:universityAtBuffalo .
ex:barrySmith ex:publicationCount 350 .

ex:mila rdf:type ex:Institution .
ex:mila ex:name "Mila - Quebec Artificial Intelligence Institute" .

ex:uoft rdf:type ex:Institution .
ex:uoft ex:name "University of Toronto" .

ex:caltech rdf:type ex:Institution .
ex:caltech ex:name "California Institute of Technology" .

ex:institutOptiqueGraduateSchool rdf:type ex:Institution .
ex:institutOptiqueGraduateSchool ex:name "Institut d'Optique Graduate School" .

ex:universityAtBuffalo rdf:type ex:Institution .
ex:universityAtBuffalo ex:name "University at Buffalo" .
```
Answer #5
```
PREFIX ex: <http://example.org/>

CONSTRUCT {
  ?researcher ex:name ?researcherName .
  ?researcher ex:researchArea ?researchArea .
  ?researcher ex:institution ?institution .
  ?researcher ex:publicationCount ?publicationCount .
}
WHERE {
  {
    SELECT ?researchArea (MAX(?pubCount) as ?maxPubCount)
    WHERE {
      ?researcher ex:researchArea ?researchArea ;
                  ex:publicationCount ?pubCount .
    }
    GROUP BY ?researchArea
  }
  ?researcher ex:name ?researcherName .
  ?researcher ex:researchArea ?researchArea .
  ?researcher ex:institution ?institution .
  ?researcher ex:publicationCount ?publicationCount .
  FILTER (?publicationCount = ?maxPubCount)
}
```
Prompt #6

```
Given an RDF dataset of cities, their countries, populations, and average annual temperatures, construct a new dataset containing information about the cities with populations greater than 1 million and average annual temperatures below 10°C (50°F), including their names, countries, populations, and average annual temperatures.
```

Dataset #6

```
@prefix ex: <http://example.org/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

ex:moscow rdf:type ex:City .
ex:moscow ex:name "Moscow" .
ex:moscow ex:country "Russia" .
ex:moscow ex:population 12500000 .
ex:moscow ex:averageAnnualTemperature 5.8 .

ex:newYork rdf:type ex:City .
ex:newYork ex:name "New York" .
ex:newYork ex:country "USA" .
ex:newYork ex:population 8400000 .
ex:newYork ex:averageAnnualTemperature 12.7 .

ex:london rdf:type ex:City .
ex:london ex:name "London" .
ex:london ex:country "UK" .
ex:london ex:population 8900000 .
ex:london ex:averageAnnualTemperature 11.6 .

ex:toronto rdf:type ex:City .
ex:toronto ex:name "Toronto" .
ex:toronto ex:country "Canada" .
ex:toronto ex:population 2800000 .
ex:toronto ex:averageAnnualTemperature 9.2 .

ex:buffalo rdf:type ex:City .
ex:buffalo ex:name "Buffalo" .
ex:buffalo ex:country "USA" .
ex:buffalo ex:population 255000 .
ex:buffalo ex:averageAnnualTemperature 9.3 .
```

Answer #6

```
PREFIX ex: <http://example.org/>

CONSTRUCT {
  ?city ex:name ?cityName .
  ?city ex:country ?country .
  ?city ex:population ?population .
  ?city ex:averageAnnualTemperature ?avgTemp .
}
WHERE {
  ?city ex:name ?cityName ;
        ex:country ?country ;
        ex:population ?population ;
        ex:averageAnnualTemperature ?avgTemp .
  FILTER (?population > 1000000 && ?avgTemp < 10)
}
```

