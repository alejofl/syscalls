# syscalls
System Calls and ASM documentation for easy access.

* [Cartilla ASM](https://alejofl.github.io/syscalls/cartilla/IntelCodeTable.pdf)

## 32-bit

* [System Calls x86](https://alejofl.github.io/syscalls/x86/)

* Registros
<img src="https://www.cs.virginia.edu/~evans/cs216/guides/x86-registers.png" width="70%">

* **Los argumentos se pasan a las funciones por el Stack**

* Registros a preservar entre funciones
  * ebx
  * esi
  * edi
  * ebp
  * esp

* **El valor de retorno se retorna por EAX**

## 64-bit

* [System Calls x86_64](https://alejofl.github.io/syscalls/x86_64/)

* Registros
<img src="https://cs.stanford.edu/people/eroberts/courses/soco/projects/2005-06/64-bit-processors/current2_clip_image002.jpg" width="70%">

* **Los argumentos se pasan a las funciones por parámetros en primera instancia, y luego por el stack**
  * Clasificación de datos:

    | Dato | En C |
    | --- | --- |
    | INTEGER | char, short, int, long, void \* |
    | SSE | float, double |
    | MEMORY | datos más grandes que 4 bytes |
  
  * Luego se pasan de la siguiente forma:

    | Dato | Registro (en ese orden) |
    | --- | --- |
    | INTEGER | rdi, rsi, rdx, rcx, r8, r9 |
    | SSE | xmm0, xmm1, xmm2, xmm3, xmm4, xmm5, xmm6, xmm7 |
    | MEMORY | por Stack |

* Registros a preservar entre funciones
  * rbp
  * rsp
  * rbx
  * r12
  * r13
  * r15 

* **El valor de retorno se retorna de la siguiente manera**
  * Si el dato es \_\_, se retorna:

    | Dato | Se retorna |
    | --- | --- |
    | INTEGER | rax y rdx |
    | SSE | xmm0 y xmm1 |
    | MEMORY | por Stack |
