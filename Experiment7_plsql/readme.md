# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80
## Program:
```
DECLARE
    num1 NUMBER := 80;
    num2 NUMBER := 40;
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    END IF;
END;
```
## Output:
<img width="460" height="125" alt="Screenshot 2026-08-24 090028" src="https://github.com/user-attachments/assets/32b6596d-9130-4e5d-ab72-00cd1e6669e4" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55
## Program:
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 10;
    sum NUMBER := 0;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first 10 natural numbers is: ' || sum);
END;
```
## Output:
<img width="592" height="130" alt="Screenshot 2026-08-24 091358" src="https://github.com/user-attachments/assets/7de27f1f-16a1-4475-961a-5ecb3d8f84e2" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
## Program:
```
DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    DBMS_OUTPUT.PUT('Fibonacci sequence: ');

    WHILE i <= n LOOP
        DBMS_OUTPUT.PUT(a);

        IF i < n THEN
            DBMS_OUTPUT.PUT(', ');
        END IF;

        c := a + b;
        a := b;
        b := c;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;
```
## Output:
<img width="567" height="140" alt="image" src="https://github.com/user-attachments/assets/f05d7c65-1dd7-4970-aa19-1764320ad1b1" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351
## Program:
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 1535;
    temp NUMBER;
    digit NUMBER;
    reversed NUMBER := 0;
BEGIN
    temp := n;

    WHILE temp > 0 LOOP
        digit := MOD(temp, 10);
        reversed := reversed * 10 + digit;
        temp := TRUNC(temp / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
```
## Output:
<img width="520" height="147" alt="image" src="https://github.com/user-attachments/assets/8fc0d446-61fc-4f12-810b-62358a649a3e" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15
## Program:
```
SET SERVEROUTPUT ON;

DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a > b THEN
        IF a > c THEN
            largest := a;
        ELSE
            largest := c;
        END IF;
    ELSE
        IF b > c THEN
            largest := b;
        ELSE
            largest := c;
        END IF;
    END IF;

    DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
    DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
```
## Output:
<img width="562" height="155" alt="image" src="https://github.com/user-attachments/assets/7f37756c-1512-4ef8-b993-cd5ceaaa272d" />

## RESULT

Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
