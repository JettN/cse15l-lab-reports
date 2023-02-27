# Lab Report 4

## 4. Log into ieng6
Keys Pressed: `<Ctrl-R>` `s` `<enter>`

I used `<Ctrl-R>` to search my command history. By pressing `s` while searching my command history, bash autocompletes `s` to `ssh cs15lwi23amn@ieng6.ucsd.edu` (a command which will log me into ieng6) and I just have to press `<enter>` to get bash to run that command.

![Task_4](Task 4.PNG)

## 5. Clone your fork of the repository from your Github account

Keys Pressed: `git clone` `<space>` `<Ctrl-V>` `<enter>`

I typed `git clone` as `git clone` is the command used to clone a repository. Then I pressed `<space>` to create a space after `git clone` and pressed `<Ctrl-V>` to paste the SSH url. Then I pressed `<enter>` to run the full command `git clone git@github.com:JettN/lab7.git`.

![Task5_Git_Clone](Task5_Git_Clone.PNG)

## 6. Run the tests, demonstrating that they fail

Keys Pressed: `cd l` `<tab>` `<enter>` `<Ctrl-R>` `ja` `<enter>` `<Ctrl-R>` `java` `<space>` `<enter>`

After cloning my fork of the repository from my GitHub account, I typed `cd l` into my terminal then pressed tab to autocomplete that line to `cd lab7/` and pressed enter to execute that command. Then I used `<Ctrl-R>` and typed `ja` which brought up `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`. I then pressed `<enter>` to run that command. Once the command ran, I used `<Ctrl-R>` and typed `java` then pressed `<space>` which brought up `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples`. I then pressed `<enter>` to run that command which provided the response below.

![Task6](Task6.JPG)

## 7. Edit the code file to fix the failing test

Keys Pressed: `<Ctrl-R>` `na` `<enter>` `<down>` x42 times(held down key) `<right>` x12 times `<backspace>` `2` `<Ctrl-O>` `<enter>` `<Ctrl-X>`

The image below shows the fixed file with my cursor next to the location I made the fix.

![Task7](Task7.JPG)

## 8. Run the tests, demonstrating that they now succeed


## 9. Commit and push the resulting change to your Github account (you can pick any commit message!)

