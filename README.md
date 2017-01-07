# AutoCompleateME
Implementation of autocomplete algorithm



## Implementation description
The implementation based on [Trie](https://en.wikipedia.org/wiki/Trie) data structure. 
Each [`Node`](https://github.com/aldonin/T9_spelling/blob/master/src/node.h) contain `isEnd` flag which shows if there is a separate word which stops on currect character.

For example: 

![alt text](https://github.com/aldonin/T9_spelling/blob/master/img/trie.png "Trie example")


Nodes with `isEnd` flag is marked with double round. We see 13 nodes(including empty root node), which represent 5 names:
 - Joe
 - John
 - Johnny
 - Jane
 - Jack

As we can see 'John' name stops on 'N' character, however we have more long 'Johnny' name, that's why we have one more pointer to another character of 'John**n**y' name (next 'N' character). So `isEnd` flags doesn't mean the end of all words started with that prefix.

`Trie` class contain three methods:
 - *insert* new word
 - *PrefixSearch* word with specified prefix
 - *PrintChildern* print all possible paths for specified node

`Trie::insert` try to find if the trie is already contain this word or part of word. We iterate thought character and try to find any children of current node with iterating character. If there is no more children, we find the parent node which represents the longest word of trie as a part of inserting word. After that, if we still have some non-iterating character we add them into the trie. And marked the last character in the trie with `isEnd` flag.

`Trie::PrefixSearch` firstly try to find the last node which corresponds the full prefix as every node holde character and path of the previous nodes

`Trie::PrintChildern`Print all of the results that taken from PrefixSearch'

One of the possible way to fill trie is using dictionary
```c#
 string[] words = System.IO.File.ReadAllLines(@"D:\New folder\Large\Dictionary (Large).txt"); // Read all words from dictionary
                 foreach (string word in words)
                 {
                     trieobject.InsertWord(word); // Insert words in trie
                 }
```

