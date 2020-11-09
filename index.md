## Bash programming 

```bash
chmod +x file.sh
./file.sh
```

```bash
bash file.sh
```

The first way need give permission to execute the file, 
and you should include a shebang #!/bin/bash.

to see what shell you have in your machie run

```bash
echo $SHELL
```
if you have bash you can see the currently installed version.

```bash
bash --version
```
### Variables


## Relative and absoulte path

  folderRoot
    /   \
   /     \
folderA  folderB

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
for x to indicate the interator.
in to give a explicity list of arguments.
do is used to loop over positional objetcts.




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

## Loops in Bash.
backup=

#Variables
store data of a command
```bash
files=$(ls)
```
take in mind that $() specify that we want run a command and store 
the results in the variable.


NOTE= you must avoid UPPERCASES to define variables, due this way 
is used for internal shell variables.

aritmetic operations will be performed inside of $[].

```bash
a=10
b=13
echo $[$a + $b]
```
note to refer to variables we need put the dollar sing.

then alternative you can uses:
```bash
cd /home/$whoami
```
to establish the working directory in the folder.




now we are create the branch gh-pages.
git remote add url.

how to drop remote branchs:
git branch -a
git push origin --delete main 

we only need create a branch with the folder.


we need create a index.html


http://jmcglone.com/guides/github-pages/



research about Jekyll, 

for what is used git stash?

see track that will be the solution to the problem.


### git page.

creating a a repo with the _username.github.io_ 
and adding a index.md this will be rendered as a html file to show the web page.

integration with anoter repos.

 we can uses a branch gh-pages to add to mainly page.



# how we can share a jupyter-notebook.
see binder plataform.


## create from source html.
index.html to load the web page.



# Share a jupyter notebook using github and binder.

we need create a requirement.txt in the repo.
requirements have the packages and the version 
pandas==2.4
matplotlib==1.6


we need create runtime.txt 
python3

what is jupyterhub?
KubeSpawner
pod



# binder creates a specific enviorment.





## What about licences 
this point is very important due, there are projects that have in mind.


## binder run in kubernetes.
reproducible containers from repositories.

## Known the version of packages in Python


```python 
import pandas
print(pandas.__version__)
```

how see packages and version in R?

$ jupyter nbconvert --to html NOTEBOOK-NAME.ipynb


pip install notedown



## We need create a work flow to publish all this material.

