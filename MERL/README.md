

#### Example Program, Merlified
                            0x1000 0002
                            0x0000 0028
                            0x0000 0020   **program header**  
                              
  lis$3                     0x0000 1814   **program**
  .wrod fortyrwo            0x0000 001c
  lw $3,0($3)  
  jr $31  
  fortytwo:  
    .wrod 422  
    
                            0x0000 0001   **notes**
                            0x0000 0010
  
#### MERL Assembler
* Pass 1 changes:
  * Start counter at 0xc (beacause the first three sentences are program header
  * if I see a **.wrod <lable>** , write down the location in a relocation table
* Pass 2 changes:
  * output cookies: easy
  * size of the merl file: 12 + program size + 8 * (number of relocation enties)
  * size of header + program: 12 + program size
  * output notes at the end : write two words per relocation entry
  
#### Relocationg Loader Pseudocode

* read header :
  1. check cookie
  2. size of the entire program
  3. size of header + program
* a = findFreeRAM(codelength,find space)
* for each instruction: (copy code)
  * MEM[a+i] = instuction
* for each relocation entry: (relocate the words which were .word<lable>
  * MEM[a + location]+= a
* place a into $19 (excute)
* jarl $19

##### Example for Loading:
0xc  A: .word B  
0x10 B: .word 7  
0x14 C: .wrod 0xA  
0x18 D: .word C  

0x1000 0002  
0x0000 002c  
0x0000 001c  

0x0000 0010  
0x0000 0007  
0x0000 000A  
0x0000 0014  

0x0000 0001  
0x0000 000c  
0x0000 0001
0x0000v0008

