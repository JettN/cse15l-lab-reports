# Lab Report 3

## Researching Commands

I decided to choose the `find` command to research. I started by asking ChatGPT for some interesting ways to use the `find` command.
My first interaction is pictured below.

![First ChapGPT Interaction](https://github.com/JettN/cse15l-lab-reports/blob/b84c9ef92b6c007132f94eef5c088c9d281816e0/ChatGPT_find_Command.JPG)

I then asked ChapGPT for some more ways to use the `find` command to see what other options there are.

![Second ChatGPT Interaction](https://github.com/JettN/cse15l-lab-reports/blob/b84c9ef92b6c007132f94eef5c088c9d281816e0/ChatGPT_find_Command_2.JPG)

From the 10 commands-line options for the `find` command that ChatGPT gave me, I chose `-type`, `-exec`, `-mindepth`, and `-empty`.
I also referenced [this website](https://man7.org/linux/man-pages/man1/find.1.html) to understand the command-line options I chose better.

## `-type`

The option `-type` specifies the type of file you want to find.

```
$ find written_2/ -type d
written_2/
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Abernathy 
written_2/non-fiction/OUP/Berk      
written_2/non-fiction/OUP/Castro    
written_2/non-fiction/OUP/Fletcher  
written_2/non-fiction/OUP/Kauffman  
written_2/non-fiction/OUP/Rybczynski
written_2/travel_guides
written_2/travel_guides/berlitz1    
written_2/travel_guides/berlitz2  
```

---

In the example above, I used `-type d` with the find command, which found all of the directories and subdirectories in the directory `written_2/`. This is useful when you want to see if a specific directory exists within a directory or its subdirectories.

```
$ find written_2/non-fiction/OUP/Castro/ -type f
written_2/non-fiction/OUP/Castro/chA.txt
written_2/non-fiction/OUP/Castro/chB.txt
written_2/non-fiction/OUP/Castro/chC.txt
written_2/non-fiction/OUP/Castro/chL.txt
written_2/non-fiction/OUP/Castro/chM.txt
written_2/non-fiction/OUP/Castro/chN.txt
written_2/non-fiction/OUP/Castro/chO.txt
written_2/non-fiction/OUP/Castro/chP.txt
written_2/non-fiction/OUP/Castro/chQ.txt
written_2/non-fiction/OUP/Castro/chR.txt
written_2/non-fiction/OUP/Castro/chV.txt
written_2/non-fiction/OUP/Castro/chW.txt
written_2/non-fiction/OUP/Castro/chY.txt
written_2/non-fiction/OUP/Castro/chZ.txt
```

In the example above, I used `-type f` with the `find` command, which found all of the files in the directory `written_2/non-fiction/OUP/Castro/` and its subdirectories. `written_2/non-fiction/OUP/Castro/` has no subdirectories with files so you do not see any listed in the example above. Using `-type f` with the `find` command is useful if you want to see all files in a directory and its subdirectories. In the case of the `written_2` directory, if you were looking for an article to read but did not have a specific one in mind, then using `-type f` with the `find` command would be perfect as it would provide a list of articles you can choose from to read.

## `-exec`

The option `-exec` executes a command on the files or directories found by `find`.

```
$ find written_2/non-fiction/OUP/Castro/ -name "*.txt" -exec wc {} \;
  140  5858 35815 written_2/non-fiction/OUP/Castro/chA.txt
  155  5447 32974 written_2/non-fiction/OUP/Castro/chB.txt
   54  3857 23689 written_2/non-fiction/OUP/Castro/chC.txt
   53  4070 24529 written_2/non-fiction/OUP/Castro/chL.txt
  145  9213 55555 written_2/non-fiction/OUP/Castro/chM.txt
  58 1513 9240 written_2/non-fiction/OUP/Castro/chN.txt
  47 1454 8396 written_2/non-fiction/OUP/Castro/chO.txt
  110  6693 41580 written_2/non-fiction/OUP/Castro/chP.txt
  24 1368 8298 written_2/non-fiction/OUP/Castro/chQ.txt
   82  5322 33502 written_2/non-fiction/OUP/Castro/chR.txt
   45  3399 19954 written_2/non-fiction/OUP/Castro/chV.txt
  25 1128 6749 written_2/non-fiction/OUP/Castro/chW.txt
  21  911 5445 written_2/non-fiction/OUP/Castro/chY.txt
  21  900 5452 written_2/non-fiction/OUP/Castro/chZ.txt
```

In the example above, I used `-exec` with the `wc` command to find the number of lines, number of words, and number of characters in each `.txt` file in the `written_2/non-fiction/OUP/Castro/` directory. According to [this website](https://www.baeldung.com/linux/find-exec-command), the `{}` after `wc` is a result placeholder which is replaced by the current file name being processed, the `;` tells the `-exec` command to repeat for each result separately, and the `\` is used to escape the semi-colon so it is not interepreted by the shell.

Using `-exec` with the `wc` command is useful if you want to find the wordcount of files in a directory and its subdirectories, but you do not know how many files there are in the directory.

---

```
$ find written_2/ -name "*.txt" -exec grep -l "Lucayans" {} \;
written_2/travel_guides/berlitz2/Bahamas-History.txt
```

In the example above, I used `-exec` with the `grep -l` command to find the file(s) containing the word "Lucayans" in the `written_2/` directory. The `grep -l` command prints only the names of files containing matches to the string input, which is "Lucayans" in this case. Using `-exec` with the `grep` command is useful when you want to find files in a directory and its subdirectories containing a specific string.

## `-mindepth`

The option `-mindepth` specifies the minimum depth for the `find` command to search, with 1 representing the current directory.

```
$ find written_2/ -mindepth 2 -name Castro
written_2/non-fiction/OUP/Castro
```

In the example above, I used `-mindepth 2` to find directories named "Castro" one level down under the `written_2/` directory. This can be useful if you want to find a directories at a specific level and ignore the directories above that level.

---

```
$ find written_2/ -mindepth 4 -name "*.txt"
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Abernathy/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch8.txt
written_2/non-fiction/OUP/Abernathy/ch9.txt
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Berk/ch2.txt
written_2/non-fiction/OUP/Berk/CH4.txt
written_2/non-fiction/OUP/Berk/ch7.txt
written_2/non-fiction/OUP/Castro/chA.txt
written_2/non-fiction/OUP/Castro/chB.txt
written_2/non-fiction/OUP/Castro/chC.txt
written_2/non-fiction/OUP/Castro/chL.txt
written_2/non-fiction/OUP/Castro/chM.txt
written_2/non-fiction/OUP/Castro/chN.txt
written_2/non-fiction/OUP/Castro/chO.txt
written_2/non-fiction/OUP/Castro/chP.txt
written_2/non-fiction/OUP/Castro/chQ.txt
written_2/non-fiction/OUP/Castro/chR.txt
written_2/non-fiction/OUP/Castro/chV.txt
written_2/non-fiction/OUP/Castro/chW.txt
written_2/non-fiction/OUP/Castro/chY.txt
written_2/non-fiction/OUP/Castro/chZ.txt
written_2/non-fiction/OUP/Fletcher/ch1.txt
written_2/non-fiction/OUP/Fletcher/ch10.txt
written_2/non-fiction/OUP/Fletcher/ch2.txt
written_2/non-fiction/OUP/Fletcher/ch5.txt
written_2/non-fiction/OUP/Fletcher/ch6.txt
written_2/non-fiction/OUP/Fletcher/ch9.txt
written_2/non-fiction/OUP/Kauffman/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch10.txt
written_2/non-fiction/OUP/Kauffman/ch3.txt
written_2/non-fiction/OUP/Kauffman/ch4.txt
written_2/non-fiction/OUP/Kauffman/ch5.txt
written_2/non-fiction/OUP/Kauffman/ch6.txt
written_2/non-fiction/OUP/Kauffman/ch7.txt
written_2/non-fiction/OUP/Kauffman/ch8.txt
written_2/non-fiction/OUP/Kauffman/ch9.txt
written_2/non-fiction/OUP/Rybczynski/ch1.txt
written_2/non-fiction/OUP/Rybczynski/ch2.txt
written_2/non-fiction/OUP/Rybczynski/ch3.txt
```

In the example above, I used `-mindepth 4` to find `.txt` files three levels down under the `written_2/` directory. This can be useful if you want to find `.txt` files at a specific level and ignore the `.txt` files above that level.

## `-empty`

The option `-empty` finds all empty files and directories in the current directory andits subdirectories.

```
$ find written_2/ -empty

```

In the example above, I used `-empty` to check if there are any empty files or directories in `written_2/` and its subdirectories. Since it returned nothing, that means that there are no empty file or directories in `written_2/` and its subdirectories. This is useful if a user wants to clean up a driectory by removing empty folders and files.

---

After seeing that there were no empty directories or files in `written_2/`, I created my own empty directories in `written_2/` using the `mkdir` command.

```
$ cd written_2/

$ mkdir emptyDir

$ mkdir emptyDir2

$ cd ..

```

After returning to the directory above `written_2/`, I used `-empty` to see if the empty directories would be found.

```
$ find written_2/ -empty
written_2/emptyDir
written_2/emptyDir2
```

In the example above, `-empty` with the `find` command now returns the two empty directories that I created. However, no empty directories or files were returned from `written_2/`'s subdirectories since I did not create any empty directory in those subdirectories. Again, this is useful if a user wants to clean up a driectory by removing empty folders and files.
