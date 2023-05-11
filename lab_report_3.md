# Lab Report 3
## Lin Zhou
## A16416268
## CSE 15L
*Command line options for `grep`*

# Command line option `-n`
`-n` option helps user to print the line numbers where the pattern was found.[^1][^2]

Here is an example of using `-n` on the file `/technical/911report/chapter-1.txt`

```
#Here is the code
grep -n "heading to an airport" technical/911report/chapter-1.txt
```
```
#Here is the output
8:    For those heading to an airport, weather conditions could not have been better
for a safe and pleasant journey. Among the travelers were Mohamed Atta and Abdul 
Aziz al Omari, who arrived at the airport in Portland, Maine.
```
This code finds the texts `'heading to an airport'` and its line number in the txt file `technical/911report/chapter-1.txt`, and then
print the line number first(*which is `8`*) and following with `: ` and the texts it found inside the txt file.

Here is another example:
```
#Here is the code
find technical/911report > find-results.txt
grep -n "chapter-13" find-results.txt
```
```
#Here is the output
2:technical/911report/chapter-13.4.txt
3:technical/911report/chapter-13.5.txt
4:technical/911report/chapter-13.1.txt
5:technical/911report/chapter-13.2.txt
6:technical/911report/chapter-13.3.txt
```
This code first find all the txt files in side the dictionary `technical/911report` and save them inside the `find-results.txt` file using `>` command.
Then I use `grep -n` to find the all text with pattern of `chapter-13` inside the `find-results.txt` associated with the line number at the front of each line it printed.(*which are `2`, `3`, `4`, `5`, `6`*)

`grep -n` is quite useful as it could show the line number that the pattern was found, which could help us locate the text much faster and gives us a brief distribution of the text inside the text file we explored.


---
# Command line option `-i`
`-i` option helps user to find the pattern inside the txt file ignoring cases(*case-insensitive search*)[^1][^2]

Here is an example of using `-i` on the file `/technical/911report/chapter-1.txt`
```
#Here is the code
grep -i -n "Homeland" technical/911report/chapter-1.txt
```
```
#Here is the output
210:IMPROVISING A HOMELAND DEFENSE
724:    The details of what happened on the morning of September 11 are complex, 
but they play out a simple theme. NORAD and the FAA were unprepared for the type 
of attacks launched against the United States on September 11, 2001. They struggled,
under difficult circumstances, to improvise a homeland defense against an unprecedented 
challenge they had never before encountered and had never trained to meet.
```
This code is finding `Homeland` inside the txt file `technical/911report/chapter-1.txt`. Since this code has command option -i, which means that
it is searching 'homeland' regardless the cases. Thus, inside the output, it finds two matches: `HOMELAND` and `homeland` in that two lines. Besides, this
code also contians `-n`, which produce the line number in front of each printed output. 


Here comes another example:
```
#Here is the code
find technical/911report > find-results.txt
grep -i "Chapter-12" find-results.txt
```
```
#Here is the output
technical/911report/chapter-12.txt
```

This code first find all the txt files in side the dictionary `technical/911report` and save them inside the `find-results.txt` file using `>` command.
Then use `grep -i` to find any text that matches `Chapter-12` regardless the case. And this gives the result `technical/911report/chapter-12.txt`, which `chapter-12` matches our search.


`grep -i` could be quite useful when we want to search some words without caring about its cases. For example, some words might at the beginning of the sentance, which has its initial capitalized,
but writing duplicate commands to find all possible uppercases of that word is a lot of work and thus `grep -i` would be quite helpful to search for all that words regardless the cases.



---
# Command line option `-c`
`-c` option helps user to find how many lines contains text that matches the pattern and only output the count of lines[^1][^2]

Here is an example of using `-c`:
```
#Here is the code
find technical/911report > find-results.txt
grep -c "chapter-13" find-results.txt
```
```
#Here is the output
5
```

This code still redirects all the files inside the `technical/911report` to the txt file called `find-results.txt` and then 
using `grep -c` to count how many lines contains `chapter-13` inside the `find-results.txt`, which is 5.
> They are
> ```
> technical/911report/chapter-13.4.txt
> technical/911report/chapter-13.5.txt
> technical/911report/chapter-13.1.txt
> technical/911report/chapter-13.2.txt
> technical/911report/chapter-13.3.txt
> ```

Here comes another example:
```
#Here is the code
grep -c -i "Homeland" technical/911report/chapter-1.txt
```
```
#Here is the output
2
```

This code as I did in `grep -i` example 1, it finds all the lines contains `Homeland` regardless the cases and then `grep -c` makes this code to return the number of lines contains that pattern, which is 2 as we showed above.


`grep -c` is quite useful since it does some similar job as `wc` does but in a more flexiable way since it could combine other option command associated with `grep` such as `-i`, `-v`(we would discuss in next part), and etc. Besides, it is also a good tool to keep track the appearance of some certain pattern inside the txt file.



---
# Command line option `-v`
`-v` option helps user to print lines that does not match the pattern. [^1][^2]

Here is an example of using 'grep -v':
```
#Here is the code
find technical/911report > find-results.txt
grep -v "chapter-1" find-results.txt
```
```
#Here is the output
technical/911report
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
```

This code still redirects all the files inside the `technical/911report` to the txt file called `find-results.txt` and then 
use `grep -v` to find and print all the lines that does not match the pattern(*does not contain `chapter-1`*)


Here is another example:
```
#Here is the code
find technical/911report > find-results.txt
grep -v "chapter" find-results.txt
```
```
#Here is the output
technical/911report
technical/911report/preface.txt
```

This code still redirects all the files inside the `technical/911report` to the txt file called `find-results.txt` and then 
use `grep -v` to find and print all the lines that does not contain `chapter`


`grep -v` is quite useful when we want to filtering some patterns, in our case, like `chapter` and etc. When we want to find lines that does not contain some pattern, `grep -v` would be quite helpful. For example, when we want to count how many files in the `technical/911report` that does not contains `chapter`, we could use 
```
find technical/911report > find-results.txt
grep -c -v "chapter" find-results.txt
```
This would print 2 since there are only two files that does not contain `chapter`(`technical/911report` and `technical/911report/preface.txt`)


[^1]:[Grep - Wikibooks](https://en.wikibooks.org/wiki/Grep)
[^2]:[ChatGPT](https://chat.openai.com/) by searching `show me some grep command line options and examples`
