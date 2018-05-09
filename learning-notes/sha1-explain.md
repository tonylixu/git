### How git calculate sha1?
First, look at this commit:
```bash
$ git show
commit d6cd1e2bd19e03a81132a23b2025920577f84e37
Author: jnthn <jnthn@jnthn.net>
Date:   Sun Apr 15 16:35:03 2012 +0200

    When I added FIRST/NEXT/LAST, it was idiomatic but not quite so fast. This makes it faster. Another little bit of masak++'s program.
```

So that's the sha1 we want to reproduce. `d6cd1e2bd19e03a81132a23b2025920577f84e37`

### We might thought
```bash
$ git cat-file commit HEAD
tree 9bedf67800b2923982bdf60c89c57ce6fd2d9a1c
parent de1eaf515ebea46dedea7b3ae0e5ebe3e1818971
author jnthn <jnthn@jnthn.net> 1334500503 +0200
committer jnthn <jnthn@jnthn.net> 1334500545 +0200

When I added FIRST/NEXT/LAST, it was idiomatic but not quite so fast. This makes it faster. Another little bit of masak++'s program.
```
These are:
* The source tree of the commit (which unravels to all the subtrees and blobs)
* The parent commit sha1
* The author info
* The committer info (right, those are different!)
* The commit message
But it turns out there is also a NUL-terminated header that gets appended to this, containing the word "commit", and the length in bytes of all of the above information:
```bash
$ printf "commit %s\0" $(git cat-file commit HEAD | wc -c)
commit 327
```
(No, you can't see the NUL byte.)

### Put this header and the rest of the information together:
```bash
$ (printf "commit %s\0" $(git cat-file commit HEAD | wc -c); git cat-file commit HEAD)
commit 327tree 9bedf67800b2923982bdf60c89c57ce6fd2d9a1c
parent de1eaf515ebea46dedea7b3ae0e5ebe3e1818971
author jnthn <jnthn@jnthn.net> 1334500503 +0200
committer jnthn <jnthn@jnthn.net> 1334500545 +0200

When I added FIRST/NEXT/LAST, it was idiomatic but not quite so fast. This makes it faster. Another little bit of masak++'s program.
```

### what you get hashes to the right sha1!
```bash
$ (printf "commit %s\0" $(git cat-file commit HEAD | wc -c); git cat-file commit HEAD) | sha1sum
d6cd1e2bd19e03a81132a23b2025920577f84e37  -
```