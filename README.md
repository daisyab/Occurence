Occurence
=========

This program counts the number of occurrences of each word in the complete works of shakespeare.  It has four functions including main().


The first one called in main is the *readfile(char *) function.  This function opens a file(complete-shakespeare)using a system call which will be passed in the terminal, initializes a string pointer to null, then uses the fseek function to move a pointer to the end of the file to determine the size of that file.  The rewind function is then used to bring pointer back to the beginning of the file.  At this point, memory is allocated to store contents of this file.  An extra space is kept to make room for the end of file(EOF) character. After reading the file, a system call closes it.


The second function called is the *bintree function which is recursive.  It is an important function because it arranges the words into a tree structure which reduces runtime when counting is done.  At the beginning, the function takes the first word and initializes it to null.  Space is allocated to the length of word +1(for EOF) by the size of each character (which is machine dependent) and gives the value to the word part of the struct so that the first word is stored into the space. The count now has a value of one and total words is incremented.

If the head(or node) is not null but the word at the node is less than(in terms of charaters) that of the word being considered, bintree() is called and the considered word is stored in the left part of the tree(struct) which itself becomes a node.

Else if the head(node) is greater (in terms of characters) than the considered word, bintreee() is called again but this time the word is stored in the right side of the node. 

If the above three conditions are not fulfilled, the word at the node and the word considered are the same regardless of the case, therefore just the count of the occurence of such word is incremented as well as the total number of words. When there are no more words to read, the program return null.


The third function called is the print_tree function() which simply displays the output of the file.  This function is also a recursive function as well as a stack (last in, first out).  This function prints the words on the tree in alphabetical order using the post order traversal.  If there are some words to read from the tree, then the right most value of the tree is gotten and stored in a stack.  The same is done with the left until all words have been printed.


The main function incorporates all these other functions.  In the beginning of the program everthing is initialized either to 0 or Null.  Then, the readfile() function is called which determines the size of the text and allocates memory for it.  Delimites, which are characters that separate two words from another are initialized by the programmer(me).  Those delimites are used in the strtok function which separates the string into separate words.  The strtok() function does this knowing the size of the file.  While strtok() is separating strings into words, the bintree() function arranges those words in a tree.  Then the total is printed.


Compilation and linking of this program is done.  For compilation and linking, type in the terminal:"gcc -o program Daisy_Nkweteyim_program.c".  When running the program, type in the "./program 'name of file' > Daisy_Nkweteyim_frequency.txt" to run the program and redirect the output to the file Daisy_Nkweteyim_frequency.txt.
