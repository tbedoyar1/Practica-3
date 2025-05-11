# Practica-3

--Thomas Bedoya Rendon & David Guerra Morales--

--Versions used of operating system, compiler and tools--

Frama c 3.0
WSL version: 2.4.13.0
Kernel version: 5.15.167.4-1
WSLg version: 1.0.65
MSRDC version: 1.2.5716
Direct3D version: 1.611.1-81528511
DXCore version: 10.0.26100.1-240331-1435.ge-release
Windows version: 10.0.26100.3775

--FUNCTIONALITY--

The function modifies two integer values via pointers: it adds 3 to the value pointed to by j and 2 to the value pointed to by i. For correct operation, the initial values must satisfy the precondition (*i * *j) + (2 * *j) + (3 * *i) == 0. If this holds true, the function guarantees that after modification, the product of the new values will be 6 (postcondition). For example, inputs (1, -1) become (3, 2), and 3 * 2 = 6 satisfies the postcondition.

This focuses purely on:

What it does (pointer modifications)

Pre/Postconditions (the mathematical rules)

An example (input/output transformation)

--REFERENCES--

-DeepSeek https://chat.deepseek.com


--CODE--

#include <stdio.h>

void ejercicio5(int *i, int *j) {
    *j = *j + 3;
    *i = *i + 2;
}

int main() {

    int a = 1;
    int b = -1;

    printf("Valores iniciales: a = %d, b = %d\n", a, b);
    printf("Comprobación precondición: %d\n", a*b + 2*b + 3*a); 

    ejercicio5(&a, &b); 

    printf("Valores finales: a = %d, b = %d\n", a, b);
    printf("a * b = %d (debería ser 6)\n", a * b); 

    return 0;
}
