### gitignore
For files you don't want to track, you can create a file called ".gitignore" and put file patterns into this file. For example:
```bash
$ cat .gitignore
*.[oa]         # Ignore any files ending with ".o" or ".a"
*~             # Ignore any files end with a tilde "~"
```