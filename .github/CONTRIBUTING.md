## Contributor guidelines

First of all, thank you for contributing to GECKO!! Anybody is welcome to contribute, but please abide by the following guidelines.

You can contribute in 2 main ways: by creating issues, and by sending pull requests (PRs) with corrections or additions to the source code.

### Reporting issues

Report an issue at https://github.com/SysBioChalmers/GECKO/issues if you note any of the following:

* Missing feature you would like GECKO to have.
* Bug/weird simulation results.
* Lacking documentation.
* Any type of feedback.

If you are unsure about the issue, consider asking first in our [Gitter chat room](https://gitter.im/SysBioChalmers/GECKO).

When creating the issue, please make sure:

* You tested your code (if any) with all of GECKO's [requirements](https://github.com/SysBioChalmers/GECKO).
* You did your analysis in the `master` branch of the repository.
* You provide any necessary files/links needed for understanding the issue.
* You checked that a similar issue does not exist already

Feel free to also comment on any of the [open issues](https://github.com/SysBioChalmers/GECKO/issues). When doing so, please comply with our [code of conduct](https://github.com/SysBioChalmers/GECKO/blob/devel/.github/CODE_OF_CONDUCT.md).

Finally, if you like GECKO please remember to 'star' our Github page (click on the star at top right corner), that way we also have an idea of who is using GECKO!

### Contributing to GECKO

Want to contribute to GECKO with some additions or improvements? Consider starting by raising an issue and assign it to yourself to describe what you want to achieve. This way, we reduce the risk of duplicated efforts and you may also get suggestions on how to best proceed, e.g. there may be half-finished work in some branch that you could start with. Also, feel free to browse our [open issues](https://github.com/SysBioChalmers/GECKO/issues): Anything tagged with "help wanted" is open to whoever wants to implement it!

Here's how to set up GECKO for local development to contribute smaller features or changes that you can implement yourself:

1. First of all, make sure that you have all [requirements](https://github.com/SysBioChalmers/GECKO) for running GECKO.

2. Fork the GECKO repository on GitHub (go to https://github.com/SysBioChalmers/GECKO & click on the upper right corner).

3. Clone your fork locally:
    ```
    git clone https://github.com/<your Github name>/GECKO.git
    ```

4. Check out the branch that you want to contribute to. Most likely that will be ``devel``:
    ```
    git checkout devel
    ```

5. Create a branch for local development based on the previously checked out branch ([see below](#branching-model) for details on the branching model and how to name your branch):
    ```
    git checkout -b name-of-your-branch
    ```

6. Now you can make your changes locally!
  * New scripts (if any) should start with a commented section describing the script and explaining the inputs/outputs. If you are uncertain on the style to follow, check out pre-existing functions.
  * Try to document as much as possible; this will help the review process.

7. Commit your changes and push your branch to GitHub.
    ```
    git add .
    git commit -m "Title of your commit"
    git push origin name-of-your-branch
    ```
    [See below](#semantic-commits) for recommendations on how to name your commits. In case of larger updates, you can of course make several commits on a single contribution. However, if you need to do too many commits, consider if your contribution could be instead split into separate PRs (making it easier for reviewing later).

8. Submit a PR through the GitHub website (https://help.github.com/articles/creating-a-pull-request-from-a-fork/) to the `devel` branch of the original SysBioChalmers repo (not your fork). We recommend ticking the box "Allow edits from maintainers" if you wish for us to be able to contribute directly to your branch (speeding-up the reviewing process).

Note that steps 3, 4, 5 and 7 can be done, if you prefer, with any git client, such as [Github Desktop](https://desktop.github.com/).

Finally, and for larger features that you want to work on collaboratively, you may consider to first request to join our development team to get write access to the repository so that you can create a branch directly in the main repository (or simply ask the administrator to create a branch for you). Once you have a new branch, you can push your changes directly to the main repository and when finished, submit a pull request from that branch to ``devel``. [See below](#development-team-guidelines) for more details.

Thank you very much for contributing to GECKO!

#### Branching model

* `devel`: Is the branch all pull-requests should be based on.

* `master`: Is only touched by the administrator and is the branch with the tested & reviewed codebase. Each merge commit to it is associated to a release.

* `{chore, doc, feat, fix, refactor, style}/descriptive-name`: Any other branch created in the model. If you work on a fix, start the branch name with `fix/`, if you work on a feature, start the branch name with `feat/`. Examples: `fix/bug` or `feat/new-algorithm`. [See below](#semantic-commits) for more details on the possible actions you can use.

#### Semantic commits

Please use concise descriptive commit messages. Ideally, use [semantic commit messages](http://karma-runner.github.io/2.0/dev/git-commit-msg.html) to make it easier to show what you are aiming to do:

`action: brief description`

`action` refers to what exactly are you doing in the commit:
* `chore`: updating toolbox, data files, etc.
* `doc`: updating documentation or explanatory comments in functions.
* `feat`: new feature added.
* `fix`: something that was incorrect and now has been corrected.
* `refactor`: see [code refactoring](https://en.wikipedia.org/wiki/Code_refactoring).
* `style`: minor format changes to functions or data.

More examples [here](https://github.com/SysBioChalmers/GECKO/commits/master). A more detailed explanation or comments is encouraged to be left in the commit description.

## Development team guidelines

This section is meant for the development team of GECKO. As a member of the development team, you should comply with all [previous contributor guidelines](#contributor-guidelines) as well. Besides that, please also consider the following guidelines.

### Creating pull requests

Changes to the source code _may not_ be directly committed to the `master` or `devel` branches (in fact they are protected). Commits are made to side-branches, after which pull requests are made for merging with `devel`. For this, follow the [instructions](#contributing-to-the-model) for contributors, but consider that as members of the development team have write access to the repository, you can create a branch directly in the main repository without needing to fork, for your convenience. This means that you can:

* Skip step 2 of the contribution process.
* In step 3 of the contribution process, clone directly the original repo:
  ```
  git clone https://github.com/SysBioChalmers/GECKO.git
  ```

Follow all other steps in the same way. Also, when creating your pull request (or after you have created it):

* Choose 1 or more members of the team (ideally with knowledge on the pull request) as reviewers. Note that the person making the pull request and the reviewer _cannot_ be the same person.
* Assign appropriate [labels](https://github.com/SysBioChalmers/GECKO/issues/labels).

### Reviewing pull requests

Every pull request must be approved by at least one reviewer before it can be merged. When reviewing someone else's pull request, keep in mind the following aspects:

* **Compatibility:** Make sure the changes introduced in the PR do not generate errors when calling either `updateDatabases.m`, `enhanceGEM.m` or `generate_protModels.m`. To test the latter two functions, you may use [yeast 8.1.3](https://zenodo.org/record/1495482), as this will also help you validate any changes to the pipeline.
* **Documentation:** The reasoning for each modification should be provided, as documentation or as a comment in the pull request.
* **Reproducibility:** If there are any added scripts, make sure that if you run them, they achieve the desired purpose.
* **Style:** Ensure that changes to the codebase have a compliant style, and new datasets (if any) are straight-forward to understand.
* When commenting in the review, please comply with our [code of conduct](https://github.com/SysBioChalmers/GECKO/blob/devel/.github/CODE_OF_CONDUCT.md).
* Avoid vague comments and try to be as explicit as possible (e.g.: _"Please include X here"_ instead of _"X could be included here"_).
* As much as possible, try to keep the review process in the pull request discussion, and not in separate private emails.

## Administrator guidelines

This section is meant for the administrator of this repo. The main duties of the administrator are:

* To keep the repository clean and organized, i.e. avoid redundancy in functions and/or data, and keep coherency in naming of files.
* To help in the reviewing process of external pull requests by assigning reviewers and [labels](https://github.com/SysBioChalmers/GECKO/issues/labels), if applicable.
* To keep [issues](https://github.com/SysBioChalmers/GECKO/issues) with the proper labels, and to close issues once they are fixed in the `master` branch.
* In cases of disagreement between contributors, to decide how to resolve the issue.
* To merge open pull requests into `devel` regularly (see [below](#merging-contributions)).
* To generate new releases of the model regularly (see [below](#releasing-a-new-version)).

### Merging contributions

The following points should be considered when merging branches to `devel`:

* Make sure the branch gets accepted by at least one developer with writing access.
* Wait at least a day before merging, to allow other developers to inspect the pull request.
* As soon as the branch is merged, confirm that `devel` is still possible to merge to `master` (this can be checked [here](https://github.com/SysBioChalmers/GECKO/compare/devel)). If conflicts appear, fix the conflict _locally_ as soon as possible in `devel` and then push it (note, **DO NOT** pull any other changes from `master` to `devel`, just the single file that is creating the conflict).

### Releasing a new version

* A merge of `devel` with `master` invokes a new release.
* A new release should be made as soon as there is substantial new work in `devel` (as rule of thumb, after 3-4 pull request merges or ~20 commits).

GECKO follows [semantic versioning](https://semver.org/):

* A `major` release is when substantial new features are added and backwards compatibility is broken.
* A `minor` release is when substantial new features are added and backwards compatibility is not broken.
* A `patch` release is the most common one and is done when only few things have changed, such as:
  - Small new features.
  - Bug fixes.
  - Updating toolboxes.
  - Re-organization of data
  - Refactoring of code.

When releasing, please follow these steps:

1. Create a pull request from `devel` to `master`, indicating all new features/fixes/etc. and referencing every previous pull request included (examples [here](https://github.com/SysBioChalmers/GECKO/releases)). Tip: if any [issue](https://github.com/SysBioChalmers/GECKO/issues) gets solved in the release, write in the pull request description "Closes #X", where "X" is the issue number. That way the issue will be automatically closed after merge.
2. Wait at least a day + 1 approval + passing CI.
3. Bump to the new version x.y.z. For this, create in `devel` a single commit `chore: version X.Y.Z` with:
    * Updated `/geckopy/HISTORY.rst` by putting at the top the same description as in the PR from step 1 (use https://pandoc.org/try for transforming markdown to ReSTructured text).
    * Updated version in:
      - `/docs/conf.py` (lines 57 & 59).
      - `/geckopy/setup.cfg` (line 2).
      - `/geckopy/setup.py` (line 22).
      - `/geckopy/geckopy/__init__.py` (line 10).

    * Updated `/README.rst` date (line 14).
4. Push the commit and confirm that the CI tool is still passing.
5. Merge PR -> confirm that the CI tool is still passing.
6. In `master`, create LOCALLY a tag `vX.Y.Z` on the latest merge commit + push said tag (in git kraken or with `git push origin vX.Y.Z`) -> confirm that the CI tool is still passing and geckopy deploys to PyPI (check [here](https://pypi.org/project/geckopy/)).
7. Make the new release at GitHub (https://github.com/SysBioChalmers/GECKO/releases/new), using the proper tag and with the same description as the corresponding PR from step 1.

## Acknowledgments

These contribution guidelines were written based on the contribution guidelines of [SysBioChalmers/yeast-GEM](https://github.com/SysBioChalmers/yeast-GEM/blob/devel/.github/CONTRIBUTING.md).
