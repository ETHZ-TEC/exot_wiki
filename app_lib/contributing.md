# Contributing to the library

The ideal way of working on the library is to follow the [git-flow](https://github.com/nvie/gitflow) workflow, or preferably its simpler alternatives. Gitlab, used for our repository hosting, facilitates such workflows thanks to its issue tracking feature. For further information please refer to:

- [Understsanding the GitHub flow](https://guides.github.com/introduction/flow/index.html),
- [Introduction to GitLab Flow](https://docs.gitlab.com/ee/workflow/gitlab_flow.html), and
- [The 11 Rules of GitLab Flow](https://about.gitlab.com/2016/07/27/the-11-rules-of-gitlab-flow/).

The basic principles are:

- **No commits on _master_**. The master branch is protected from direct writes by project members. Only stable version will be merged into master for publication.
- **Use the _master_ branch for stable versions**. Pull to the _master_ branch only tested and stable features from the development brach.
- **Keep main development on the _develop_ branch**. The _develop_ branch contains the current work-in-progress. At the same time, avoid introducing large changes to the _develop_ branch.
- **Use the issue tracker and milestones**. Create new issues for features, fixes, to-do's, and errors. Use the available labels, or add new if necessary.
- **Create separate feature branches**. Create a new branch from the _develop_ branch before starting working on implementing a new feature, or a larger change. GitLab issue tracker can be used to automatically create a branch and optionally create a pull request. If changes are introduced into the _develop_ branch after creating the feature, they can be merged or cherry-picked into the feature branch.
- **Create pull requests before introducing the feature**. A pull request to the _develop_ branch will help review and test the changes.
- **Tag working code using a proper versioning system**. The version number should be kept in sync with the project version in *CMakeLists.txt*. Creating tagged versions will help importing and using the library in other pieces of software.
- **Use issue and milestone numbers, commit hashes, and other advanced GitLab-flavoured Markdown features**. These facilitate keeping track of the changes and progress.

Also, please refer to the ["Code Style and Formatting"](../general/code-style#c-applications-and-the-application-library) page, which shows you how to automatically format the code with *clang-format* to conform to our coding style.