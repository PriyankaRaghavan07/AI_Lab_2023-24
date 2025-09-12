# Ex.No: 5   Logic Programming – Factorial of number   
### DATE:   12/09/2025                                                                         
### REGISTER NUMBER : 212223060213

### AIM: 
To  write  a logic program for finding the factorial of given number using SWI-PROLOG. 
### Algorithm:
1. STEP 1: Start the program
2. STEP 2:  Write a rules for finding factorial of given program in SWI-PROLOG.
3.   a)	factorial of 0 is 1 => written as factorial(0,1).
4.   b)	factorial of number greater than 0 obtained by recursively calling the factorial    function.
5. STEP 3: Run the program  to find answer of  query.
6. STEP 4: Stop the program.

### Program:

```
% Base case: factorial of 0 is 1
factorial(0, 1).

% Recursive case: factorial(N) = N * factorial(N-1)
factorial(N, F) :-
    N > 0,
    N1 is N - 1,
    factorial(N1, F1),
    F is N * F1.

```


### Output:
<img width="959" height="299" alt="image" src="https://github.com/user-attachments/assets/47a73235-1bb5-4e47-abf7-b5f83ac5b0f1" />



### Result:
Thus the factorial of given number was found by logic programming. 
