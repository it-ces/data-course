# Basic in Linux

to see what shell type in your terminal;

```bash
echo $SHELL
```
```bash
bash --version
```
if you have bash you can see the currently installed version.

cd it is the command to establish the current folder of work,
for instance put in the root of system:
```bash
cd \
```
while, fhe following put in Documents folder
```bash
cd ~/Documents
```
## Relative and absoulte path

```bash
  folderRoot
    /   \
   /     \
folderA  folderB
```
To see where you are on,  uses
```bash
pwd
```
if we want establish our working directory in _folderB_ we must
uses a absolute path in the following way.
```bash
cd \home\user\folderRoot
```
but if we want to change to folderA we can uses a relative path using
```bash
cd ../folderA
```
then if we need for instance come back to folderRoot we only need type
```bash
cd ..
``
## Variables
Bash recognize variable=value, does not variable = value.
for instance.

```bash
figure=square
```
## reserved keywods
**for** x to indicate the interator.
**in** to give a explicity list of arguments.
**do** is used to loop over positional objetcts.

Note: when you are typing in terminal could be useful 
to know that: 
ctrl-a put the cursos to beginning of line.
ctrl-e put the cursor at the end of line.

in script you can comment one line
```bash
# comment one line
# comment two line
```

multiple lines
```bash
: '
one line
two lines
three lines
'
```
the command which show us the path of a command.
for instance:
```bash
which bash
which ls
```
the string variable will be executed with $name
it is important remark that $(ls) means shell execution.
```bash
ls='word_!'
echo $(ls) 
echo $ls
```
Thus the second line, execute de command, otherwise the third line print the variable ls that containt word_!.
due the modularity of the bash programming functions are very handy.
function_name(){
    expressions
}

for instance;
lvim(){
ls > texto.txt
vim texto.txt
}

Sometimes we need interact with input or macros, in the following example
we used the for loop. 
for i in /home/ces/courses/notes/*
do
echo $i 
done 
this will be very handy to operate over files systematically. 

The following function will be return a file
tha contain the number of line of the documents in a folder.

wd_doc(){
    dic="$(pwd)/*" 
    for x in $dic
    do 
    wc $x > count_FILE.txt
    vim count_FILE
    done
}

Note: if you are using screen remember that we can alter screen with 
ctrl + a, shift +a and change the config with :SlimeConfig inside of vim.

echo "hello world"

we can put a single send of command using \ for instance;
echo line 1 \
line 2 \
line 3

echo $(pwd)
echo hello

echo allow us the tag -e to init to give to parse especial characters as \n new line.

echo "in this text \n here beging a new line"
echo -e "in this text \n here begin a new line"

seq allow us print sequences. here %g means integer.

```bash
seq -f 'this is a string format as in C, we will see the following %g' 10
```

seq have a general syntax (which?) 

the command echo without arguments allow us  create an empty file.

echo > empty_file.1

cat > out.1 <<CES
CustomerID, Customer
   1, Customer A
   2, Customer B
CES

cat is usually used to concatenate files.

see the following code and try of understand what happend.
```bash
head -n # file_name.
for x in {1..4}
do 
seq -f "the number will be %g"  1 1 $x > file_seq$x.txt
ls | grep file > summary.txt
dic="$(pwd)/file_seq*.txt"
done
```
```bash
for t in $dic 
do
head -n 1 $t
done 
cat file_seq*
```
the previous one example was a case of no nested loop example.
Note: in a single line, multiple statemensts are allowed with ; 

cat line1.txt line2.txt  | sort -V
to sort in numerical values within the text.
cat > line2.txt <<CES
line 99
line 101
line 98
line 120
line 100
line 119
line 118
CES

note that > overwrite the document while >> append to the document.
seq -f 'line %g' 5 > lab1.txt
seq -f 'line %g' 5 >> lab1.txt

cat lab1.txt | sort | uniq

grep is a command to search text using regular expression.

seq 20 | grep #
print only the numbers with #.

seq 20 | grep ^#
print only the numbers that beging with #.

Note: grep can be combined with $ ^ the first to match at the end of line, and caret to the beging of line.

seq -f ' Numbers %g' 41

important flags,
-r make a recusive search in currently directory.

## tr (tranlate or delete characters)

## Cut command  (research)

Note: Before you can execute a script we must execute:
```bash
chmod +x file.sh
./file.sh
```
```bash
bash file.sh
```
The first way need give permission to execute the file, 
and you should include a shebang #!/bin/bash.


Note= you must avoid UPPERCASES to define variables, due this way 
is used for internal shell variables.

aritmetic operations will be performed inside of $[].

```bash
a=10
b=13
echo $[$a + $b]
```
However to organize the content we can perform 
arithmetic operations in (()).
for instance;
```bash
a =$((1+3))
```
then alternative you can uses:

```bash
cd /home/$whoami
```

```bash
head file 
head -n 1 file
tail +33
```
the flag -n allow us to get only n lines.
tail +33 print sice 33 line until the last line.

```bash
tr
```
tr is to replace and delete text.
change from to lower case to upper case
```bash
tr [:lower:] [:upper:]
tr [a-z] [A-Z]
```
redireccionamiento 
```bash
tr [a-z] < input.txt > output.txt
```
pass the commo to the return car.

```bash
cat file | tr ';' '\n'
```

drop blank character 
```bash
cat blank | tr -d ' '
```
number of lines in a document:
```bash
cat results.txt | wc -l
```

deleting lines with the sed editor;
```bash
sed '1d' file
```

to print two lines in screen
```
sed -n '2p' file
```
the subsitution command 
```bash
sed s/'line'/'LINE/'  bash.txt
``

# Regular expressions 
Used to match strings, are very powerful to find patterns 
in the search, here you must take in account that there are a special 
characters in regex;
# Metacharacters
()
[]
.
+
*
$
|
\
^
and to match the literal character of Metacharacters we need uses for instance \
for instance to match 1+1=1 we need "1\+1"

a brief discription of those and others:

$ match at the end
^ match at the beging
\d match a digit [0-9]
\D match a no digit
\w match a alphanumeric Character
\W no match a alphanumeric Character
\s match a white space Character [tab and newline are included)
[az] match any of a and z this only match a single character the order of character dont matter. 
[a,e,i,o,u] all vowels.
[a-z] with the hyphen - you can match a range of characters, match any between a and z
[^az] the caret in this case indicate not.
 [^\n] any one characters except new line.
[^#-character] means  by any character less by #.
this also it is important.
x{m,n}	At least m and at most 
x{m,} m or more

# positional group
() create a back reference
$1 $2 retrieve the back reference in sequential order.

it is important constrant the uses of () paranthesis in regular expressions.
() grouping and capturing.
backreferences

this is more easy of understand with examples:
12-123-456
19-124-190
12-144-987
03-001-876
if we make a pattern match we could uses:
\d{2}-\d{3}-\d{3}.
but note that this will be a entire search, however if we want select only
the first three digits we need enclosed in paranthesis.
\d{2}-(\d{3})-\d{3}.
group one.
and we can refer to the groups with dollar sing, for instance $1 refer to the first 
\d{3}. the we want replace then we can think in replacing $xxx-$1-xxx.

backreference 
uses the match pattern  to uses itself pattern regex for instance check the repeated words.

(\w+)\s\1 return for instance así así 

bounderaries \b 

\bdeterminant\b

determinante no match
determination no match
determinant match 

only math the last, due especify the boundaries.


