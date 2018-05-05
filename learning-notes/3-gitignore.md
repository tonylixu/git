### gitignore
For files you don't want to track, you can create a file called ".gitignore" and put file patterns into this file. For example:
```bash
$ cat .gitignore
# Ignore any files ending with ".o" or ".a"
*.[oa]
# Ignore any files end with a tilde "~"
*~
```
`.gitignore` rules:
* Blank lines or lines starting with `#` are ignored.
* Standard glob patterns work, and will be applied recursively throughout the entire working tree.
* You can start patterns with a forward slash (/) to avoid recursivity.
* You can end patterns with a forward slash (/) to specify a directory.
* You can negate a pattern by starting it with an exclamation point (!).

Example:
```bash
# Ignore all .a files
*.a

# Do track lib.a
!lib.a

# Ignore all files in build directory
build/

# Ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# Ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```