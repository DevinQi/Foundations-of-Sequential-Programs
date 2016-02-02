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

#####
