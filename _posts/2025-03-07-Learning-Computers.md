---
layout : post
date : 2025-03-07
title : Learning internals of building a PC
---

[computer from starting up](https://cpu.land/the-basics)
[computerphile explaining CPU](https://www.youtube.com/watch?v=IAkj32VPcUE)
[Inside a CPU](https://www.youtube.com/watch?v=iNfuE3MLmzA)
[blog explaining cpu working](https://www.trentonsystems.com/en-us/resource-hub/blog/what-is-a-cpu)
[compiler explorer](https://godbolt.org/)

# What is a disassembler? and what does that mean? 



# How does a CPU works ?

So this all starts as I wanted to learn how a GPU works and without knowing CPU indepth I wont be able to appreciate GPU enough !! So here we learn how computers work we will write some assembly code , see the flow how that turns out in CPU instruction set and the optimisations made in CPU to reduce time taken !

CPU the most important part / brain of a computer ! 
It has 3 parts that are : 

1. Fetch the instruction from memory
2. Decode the instruction
3. Execute the instruction 


## Fetching the instruction 
Lets say we want to print character on a screen, that in assembly would look like :

```asm 
.LC0:
        .string "Character is "
printme(char):
        push    rbp
        mov     rbp, rsp
        sub     rsp, 16
        mov     eax, edi
        mov     BYTE PTR [rbp-4], al
        mov     esi, OFFSET FLAT:.LC0
        mov     edi, OFFSET FLAT:std::cout
        call    std::basic_ostream<char, std::char_traits<char>>& std::operator<<<std::char_traits<char>>(std::basic_ostream<char, std::char_traits<char>>&, char const*)
        mov     rdx, rax
        movsx   eax, BYTE PTR [rbp-4]
        mov     esi, eax
        mov     rdi, rdx
        call    std::basic_ostream<char, std::char_traits<char>>& std::operator<<<std::char_traits<char>>(std::basic_ostream<char, std::char_traits<char>>&, char)
        mov     esi, OFFSET FLAT:std::basic_ostream<char, std::char_traits<char>>& std::endl<char, std::char_traits<char>>(std::basic_ostream<char, std::char_traits<char>>&)
        mov     rdi, rax
        call    std::ostream::operator<<(std::ostream& (*)(std::ostream&))
        nop
        leave
        ret
```

Here the one's starting with 'r' are the registers !

The fetching stage means, using the address bus ( a 16bit bus / connection that sends the memory address to the CPU ) we fetch the instruction at that memory location .. The memory location is usually a 8byte memory stack laid out !! (If its RAM, then its kinda incorrect !!)

Address bus sends the address to the memory 
Data bus sends back the data to the CPU (which initiated it in the first place) 

## Decoding the instruction ( mention examples in this )
We need to decode the instruction, once we get that instruction from the fetching part we need to then decode it to actually make it usable to the CPU,


## Executing the instruction ( mention examples )
Once decoded we need to execute / carry out that instruction ( i.e. apply maths , wait, get data .. etc) and storing 

## Clock speed ( what ??)


## Threading ( how does that work with examples in assembly) 

## Cores

## Die shots 

`NOT COMPLETING IT !! LEXI HAS WRITTEN WAY TOO GOOD IN CPU LAND CANT BECOME BETTER !`

[SIMD](https://www.youtube.com/watch?v=ulmjqD6Y4do)
## How to program a CPU ?

Single Instruction Single Data 
Single Instruction Multiple Data 

Writing instruction for a CPU in C lang (coding) vs writing SIMD in C how does that matter ? 
arent both the same?

In C, you depend on the compiler's to convert to machine code ( u trust too much on compiler ) that will do it optimally and placce in apt registers for faster  

In SIMD in C, uses SIMD registers that basically fakes CPU to do multiple operation on multiple data at a single time, this is called vectorisation     

Example : 

C code 
```c
for (int i = 0; i < 1000; i++) {
    array[i] = array[i] + 1;  // Adds 1 to each element in the array
}

```

SIMD code :
```c
for (int i = 0; i < 1000; i += 8) {
    __m256i data = _mm256_load_si256(&array[i]);  // Load 8 elements at once
    __m256i result = _mm256_add_epi32(data, _mm256_set1_epi32(1)); // Add 1 to each of 8 elements
    _mm256_store_si256(&array[i], result);  // Store the result back to the array
}

```


# How does a GPU works ?  









