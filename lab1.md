# Lab Report 1

## `cd`

### `cd`

1.

```
repos johnpork$ cd
~ johnpork$
```

2. absolute path: `/Users/johnpork/repos`

3. I got this output because the default argument is probably the home directory

4. not an error

### `cd webapps`

1.

```
repos johnpork$ cd webapps/
webapps johnpork$
```

2. absolute path: `/Users/johnpork/repos`

3. I got this output I gave an argument that was a directory in the place where I am in. Then it changed my current directory to the one I gave it.

4. not an error

### `cd test.txt`

1.

```
repos johnpork$ cd test.txt
bash: cd: test.txt: Not a directory
repos johnpork$
```

2. absolute path: `/Users/johnpork/repos`

3. I go this output because I gave an invalid argument. A file is not a directory so it threw an error.

4. yes error. You can not change your directory to a file, so bash would not like me passing a file as the argument for cd.

## `ls`

### `ls`

1.

```
mern-blog johnpork$ ls
api     client
mern-blog johnpork$
```

2. absolute path: `/Users/johnpork/repos/webapps/mern-blog`

3. I think this was the output because the default argument for ls is the current directory. So then it will list the stuff in the current directory.

4. not error

### `ls client`

1.

```
mern-blog johnpork$ ls client
README.md       node_modules    package.json    public          src             yarn.lock
mern-blog johnpork$
```

2. absolute path: `/Users/johnpork/repos/webapps/mern-blog`

3. I got this output because I provided a directory as an argument. Then it will list the files in that directory

4. not error

### `ls client/README.md`

1.

```
mern-blog johnpork$ ls client/README.md
client/README.md
mern-blog johnpork$
```

2. absolute path: `/Users/johnpork/repos/webapps/mern-blog`

3. I think this was the output because the argument I provided told ls to list the exact name of the file. There is a probably options like wildcards and sorting so it can list multiple files.

4. not error

## `cat`

### `cat`

1.

```
mern-blog johnpork$ cat
asod
asod
```

2. absolute path: `/Users/johnpork/repos/webapps/mern-blog`

3. It repeats what I input until I do control D. You can probably direct the output into a file or pipe it with other text inputs.

4. not error

### `cat client`

1.

```
mern-blog johnpork$ cat client
cat: client: Is a directory
mern-blog johnpork$
```

2. absolute path: `/Users/johnpork/repos/webapps/mern-blog`

3. It will throw an error when given a directory because this is not the funciton of the command.

4. yes error. The command works with inputting and outputting text, so it will not work with directories.

### `cat client/test.txt`

1.

```
mern-blog johnpork$ cat client/test.txt
amon
mern-blog johnpork$
```

2. absolute path: `/Users/johnpork/repos/webapps/mern-blog`

3. It prints out the string representation of the file. Since the file contains text, the contents printed is the stuff inside.

4. not error
