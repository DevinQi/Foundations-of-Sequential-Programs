#Formal Language

###Intruduce to Formal Language
##### Motivation
1. precision of specification and recognition
2. importance of this: every assignment from this point forword
3. benefits of theory:
  * Means of communication(universal)
  * Determine the power and limits of communication
  * guides our pratice => implement and design a compiler

##### Terminology
* **alphabet**:  
a *finite* set of symbol(not necessarily an ASCII character)
* **word** (aka string,sentence):  
*finite* sequence of symbols from the alphabet  
ε (epsilon) means the empty word
* **language**:  
set of word (can be finite or infinite)
* |W|: the size of W (where W is a word or language)

##### Uses of Formal Languages: Specification:
* A statement of what is in the language (Specification):
  * precise (mandatory)
  * easy_to_express (ideally)
  * automatable (ideally)
* Determine if a word is in a language (Recognition):  
Formally: Given a laguage L and a word w, recognition answers the question "Is w belong L?"  
In practice:  
    * no => location and type of error
    * yes => certification of correctness

##### WLP4  
Waterloo Language Plus Pointers Plus Procedures
* alhabet:
  * WLP4 takes : {IF,ELSE,WHILE,GT,LT,...}
* word:
  * WLP$ program: (sequence of tokens)
* language:
  * set of valid WLPH programs
##### Language Classes  
a set of languages may share common characteristics  
Chomsky Hierarchy  
Context-Sensitive-Language > Contact free language > Regular Language > Finite language

##### Organization of Compilation
* lexical analysis
* sytactic analysis
* context-sensitive analysis(semantic) analysis
* synthesis (code generation)

##### Regular Languages
* Defining regular languages: two approache
 1. How to specify a regular language  => construction
 2. how to recognize a regular language
* Specifying Regular Languages:
 1. finite languages
 2. union
 3. concatenation
 4. repetition
* Union:
 * Defination: 
 * Example:  
 T1 = {doge,cat}  
 T2 = {red,blue,dog}  
 Union{T1,T2} = {doge,cat,red,blue}   
* Concatenation:
 * Example:  
 T1 = {dog,cat}
 T2 = {fish,hah}
 T1*T2 = {dogfish,doghah,catfish,cathah}
* Repetition:
 * Example:  
 T1 = {dog,cat}
 T1* = { ε ,dog,cat,dog,cat,catdog,catcat,dogdog,dogcatdog,.......}

##### Recognizers: Finite Automata
* **States** : describes what is true now
* **Transitions** : if i am in state A and read input x move to state B
* **Start State** 
* **Final State** : aka accepting states, if after reading all input are in accepting state,then accept the input

##### Observation About Finite Automata
* ability to trace:
 * picture: only every in one stage at a time
* Transititons out of a state re unique(deterministic)
* errors
* size of language:
* DFA M and language L(M)

##### Forlmal Definition
* finite alphabet
* finite set of states
* start state q0
* set of final acceptng states 
* transition function


 
