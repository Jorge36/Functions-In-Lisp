**5 Functions in Lisp**

**Exercise 1**

Write a function divisibleBy which takes two arguments, a number N and a list of numbers L,  and returns a new list containing all numbers X in the list L where either X divides N exactly, or N divides X exactly.  You can assume that all numbers will be integers, and you can assume that the input  number N will never be 0 (but numbers in the list L may be 0).
You probably want to use the built-in modulo function here.  The call (modulo X N) gives the remainder you get after dividing X by N.  
For example, the call 
(divisibleBy 10 '(4 30 11 5 0)) 
returns the list  (30 5 0) because 10 divides 30 exactly  (3*10=30), 5 divides 10 exactly (5*2=10), and 10 divides 0 exactly (10*0 = 0).  
A hint:  Notice a mathematical quirk here:  every number E divides exactly into 0: (modulo 0 E)=0 for all possible numbers E, but you cannot divide a number by 0: (modulo E 0) will give a "divide-by-zero" error.   This means that you will need to add a special case to your function to "catch" the situation where an element (car L) in the list L is equal to 0, to make sure you don't call (modulo E (car L)).

For example:
Test	Result
1. (divisibleBy 10 '(4 30 11 5 0)) => (30 5 0)
2. (divisibleBy 6 '(2 6 1 9 18) ) =>	(2 6 1 18)

**Exercise 2**

A plaindrome is a sequence that is symmetrical: it reads the same in forward and in reverse order.  The numbers 11, 131, 14541 are all palindromes, for example.   
In scheme we can distinguish between two types of palindromes: simple palindromes and structured palindromes.   Simple palindromes involve only flat lists (lists with no sublists) and are symmetrical in their elements. Examples of simple palindromes are the lists.

1.	 '(a a)
2. '(a b a) 
3.	'(a b b a)  
4.	'(a b a b a)

Structured palindromes involve lists with sublists, and are symmetrical both in elements and their structure.  Examples of structured palindromes are the lists

1.	'( (a b) a (b a) ) 
2.	  '(a (b c) (c b) a)
3.	 '( a (b () b) a)
4.	 '(a b a)

Note that lists such as '( (a b) a b a) are symmetrical in terms of their sequence of elements, but not in terms of their structure: these are not structured palindromes. Write a function (isPalindrome L) that takes a list L and returns true if L is a simple or structured palindrome and false otherwise.   

For example:
Test	Result
1. (isPalindrome '(a b a) ) => t	
2. (isPalindrome  '(a (b c) (c b) a)) => t
3. (isPalindrome  '(a (b c) ((c) b) a)) =>	nil
4. (isPalindrome '(a (b (c d)) ((c d) b) a ) ) => nil

**Exercise 3**

The reverse() method reverses the elements of a list.

For example:
Test Result
1. (reverse-aux '(1 2 3 (5 6) ((7 (8))))) => (((7 (8))) (5 6) 3 2 1)
2. (reverse-aux '()) => NIL
3. (reverse-aux '(1 2 3 (6) (9) 34 5)) => (5 34 (9) (6) 3 2 1)

**Exercise 4**

Write a Lisp function duplicate-entries that takes a list and returns true if it contains multiple copies of some entry, and NIL otherwise. Be sure to handle nested lists properly. You can do this recursively, or my using the mapping functions. For example, maplist. Did you know that member takes an optional argument, :TEST, followed by a function to be used for testing 
equality? For example, (member thing1 thing2 :TEST #’equal). This will often be VERY useful.

For example: 
Test Result
1. (duplicate-entries '((a) (c) (b))) => nil
2. (duplicate-entries '(1 (1 2 (4) (1 2 3)) (1 2 (5) (1 2 3)) 1)) => t
3. (duplicate-entries '((a) (2) (b) (z (2)))) => nil
4. (duplicate-entries '((a) (c) (b) (z (c)) (c))) => t
5. (duplicate-entries '(a b (a) c d)) => nil
6. (duplicate-entries '((a b) b c (a b))) => t

**Exercise 5**

Define (has-number-p s-exp) to return true if the s-expression is or contains a number.
Implement this using a simple conditional, recursion, and SOME. Letting SOME do some of the work is more efficient than a pure CAR-CDR recursive solution.

For example: 
Test Result
1. (has-number-p '(b c d (3))) => t
2. (has-number-p '(a (b 2) c)) => t
3. (has-number-p '(a (b) c)) => nil
4. (has-number-p '(a (b 3))) => t
5. (has-number-p 5) => t
6. (has-number-p 'hello) => nil
