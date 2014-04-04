99 problems in Java
======

This is a Java version of the 99 problems. The 99 problems also have [OCaml version](https://github.com/MassD/99), [Lisp version] (http://www.ic.unicamp.br/~meidanis/courses/mc336/2006s2/funcional/L-99_Ninety-Nine_Lisp_Problems.html).

This README is restructured version of [ocaml.org-99problems] (http://ocaml.org/learn/tutorials/99problems.html).

Though the problems number from 1 to 99, there are some gaps and some additions marked with letters. 

##Arithmetic

1. Determine whether a given integer number is prime. (medium)
2. Determine the greatest common divisor of two positive integer numbers. (medium)

Use Euclid's algorithm.
3. Determine whether two positive integer numbers are coprime. (easy)

Two numbers are coprime if their greatest common divisor equals 1.

4. Calculate Euler's totient function φ(m). (medium)

Euler's so-called totient function φ(m) is defined as the number of positive integers r (1 ≤ r < m) that are coprime to m. We let φ(1) = 1.

Find out what the value of φ(m) is if m is a prime number. Euler's totient function plays an important role in one of the most widely used public key cryptography methods (RSA). In this exercise you should use the most primitive method to calculate this function (there are smarter ways that we shall discuss later).

5. Determine the prime factors of a given positive integer. (medium)

Construct a flat list containing the prime factors in ascending order.

6. Determine the prime factors of a given positive integer (2). (medium)

Construct a list containing the prime factors and their multiplicity. Hint: The problem is similar to problem Run-length encoding of a list (direct solution).

7. Calculate Euler's totient function φ(m) (improved). (medium)

8. Compare the two methods of calculating Euler's totient function. (easy)

9. A list of prime numbers. (easy)

Given a range of integers by its lower and upper limit, construct a list of all prime numbers in that range.

10. Goldbach's conjecture. (medium)

11. A list of Goldbach compositions. (medium)

Given a range of integers by its lower and upper limit, print a list of all even numbers and their Goldbach composition.

In most cases, if an even number is written as the sum of two prime numbers, one of them is very small. Very rarely, the primes are both bigger than say 50. Try to find out how many such cases there are in the range 2..3000.

##Binary Trees

A binary tree is either empty or it is composed of a root element and two successors, which are binary trees themselves.

12.Construct completely balanced binary trees. (medium)

In a completely balanced binary tree, the following property holds for every node: The number of nodes in its left subtree and the number of nodes in its right subtree are almost equal, which means their difference is not greater than one.

13. Symmetric binary trees. (medium)

Let us call a binary tree symmetric if you can draw a vertical line through the root node and then the right subtree is the mirror image of the left subtree. Write a function is_symmetric to check whether a given binary tree is symmetric.

Hint: Write a function first to check whether one tree is the mirror image of another. We are only interested in the structure, not in the contents of the nodes.

14. Binary search trees (dictionaries). (medium)

A. Construct a binary search tree from a list of integer numbers.

B. Then use this function to test the solution of the previous problem.

15. Generate-and-test paradigm. (medium)

Apply the generate-and-test paradigm to construct all symmetric, completely balanced binary trees with a given number of nodes.

How many such trees are there with 57 nodes? Investigate about how many solutions there are for a given number of nodes? What if the number is even? Write an appropriate function.

16. Construct height-balanced binary trees. (medium)

In a height-balanced binary tree, the following property holds for every node: The height of its left subtree and the height of its right subtree are almost equal, which means their difference is not greater than one.

Write a function hbal_tree to construct height-balanced binary trees for a given height. The function should generate all solutions via backtracking. Put the letter 'x' as information into all nodes of the tree.

17. Construct height-balanced binary trees with a given number of nodes. (medium)

Consider a height-balanced binary tree of height h. What is the maximum number of nodes it can contain?

A. Clearly, maxN = 2h - 1. However, what is the minimum number minN? This question is more difficult. Try to find a recursive statement and turn it into a function min_nodes defined as follows: min_nodes h returns the minimum number of nodes in a height-balanced binary tree of height h.

B. On the other hand, we might ask: what is the maximum height H a height-balanced binary tree with N nodes can have? max_height n returns the maximum height of a height-balanced binary tree with n nodes.

C. Now, we can attack the main problem: construct all the height-balanced binary trees with a given nuber of nodes. hbal_tree_nodes n returns a list of all height-balanced binary tree with n nodes.

18. Count the leaves of a binary tree. (easy)

A leaf is a node with no successors. Write a function count_leaves to count them.

18A. Collect the leaves of a binary tree in a list. (easy)

A leaf is a node with no successors. Write a function leaves to collect them in a list.

19. Collect the internal nodes of a binary tree in a list. (easy)

An internal node of a binary tree has either one or two non-empty successors. Write a function internals to collect them in a list.

19A. Collect the nodes at a given level in a list. (easy)

A node of a binary tree is at level N if the path from the root to the node has length N-1. The root node is at level 1. Write a function at_level t l to collect all nodes of the tree t at level l in a list.

20. Construct a complete binary tree. (medium)

A complete binary tree with height H is defined as follows: The levels 1,2,3,...,H-1 contain the maximum number of nodes (i.e 2i-1 at the level i, note that we start counting the levels from 1 at the root). In level H, which may contain less than the maximum possible number of nodes, all the nodes are "left-adjusted". This means that in a levelorder tree traversal all internal nodes come first, the leaves come second, and empty successors (the nil's which are not really nodes!) come last.

Particularly, complete binary trees are used as data structures (or addressing schemes) for heaps.

We can assign an address number to each node in a complete binary tree by enumerating the nodes in levelorder, starting at the root with number 1. In doing so, we realize that for every node X with address A the following property holds: The address of X's left and right successors are 2*A and 2*A+1, respectively, supposed the successors do exist. This fact can be used to elegantly construct a complete binary tree structure. Write a function is_complete_binary_tree with the following specification: is_complete_binary_tree n t returns true iff t is a complete binary tree with n nodes.

21. Layout a binary tree (1). (medium)

As a preparation for drawing the tree, a layout algorithm is required to determine the position of each node in a rectangular grid. Several layout methods are conceivable, one of them is shown in the illustration.

Binary Tree Grid

In this layout strategy, the position of a node v is obtained by the following two rules:

x(v) is equal to the position of the node v in the inorder sequence;
y(v) is equal to the depth of the node v in the tree.
In order to store the position of the nodes, we redefine the OCaml type representing a node (and its successors) as follows:

type 'a pos_binary_tree =
  | E (* represents the empty tree *)
  | N of 'a * int * int * 'a pos_binary_tree * 'a pos_binary_tree
N(w,x,y,l,r) represents a (non-empty) binary tree with root w "positioned" at (x,y), and subtrees l and r.

Write a function layout_binary_tree with the following specification: layout_binary_tree t returns the "positioned" binary tree obtained from the binary tree t.

22. Layout a binary tree (2). (medium)

Binary Tree Grid

An alternative layout method is depicted in this illustration. Find out the rules and write the corresponding OCaml function.

Hint: On a given level, the horizontal distance between neighbouring nodes is constant.

23. Layout a binary tree (3). (hard)

Binary Tree Grid

Yet another layout strategy is shown in the above illustration. The method yields a very compact layout while maintaining a certain symmetry in every node. Find out the rules and write the corresponding predicate.

Hint: Consider the horizontal distance between a node and its successor nodes. How tight can you pack together two subtrees to construct the combined binary tree? This is a difficult problem. Don't give up too early!

24. A string representation of binary trees. (medium)

Binary Tree

Somebody represents binary trees as strings of the following type (see example): "a(b(d,e),c(,f(g,)))".

Write an OCaml function which generates this string representation, if the tree is given as usual (as Empty or Node(x,l,r) term).

Then write a function which does this inverse; i.e. given the string representation, construct the tree in the usual form.

Finally, combine the two predicates in a single function tree_string which can be used in both directions.

Write the same predicate tree_string using difference lists and a single predicate tree_dlist which does the conversion between a tree and a difference list in both directions.

For simplicity, suppose the information in the nodes is a single letter and there are no spaces in the string.

25. Preorder and inorder sequences of binary trees. (medium)

We consider binary trees with nodes that are identified by single lower-case letters, as in the example of the previous problem.

Write functions preorder and inorder that construct the preorder and inorder sequence of a given binary tree, respectively. The results should be atoms, e.g. 'abdecfg' for the preorder sequence of the example in the previous problem.

Can you use preorder from problem part 1 in the reverse direction; i.e. given a preorder sequence, construct a corresponding tree? If not, make the necessary arrangements.

If both the preorder sequence and the inorder sequence of the nodes of a binary tree are given, then the tree is determined unambiguously. Write a function pre_in_tree that does the job.

Solve problems 1 to 3 using difference lists. Cool! Use the function timeit (defined in problem “Compare the two methods of calculating Euler's totient function.”) to compare the solutions.

What happens if the same character appears in more than one node. Try for instance pre_in_tree "aba" "baa".

26. Dotstring representation of binary trees. (medium)

We consider again binary trees with nodes that are identified by single lower-case letters, as in the example of problem “A string representation of binary trees”.

Such a tree can be represented by the preorder sequence of its nodes in which dots (.) are inserted where an empty subtree (nil) is encountered during the tree traversal. For example, the tree shown in problem “A string representation of binary trees” ("a(b(d,e),c(,f(g,)))") is represented as 'abd..e..c.fg...'. First, try to establish a syntax (BNF or syntax diagrams) and then write a function tree_dotstring which does the conversion in both directions. Use difference lists.
