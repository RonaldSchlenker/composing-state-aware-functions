
Titel (Alternativen)
===

> HowTo: Digital Signal Processing in F#
> Benefits of Relative-Addressed State
> Stateful Computations
> Composing State-Aware Functions (as simple as pure functions)
> ...an alternative approach to OOP
> What is state, when should we care about it, and how to deal with it.
> Write Your Own React (in less than 500 LoC)
> Mutable Pure State?

Advertisement
===

* Obscure State


Präsi
===

Einleitung:
  Vide Library
  

* What is state / why we care about / how to deal with?
* (ganz am Anfang)
  * Natural language - Traffic Light - Can we say that "A traffic light has state"? -> Yes.
  * "Can I drive?" - "No, traffic light is red"... "can I drive now"? - "Yes, it's green now"
  * Dissect that conversation - what can we learn?
    * a) Changing values over time:
      *  A traffic light has properties, and their values can change over time.
    * b) Identifyable:
      * Nevertheless, we can talk about "that" traffic light - it's identifyable independent of the changing properties.
    * c) Shared / Revisitable:
      * Different prople can refer to the same thing
      * OR: "that thing" is referencable now, and at another point in time (it's still "that thing").
    * Only if all 3 properties occur together, then it has relevance. This relevance, we express with the word "State".
  * Excurs: OOP
    * OOP is the 3 properties above, with 2 restrictions:
      * (not a real restriction - leave that aside: Programmer has to have a way of state encapsulation)
      * Restrict property "Identifyability": Identifyability by means of absolute adressed locations in a (finite) adress space
    * What if not?
      * -> Identifiability without an adress space, but with rules or relations?
        * What could that mean? Feeling: What are nat. numbers? Zero + Successors.
        * How exactly?


## Brainstorm

* "When do we have to care about state"?
  * JETZT: Überleitung zum Schaltkreis-Bild!
    * we see 2 things
      * Auch reinbringen:
        * (Stateful) blocks are identified not by name or an (absolute) location, but by their relative position inside of a whole structure.
        * (!!!!!) We should stop here and think!
        * What was the definition of an object (REF-1: Das muss vorher rein)?



Nicht vergessen:
---
* Lego: Dou you have to "declare" a lego Brick before using it?
  * "Play instinct" (!!!!) should be encouraged!

TODO
---
* Composing functions is simple, convenient - but not always possible.
* Joke:
  * We don't need existential type, HKTs, type classes, Rank-N types, type families, GADTs.
  * We need only: Plain Old F#, crazy CE stuff, bad ass real world HM-ish type inference



Coding
---

* Absatz: „so will ich es haben“ - wie kommt man hin? Kreativ sein - hier kennen wir es: Task<T>
* Let: = überschreiben. Das geht nicht. Deshalb; let desugar 


Randnotitzen / schon verwendet
---

* Identifyable:
  * usually via a unique location ((absolute) address). Ex.: Traffic light
  * or: an invariant property: Car identity number at frame.
  * IT: Pointer (memory address) / ID (database)

* The "Object"-Approach (als eigener Punlt)
  * Object with minimal interface: Only one method: `unit -> 'v`
  * How dows it look like (show code)?
    * We always have to define a function (ok - not too bad)
    * Definition of instances "up-front" instead of "inline" or "in-place"
      * destroys play instinct
      * Better: ad-hoc
    * manual evaluation before "value" is present:
      * error prone (double evaluations)
  * Is it good / bad?
    * manual evaluation is error prone (double evaluations)
      * no ad-hoc usage of "blocks" possible
