Download Link: https://assignmentchef.com/product/solved-racket-programming-part-2
<br>
This assignment is designed to give you experience with structures and higher-order functions written in Racket. Again, you will write several, small functions.General Requirements:o Use only those functions that are available in DrRacket using the “Intermediate Student with lambda” language.o In all of the functions, it is important that your solution be reasonably efficient. For example, an O(n2) solution will lose points if there is an obvious O(n) solution. In particular, be careful of using append and length since both of these are O(n) operations.Problem 1 [5 points]:Write a function dot-product : list(num) X list(num) – numThis function is to take two lists of numbers (either integers or floats) and return the sum of the products. For instance, (dot-product ‘(1 2 3) ‘(4 5 6)) would return 32.Assume both lists have the same length. Your solution must use higher-order functions instead of recursion, and you cannot define auxiliary named functions. The restriction against auxiliary functions forces using lambda.Hint: map can take as many number of lists as parameters as the number of arguments the mapped operation can take.Problem 2 [5 points]:Write a function home-wins. The structure(define-struct results (home away))records the results of NBA matches. Given a list of results, home-wins will return the number of times the home score was strictly greater than the away score. For example, given(define s1 (list (make-results 92 98)(make-results 89 110)(make-results 82 71)(make-results 96 80)(make-results 103 103)))(home-wins s1) would return 2. Again, do not use recursion or auxiliary functions. Use higher-order functions with lambda instead.Problem 3 [5 points]:above-average: given a list of numbers, above-average returns those which are strictly greater than the average of the list. For example, (above-average ‘(5 8 3 5 9 0)) would return the list ‘(8 9). (above-average ‘(3)) and (above-average empty) should both return empty lists.As above, use lambda rather than writing auxiliary functions.Problem 4 [5 points]:values-by-layers: To use structure to represent a binary tree, you may need two definitions:(define-struct node (value left right))(define-struct tip ()) ;; empty nodeWrite a function values-by-layers which returns all values in such a tree as a list with those elements in a top-down and left-right order. The first value will be the value at the root (layer 0); the next two will be the values at layer 1, assuming they all exist; the next ones will be the values at layer 2, and so on. Within each layer, always list the values in a left-to-right order. For example, (values-by-layers (make-node 20 (make-node 13 (make-tip) (make-node 19 (make-tip) (make-tip))) (make-node 2 (make-node 105 (make-tip) (make-tip)) (make-tip))))will return the list (20 13 2 19 105)One solution to this problem is similar as a breath first traversal, in which we keep a list of subtrees that remain to be processed in a queue. Initially the queue would contain the whole tree. Add the value of the first node in the queue to the result, then add the subtrees of that node to the end of the queue.Note: you can use a list to implement a queue. It is ok to implement a O(n2) queue because O(n) queue in pure “scheme” is difficult.Submission guideline:o Submit your source code named “lab3-username.rkt” to S:CoursesCSSEshiycs30301Dropboxo 2 point penalty for each day being late. Your submission will not be accepted more than 3 days late.o If one of your functions won’t load, comment it out so you can at least get partial credit for the other functions.o I expect you to present your solutions in a well-formatted way. Also, you must document every function you write with its prototype and a line or two describing what it does.o You can use the following test cases to make sure your code works:(check-expect (dot-product ‘(7 10 -3 2.2) ‘(3.5 8 0 1)) 106.7)(check-expect (home-wins (list (make-results 109 98))) 1)(check-expect (home-wins (list (make-results 95 98)(make-results 89 100)(make-results 92 81)(make-results 106 90)(make-results 83 83))) 2)(check-expect (above-average ‘(3 -6 9 12 0 44)) ‘(12 44))(check-expect (above-average empty) empty)(check-expect (above-average ‘(5)) empty)(define t1 (make-node ‘a(make-node ‘b (make-tip) (make-tip))(make-tip)))(define t2 (make-node 20(make-node 13(make-tip)(make-node 19 (make-tip) (make-tip)))(make-node 2(make-node 105 (make-tip) (make-tip))(make-tip))))(check-expect (values-by-layers t1) ‘(a b))(check-expect (values-by-layers t2) ‘(20 13 2 19 105))(check-expect (values-by-layers (make-tip)) empty)