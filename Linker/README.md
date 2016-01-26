
#### Combining Programs
* **Reason**: divide up a task into modules/functions, and at some point, need to combine solutions togethe 
* Combining programs Option:
  1. **Concatenate** (cat):
    * Productivity: require all programs before assembling
    * Bug traclaing: difficult to find the origin of bugs
    * Duplicate lables possible!
  2. **Linker**:  
  main.asm => assembler => main.merl  |  
  fred.asm => assembler => fred.merl  |     linker => combinethem  => loader    
  derf.asm => assembler => derf.merl  |    
    * undefine symbol
  3. **Modifying the assembler**: 
    * look at the MERL format again: ESR and ESD:
      * ESD: external symbol definition
      * ESR: external symbol reference
    * the .import and .export directives
* [Example](https://www.student.cs.uwaterloo.ca/~cs241/slides/linkFred.pdf)
