### What is a PR?
Quote from Github:
```bash
Pull request lets you tell others about changes you've pushed to a Github repo. Once a pull request is sent, interested parties can review the set of changes, discuss modifications and even push follow-up commits if necessary.
```
Pull request are commonly used by teams and organizations collaborating using the Shared Repository Model, where everyone shares a single repo and topic branches are used to develop features and isolate changes. Many open source projects on Github use pull requests to manage changes from contributors as they are useful in providing a way to nofity project maintainers about changes one has made and in initiating code review and general discussion about a set of changes before being merged into the main branch.

### A bit more
PR is a mechanism for a developer to notify team members that they have completed some work. Once a PR is created, they can start review the code and merge it into `master` branch.

But, the pull request is more than just a notification—it’s a dedicated forum for discussing the proposed feature. If there are any problems with the changes, teammates can post feedback in the pull request and even tweak the feature by pushing follow-up commits. All of this activity is tracked directly inside of the pull request.

Compared to other collaboration models, this formal solution for sharing commits makes for a much more streamlined workflow.

### Anatomy of a Pull Request
When you file a pull request, all you’re doing is requesting that another developer (e.g., the project maintainer) pulls a branch from your repository into their repository. This means that you need to provide 4 pieces of information to file a pull request:
* Source repository
* Source branch
* Destination repository
* Destination branch
