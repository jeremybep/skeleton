# Contributing & Code of conduct

### Contributing

Please note we have a code of conduct, please follow it in all your interactions with the project. When contributing to this repository, please first:

- Discuss the change you wish to make via a GitLab issue.
- Add appropriate label(s) to the new issue.
- Any merge request which hasn't been discussed in an issue before won't be taken into consideration.

### Release process

We use the [GitLab Flow](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/).  
The **main** branch is the **main** and default branch. Branchs are continuously checked out from **main** for developing features, bug fixes, refactors... and then merged + squashed into **main**.

Releases are tagged on **main**

### Development phases

Before a release, we will switch to a specific (fix, features, ect...) branches and then a **dev** phase. Merging new features is stopped and the devs focus on bug fixing. New features can still be developed, but will wait until after the release tag to get merged into **main** .

#### dev

**your\_package** is being tested by technical users (e.g. TDs, Devs...) to be sure nothing is broken and is still usable in any case...

#### main

**your\_package** is being tested by everyday users (e.g. Artists, Sups, Reviewers...) to be sure everything works and the new features are as perfect as they could be.

#### Roadmap

We are a small studio, with a small dev team, we don't use milsetone for the moment.

### Merge Request Process

1. Fork the repository.
2. Checkout a new branch from **main** with an explicit name regarding its content. **Keep one**
    
    **branch by feature, else you'll be asked to split**. It is best to start a branch from the issue board.
3. Code, **test**, make sure everything works and nothing is broken. You can make as much commits as you need, they'll be squashed in the end. Make sure you strictly follow the
    
    **coding style**.
4. Update the documentation if needed.
5. Write your tests if the features allows it (feel free to ask for assistance).
6. Rebase your branch on **main** before considering your job finished.
7. Create a merge request to **main** . **Your git history has to be clean**.
8. Apply the corrections from the reviews until it's considered finished. It may happen the
    
    **main** branch evolves during the review process and creates conflicts with your branch, you'll be asked to rebase your branch.
9. Be happy, your contribution has been merged! (thank you)
10. Wait until the next release is tagged to see everyone use your wonderful work.


### Testing

**your\_package** development is highly demanding about stability. That's why testing your contribution by hand and by running anti-regression tests is inescapable. Be aware you might be asked to write related automatic tests when proposing a feature, otherwise it might not be approved to be merged in core. "But it does take time!", sure, and saves much more from everyone: A bug is a lot of time consumption at a big scale, for users and for core team members, while spending a little more time to write some tests from one person, will make life easier for everyone.

*NB: If you're bugfixing, writing related tests to make sure the bug won't happen again is considerably welcome, but not mandatory.*

##### By hand

**your\_package** core focuses on remaining simple and having distinct processes as much as possible, randomly test your feature, try to run something totally different during it's process, play with it until you break it! If you despair to make it crash, your feature is ready to be submitted to the review process...

### Naming convention

##### Branch

Clear and concise naming with a short prefix to explicit the issue number and then the kind of change:

