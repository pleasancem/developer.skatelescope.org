Working with git
----------------

About git
=========

Git is the version control system of choice used by SKA. Describing the basics
of how to use git is out of the scope of this developer portal, but it is
fundamental that all developers contributing to SKA get familiar with git and
how to use it. These online resources are a good starting point:

  * Learn git interactively: https://learngitbranching.js.org/
  * Official git reference at: https://git-scm.com/docs
  * Interactive Git cheatsheet: http://www.ndpsoftware.com/git-cheatsheet.html


Committing code
===============

When working on a development project, it is important to stick to these simple
commit rules:

* Commit often.
* Have the **Jira story ID** at the beginning of your commit messages.
* Git logs shall be human readable in sequence, describing the development activity.
* Use imperative forms in the commit message.

Configure git
=============

Set GIT institutional email address
+++++++++++++++++++++++++++++++++++

Setup git so that it uses your institutional email account to sign commits,
this can be done in your global git configuration:

.. code:: bash

  $ git config --global user.email "your@institutional.email"
  $ git config --global user.email
  your@institutional.email

Or you can configure the mail address on a project basis.

.. code:: bash

  $ cd your/git/project
  $ git config user.email "your@institutional.email"
  $ git config user.email
  your@institutional.email


Branching policy
================

Albeit the SKA organisation does not want to be prescriptive about git
workflows, two concepts are important to the SKA way of using GIT:

  1. The master branch of a repository shall always be stable.
  2. Branches shall be short lived, merging into master as often as possible.

Stable means that the master branch shall always compile and build correctly,
and executing automated tests with success. Every time a master branch results
in a condition of instability, reverting to a condition of stability shall have
the precedence over any other activity on the repository.

Master based development
++++++++++++++++++++++++

We suggest teams to start developing adopting a master-based development
approach, where each developer commits code into the master branch at least
daily. While this practice may seem counter intuitive, there is good evidence
in literature that it leads to a better performing system. Branches are
reduced to a minimum in this model, and the discipline of daily commits into
master greatly enhances the communication within the team and the modularity
of the software system under construction. The workflow follows these steps:

  * As a developer starts working on a story, all his commits related to the story shall contain the story Jira ID in the message. i.e. *AT-51 method stubs*
  * The developer continues working on his local master branch with multiple commits on the same story.
  * Each day the local master pulls the remote and incorporates changes from others.
  * The local master is tested successfully.
  * The local commits are pushed onto the remote master.
  * The CI pipeline is correctly executed on the remote master by the CI server.

Implemented correctly, this practice leads to having an integrated, tested,
working system at the end of each  development interval, that can be shipped
directly from our master branch with the click of a button.

Story based branching
+++++++++++++++++++++

We support adopting a story-based branching model, often referred to as
**feature branching**. This workflow effectively leverages **pull requests** enabling code reviews and continuous branch testing, but it
is important to stress the importance of having short lived branches. It is
easy to abuse this policy and have long living branches resulting in painful
merge activities and dead or stale development lines.
Bearing in mind that a *story* by definition is some
piece of work a developer should conclude in the time of a sprint, the workflow
would follow these steps:

* As a developer starts working from master on a new story, she creates a new branch.
* The new branch shall be named as the story, i.e. *story-AT1-26*.

.. code:: bash

  $ git branch
  * master
  $ git checkout -b my-story-id
  $ git branch
  master
  * my-story-id

* All the commit messages contributing to the development of the story begin with the story ID, i.e. *AT1-26 basic testing*.
* The developer makes sure that all tests execute correctly on her local story branch.
* When the story is ready for acceptance the developer pushes the story branch upstream.

.. code:: bash

  $ git push -u origin my-story-id

* A pull request is created on the DVCS server to merge the story branch into the master branch.
* Reviewers interact with comments on the pull request until all conflicts are resolved and reviewers accept the pull request.
* Pull request is merged into Master.
* The CI pipeline is executed successfully on the master branch by the CI server.

Whenever a team deviates from one of the recommended policy, it is important
that the team captures its decision and publicly describe its policy,
discussing it with the rest of the community.

See a more detailed description of this workflow at https://guides.github.com/introduction/flow/


Workin with Github
------------------

Use institutional email
=======================

Create a github account using your **institutional email** address at
https://github.com/join?source=login . If you already have an account on
github, you shall have your institutional email added to your profile: click on
your user icon on the top right corner and select *Settings->Emails->Add email
address* .

Setup SSH key
=============

Associate your ssh-key to your user at *Settings->SSH and GPG keys* .

Join SKA Organisation
=====================

SKA Organisation can be found on github at https://github.com/ska-telescope/ , The scrum master of your team will make sure you can access it.

Desktop client
==============

Less experienced developers can use the github desktop client at:
https://desktop.github.com/
This definitely lowers the barrier of using git for a number of different users.
