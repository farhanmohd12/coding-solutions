# Pointers in C

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

A document is represented as a collection paragraphs, a paragraph is represented as a collection of sentences, a sentence is represented as a collection of words and a word is represented as a collection of lower-case ([a-z]) and upper-case ([A-Z]) English characters.  
  
You will convert a raw text document into its component paragraphs, sentences and words.  To test your results, queries will ask you to return a specific paragraph, sentence or word as described below.  
  
Alicia is studying the C programming language at the University of Dunkirk and she represents the words, sentences, paragraphs, and documents using pointers:  
  
- A word is described by $\texttt{char*}$.
- A sentence is described by $\texttt{char**}$. The words in the sentence are separated by one space (" "). The last word does not end with a space(" ").
- A paragraph is described by $\texttt{char***}$. The sentences in the paragraph are separated by one period (".").
- A document is described by $\texttt{char****}$. The paragraphs in the document are separated by one newline("\n"). The last paragraph does not end with a newline.

For example:  
> Learning C is fun.	
Learning pointers is more fun.It is good to have pointers.

- The only sentence in the first paragraph could be represented as:

```c
char** first_sentence_in_first_paragraph = {"Learning", "C", "is", "fun"};
```

- The first paragraph itself could be represented as:

```c
char*** first_paragraph = {{"Learning", "C", "is", "fun"}};
```

- The first sentence in the second paragraph could be represented as:

```c
char** first_sentence_in_second_paragraph = {"Learning", "pointers", "is", "more", "fun"};
```

- The second sentence in the second paragraph could be represented as:

```c
char** second_sentence_in_second_paragraph = {"It", "is", "good", "to", "have", "pointers"};
```

- The second paragraph could be represented as:

```c
char*** second_paragraph = {{"Learning", "pointers", "is", "more", "fun"}, {"It", "is", "good", "to", "have", "pointers"}};
```

- Finally, the document could be represented as:

```c
char**** document = {{{"Learning", "C", "is", "fun"}}, {{"Learning", "pointers", "is", "more", "fun"}, {"It", "is", "good", "to", "have", "pointers"}}};
```

Alicia has sent a document to her friend Teodora as a string of characters, i.e. represented by $\texttt{char*}$ not $\texttt{char****}$. Help her convert the document to $\texttt{char****}$ form by completing the following functions:  

- $\texttt{char**** get_document(char* text)}$ to return the document represented by $\texttt{char****}$.  
- $\texttt{char*** kth_paragraph(char**** document, int k)}$ to return the $k^{th}$ paragraph.   
- $\texttt{char** kth_sentence_in_mth_paragraph(char****document, int k, int m)}$ to return the $k^{th}$ sentence in the $m^{th}$ paragraph.    
- $\texttt{char* kth_word_in_mth_sentence_of_nth_paragraph(char**** document, int k, int m, int n)}$ to return the  $k^{th}$ word in the $m^{th}$ sentence of the $n^{th}$ paragraph.  

**Input Format**

The first line contains the integer $paragraph\_count$.   
Each of the next $paragraph\_count$ lines contains a paragraph as a single string.  
The next line contains the integer $q$, the number of queries.   
Each of the next $q$ lines or groups of lines contains a query in one of the following formats:  

- 1 The first line contains $1 \enspace k$:    
	* The next line contains an integer $x$, the number of sentences in the $k^{th}$ paragraph.  
	* Each of the next $x$ lines contains an integer $a[i]$, the number of words in the $i^{th}$ sentence.  
	* This query corresponds to calling the function $\texttt{kth_paragraph}$.   
  
- 2 The first line contains $2 \enspace k \enspace m$:   
	* The next line contains an integer $x$, the number of words in the $k^{th}$ sentence of the $m^{th}$ paragraph.  
	* This query corresponds to calling the function $\texttt{kth_sentence_in_mth_paragraph.}$ 

- 3 The only line contains $3 \enspace k \enspace m \enspace \ n$:    
	* This query corresponds to calling the function $\texttt{kth_word_in_mth_sentence_of_nth_paragraph.}$  


**Constraints**

- The text which is passed to the $\texttt{get_document}$  has words separated by a space (" "), sentences separated by a period (".") and  paragraphs separated by a newline("\n").   
- The last word in a sentence does not end with a space.
- The last paragraph does not end with a newline.  
- The words contain only upper-case and lower-case English letters.  
- $ 1 \enspace \le \enspace $ number of characters in the entire document $  \enspace \le \enspace 1000 $   
- $ 1 \enspace \le \enspace $ number of paragraphs in the entire document $  \enspace \le \enspace 5 $   


**Output Format**

Print the paragraph, sentence or the word corresponding to the query to check the logic of your code.

## Solution

**Language:** C  
**Runtime:** N/A  
**Memory:** N/A  
**Submitted:** 2026-10-06T15:42:43.415Z  

```c
#include <stdio.h>

void update(int *a, int *b) {
    int sum = *a + *b;
    int diff = *a - *b;

    if (diff < 0)
        diff = -diff;

    *a = sum;
    *b = diff;
}

int main() {
    int a, b;

    scanf("%d", &a);
    scanf("%d", &b);

    update(&a, &b);

    printf("%d\n%d\n", a, b);

    return 0;
}

```

---

[View on HackerRank](https://www.hackerrank.com/challenges/querying-the-document/problem)