We follow [Semantic Versioning](https://semver.org) and also fully automated version management and package publishing with [semantic-release](https://github.com/semantic-release).

##### Commit Message Header

```
<type>: <short summary>
   │        │
   │        └─⫸ Summary in present tense. Not capitalized. No period at the end.
   │
   └─⫸ Commit Type: build|chore|ci|docs|feat|fix|perf|refactor|style|test
```

The **type** and **short summary** fields are mandatory.

##### Type

Must be one of the following:

- build : Changes that affect the build system or external dependencies
- chore : Other changes that don't modify src or test files
- ci : Changes to our CI configuration files and scripts
- docs : Documentation only changes
- feat : A new feature
- fix : A bug fix
- perf : A code change that improves performance
- refactor : A code change that neither fixes a bug nor adds a feature revert : Reverts a previous commit
- style : Changes that do not affect the meaning of the code
- test : Adding missing tests or correcting existing tests

**Breaking Changes Indicator**
Breaking changes should be indicated by an ``!`` before the ``:`` in the subject line e.g. ``feat!: remove status endpoint``

- Is an optional part of the format


see releaseRules in ``.github/workflows/release.yml``


##### Commit

The commit message must start with the **type**, colon, and the kind of changes which has been made, followed by a short description of the change. A longer description can be filled on the second line.

##### Exemples

> fix: Short description for the fixture
> feat: Short description for the feature
> feat!: remove ticket list endpoint
> perf: decrease memory footprint for determine uniqe visitors by using HyperLogLog
> style: remove empty line
> refactor: implement fibonacci number calculation as recursion
> build: update dependencies


### Coding style

#### Comment your code!

**your\_package** code is highly commented and contributing to **your\_package** implies to adopt this reflex. The global algorithm must be understandable by reading only the comments.

#### Explicit variable name

We prefer a long and explicit variable name than a short and obscur one.

- **timeline\_item\_path** is perfect, when **tip** or **tlitmpt** are unacceptable.
- A shortened name is still possible as long as it's perfectly obvious: **items\_dir**.


### Docstrings

##### One line docstring

```python
"""Do this action"""
```

- Rules are : 
    - Use """ and not '''
    - No space before the first letter
    - No space after the last letter
    - No point at the end of the line
    - Use imperative mode

##### Multi line docstring

```python
"""Do this action
To make the world a better place.
"""
```

- Rules are: 
    - Use """ and not '''
    - No space before the first letter
    - Last """ need to be alone on his line
    - No point at the end of the first line
    - Use imperative mode in the first line
    - Only one sentence on first line.
    - Add space between first line and next ones.

#### Parameters and return

Use sphinx [NumPy Style Python Docstrings](https://www.sphinx-doc.org/en/master/usage/extensions/example_numpy.html#example-numpy).

```python
def module_level_function(param1, param2=None, *args, **kwargs):
    """This is an example of a module level function.
    Function parameters should be documented in the ``Parameters`` section.
    The name of each parameter is required. The type and description of each
    parameter is optional, but should be included if not obvious.
    If ``*args`` or ``**kwargs`` are accepted,
    they should be listed as ``*args`` and ``**kwargs``.
    The format for a parameter is::
        name : type
            description
            The description may span multiple lines. Following lines
            should be indented to match the first line of the description.
            The ": type" is optional.
            Multiple paragraphs are supported in parameter
            descriptions.
        Parameters
        ----------
        param1 : int
            The first parameter.
        param2 : :obj:`str`, optional
            The second parameter.
        *args
            Variable length argument list.
        **kwargs
            Arbitrary keyword arguments.
        Returns
        -------
        bool
            True if successful, False otherwise.
            The return type is not optional. The ``Returns`` section may span
            multiple lines and paragraphs. Following lines should be indented to
            match the first line of the description.
            The ``Returns`` section supports any reStructuredText formatting,
            including literal blocks::
                {
                    'param1': param1,
                    'param2': param2
                }
        Raises
        ------
        AttributeError
            The ``Raises`` section is a list of all exceptions
            that are relevant to the interface.
        ValueError
            If `param2` is equal to `param1`.
"""
```

### import statements order

1. Standard Python (sys, os...)
2. Third parties (OTIO, PySide2, Blender)
3. your in-house modules

##### Order

They have to be alphabetically ordered.

```python
# Wrong
import sys
import os
import unittest

# Right
import os
import sys
import unittest
```

##### Linting

[Black](https://github.com/psf/black) is used with [Pylint](https://pylint.pycqa.org/en/latest/). Some preset :

you can find settings.json in .vscode you can find .pylintrc for pylint.

### Code of Conduct

#### Our Pledge

In the interest of fostering an open and welcoming environment, we as contributors and maintainers pledge to making participation in our project and our community a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, gender identity and expression, level of experience, nationality, personal appearance, race, religion, or sexual identity and orientation.

#### Our Standards

Examples of behavior that contributes to creating a positive environment include:

- Using welcoming and inclusive language
- Being respectful of differing viewpoints and experiences Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

Examples of unacceptable behavior by participants include:

- The use of sexualized language or imagery and unwelcome sexual attention or advances
- Trolling, insulting/derogatory comments, and personal or political attacks
- Public or private harassment
- Publishing others' private information, such as a physical or electronic address, without explicit permission
- Other conduct which could reasonably be considered inappropriate in a professional setting

#### Our Responsibilities

Project maintainers are responsible for clarifying the standards of acceptable behavior and are expected to take appropriate and fair corrective action in response to any instances of unacceptable behavior.

Project maintainers have the right and responsibility to remove, edit, or reject comments, commits, code, wiki edits, issues, and other contributions that are not aligned to this Code of Conduct, or to ban temporarily or permanently any contributor for other behaviors that they deem inappropriate, threatening, offensive, or harmful.

#### Scope

This Code of Conduct applies both within project spaces, communication utilities and in public spaces when an individual is representing the project or its community. Examples of representing a project or community include using an official project e-mail address, posting via an official social media account, or acting as an appointed representative at an online or offline event. Representation of a project may be further defined and clarified by project maintainers.

#### Enforcement

Instances of abusive, harassing, or otherwise unacceptable behavior may be reported by contacting the project team. All complaints will be reviewed and investigated and will result in a response that is deemed necessary and appropriate to the circumstances. The project team is obligated to maintain confidentiality with regard to the reporter of an incident. Further details of specific enforcement policies may be posted separately.

Project maintainers who do not follow or enforce the Code of Conduct in good faith may face temporary or permanent repercussions as determined by other members of the project's leadership.

#### Attribution

This Code of Conduct is adapted from the [Contributor Covenant](https://www.contributor-covenant.org), version 1.4, available at [http://contributor-covenant.org/version/1/4](http://contributor-covenant.org/version/1/4)
