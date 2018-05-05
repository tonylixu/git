### File states
Each file in your working directory can be in one of two states: tracked or untracked.
* Tracked: Files that were in the last snapshot; they can be unmodified, modified, or staged
* Untracked: Everything else — any files in your working directory that were not in your last snapshot and are not in your staging area

### Stage a file
Given the exmaple below:
```bash
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```
The `CONTRIBUTING.md` file is under `Changes not staged for commit`. This means that a file that is tracked has been modified but not yet staged. To stage is:
```bash
$ git add CONTRIBUTING.md
```
