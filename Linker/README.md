
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
* What are these "notes of what to change"?
  1. **Relocation entry**:
    * 0x01 <location> what needs updating when loaded
  2. **ESD**:
    * 0x05 <location of label defination>
    * <n character in ASCII>(lable name)
  3. **ESR**:
    * 0x11 <location of where it is used>
    * <n character in ASCII>(lable name)
* Pass 1 and Pass 2 modification
  * Pass 1 Changes:
    * when see a .export <lable>, create a list of "exported names", add <lable> to it
    * find the location of each lable in "exported names"
    * when see a .import <ext_lable>, put in " imported names" table
  * Pass 2 Changes:
    * if a label is not in symbol table,  check the "imported names" table
    * for each exported name => write out and ESD
    * for each .word <ext_label> and beq/bne <ext_label>, write out an ESR
* [Example](https://www.student.cs.uwaterloo.ca/~cs241/slides/linkFred.pdf)

#### Linker Pseudocode

four step to link:
1. **Concatenate the programs**:
  * combine main.merl fred.merl and derf.merl(from the example) => combine.merl
  * Program for combine = P(main.merl) + P(fred.merl) + P(derf.merl)
  * remember the sizes of each program
2. **Construct ESD**:
  * Combine each individual ESD into an gobal ESD
    * add the length of the previous program to each ESD location
  * error check: unique labels defined
3. **Use ESR**
  * For each ESR entry:
    * look up the value in the ESD, if found, add the value to the location appropriately
      * .word => put in the value as a 32-bits pattern
      * beq/ne => compute the 16-bit 2's comp rel offset
    * if not found
      * write out new ESR with new location
4. **Relocate Internally**
  * For each relocation entry
    * add the offset(previous program length) to each relocation entry
    * add the offset(previous program length) to each code value (for internal relation)

* [Pseudocode](https://www.student.cs.uwaterloo.ca/~cs241/slides/link_algorithm.pdf)



#### Static Linking vs. Dynamic Linking
* Static linking example:
  * assemble and link all code => one large executable and self-contained
  * what we just did
* Dynamic linking :
  * do linking at examtion time
    1. Create a string "helper1"
    2. $1 point to the string
    3. lis $29
    4. .word binloarder
    5. jalr $29
  * binloader searches through the library to find helper1
  * put address of helper1 into $3

#### Windows DLLs
* **Dynamic Linked Library**
