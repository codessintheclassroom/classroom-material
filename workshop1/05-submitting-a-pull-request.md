[⏮ Previous step: Testing your code](./04-testing-your-code.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;⏭ ~~Next step~~

----

## Step 5: Submit a pull request and get your code reviewed

You've written some code and committed it. Now, we're now going to push that
code up to GitHub and open a "pull request", which is an opportunity for a
colleague to review your changes before merging them to the `master` branch.

### Context

In many teams, code review -- that is, having a second (and perhaps third)
person review changes before they are merged -- is an important part of the
software development process. At its best, code review can:

- improve the design of the code,
- help to maintain an appropriate level of code quality,
- help submitters _and reviewers_ learn about the codebase they work on,
- and, sometimes, find bugs.

Peer code review is most effective when it focuses on high-level questions of
design and problem-solving approach, without getting bogged down in details
such as style and formatting, which are often better reviewed by automated
tools such as linters or formatters.

We'll first look at the basics: how to open a GitHub pull request (which is
just one code review tool of many) and how to use one to review code. Then
we'll discuss and think about what constitutes a good code review experience
for everyone.

### Create a pull request

Currently, all the code you've written and all the commits you've made are on
your local machine. The first step to opening a pull request is to push your
changes to a branch.

_**N.B.** What follows is an abbreviated guide to pushing a branch and
opening a pull request. GitHub provides more detailed documentation on both
[pushing to a
branch](https://help.github.com/en/articles/pushing-to-a-remote) and
[creating a pull
request](https://help.github.com/en/articles/creating-a-pull-request) if you
need it._

1. Check that you're on a branch other than `master` by running `git branch`.
   If you made your changes on a branch (as suggested in step 1) the output
   should say something like `*shelter-frontend`.

2. Push your branch up to GitHub with `git push -u origin shelter-frontend`
   (you'll need to change the name of the branch to match yours!).

   _For further guidance on pushing your branch, consult [our Git
   cheatsheet](https://github.com/codessintheclassroom/classroom-material/blob/master/git-cheatsheet.md#push)._

3. Open up your repository on GitHub (it'll be at
   `https://github.com/codessintheclassroom/<repository-name>`).

4. Click the "New pull request" button. It's on the left under the status bar
   showing number of commits, branches, etc.

5. Leave the base branch as `master`, and select the branch you just pushed
   as the "compare" or "head" branch.

6. Add a title and description for your pull request.

   _In general, it's good to use the description field to explain the **why**
   of your changes. A reviewer can easily see **what** you've changed by
   looking at the code. Use the description field to explain the motivation
   for your changes (e.g. what problem are you trying to fix?), alternative
   approaches you considered, and perhaps details of any special
   considerations for rolling out your changes to production._

7. Click the big green button: "Create pull request"!

Hooray, you've opened a pull request! 🍰

Now it's time for your reviewer to take a look, ask any questions they have,
and perhaps propose some improvements. If they have suggestions, you can fix
the problems locally and push again. The pull request will be automatically
updated with any changes in the remote branch. You can also answer to the
pull request comments and once the issue is fixed or you have explained your
reasoning, you can mark the conversation as finished.

Once the pull request is reviewed and approved, you can again click the big
green button to merge your pull request!

### Review a pull request

_**N.B.** What follows is an abbreviated guide to reviewing a pull request.
GitHub provides more detailed
documentation](https://help.github.com/en/articles/reviewing-proposed-changes-in-a-pull-request)
if you need it._

1. Open up the relevant repository on GitHub (it'll be at
   `https://github.com/codessintheclassroom/<repository-name>`), go to the
   "Pull requests" tab, and select the pull request you want to review from
   the list.

2. Read the title and description. You can see the code changes themselves in
   the "Files changed" tab.

3. If you hover your mouse pointer over a line, a blue **+** button appears.
   Click the button to add a comment for the line. Once you have written a
   comment, click "Start a review". For further comments, you can click "Add
   review comment".

4. Once you are happy with your comments you can send them to the submitter
   by clicking "Review changes". You can also add a general comment for the
   review at this point.

   When you are submitting the review you can decide whether:

   - you are requesting changes based on your comments
   - your comments are general feedback without explicitly approving the
     changes or requesting additional changes
   - you approve merging the changes proposed in the pull request

5. Click "Submit review" to finish reviewing. The submitter won't see any of
   your comments until this step.

Now it's time for the submitter to look at your review and any comments. If
necessary, they may make changes and perhaps even ask you for a second round
of review.

### What is a "good" code review

In order for everyone to get the most out of a code review, it's very
important for everyone to practise empathy for the other people involved. In this section we'll cover some general guidelines to making code review a good experience for everyone.

We encourage you to discuss these issues with the people around you. Have you had particularly good or bad code review experiences? Share them and, in particular, try and identify what made the good experiences stand out for you.

#### Practise empathy for your peer

The most important quality for good peer code review is empathy. Try and keep the following points in mind:

- On the receiving end of your comments is another person who is trying
  their best to do a good job in a business context which likely includes
  time pressures, conflicting goals, and distractions.

- Code reviews are not an opportunity to prove who is a better programmer. Code
  review is an opportunity for people to working together to make the code
  better.

- As a reviewer, you can help the submitter improve their code, but you can and
  often will learn from other people's code too! Code review is an important
  way in which you can keep your knowledge about the codebase up to date.

- As a submitter you have the opportunity to truly polish your code and catch
  any mistakes without real harm done, because it takes place before merging
  to master. If a mistake is found or improvement is pointed out, everyone
  wins, because it means the codebase is going to be better after the review.

Note that is is not necessary for the reviewer to always be the more
experienced developer. For any team that includes junior developers, it is
important that they are able to understand the code too, and code review
provides an opportunity for them to provide feedback on code
comprehensibility. Usually everybody is expected to participate in the review
regardless of seniority.

_**Further reading:** for an even more detailed look at how to make your code
reviews the best they can be, see [this article by Sean
Hammond](https://seanh.cc/post/code-review/)._

#### Considerations for reviewers

First of all, it is important to **understand the change** you’re reviewing.
If you don’t understand the change, you can’t positively review the change.
If you are unsure what the pull request is about after reading the
description/commit messages, you need to ask the author for a better
description.

When you understand the change, there are a few key levels of code review.
It's usually best to progress through this list in order. Don't worry about
details of syntax and style before you've addressed major architectural
issues:

1. **Architecture and design**

   Here are a few things to think about. Not every review needs to consider all of these!

   - Is the code required? Are there any improvements to be made through
     abstractions or reuse of existing code? Does the code tie in with the rest of
     the codebase?
   - Is the code appropriately [reusable](https://en.wikipedia.org/wiki/Reusability)?
   - Is naming within the code appropriate? For example: usually code should
     be named based on what it does, not based on how it may be used, data
     models should describe the data and not contain UI concepts, etc.
   - Does the code make appropriate use of
     [encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming))?
   - Do the components have [single responsibilities](https://en.wikipedia.org/wiki/Single_responsibility_principle)?
   - Has the submitter considered appropriate [separation of
     concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)

   _To learn more about the principles of clean code and architecture, Clean
   Code and Clean Architecture books by Robert C. Martin are a good read._

2. **Functionality**

   - Does the code do what it’s supposed to do?

3. **Style**

   - Is the code idiomatic for the language?
   - Are common error-prone patterns for that language avoided?
   - Is the code easy to understand?

4. **Syntax**

   - Is the code well formatted, meeting indentation and whitespace standards
     and free from parse errors?

Comment on specific lines of code if you can to say where the code could be
improved. General feedback on the change as a whole can typically be provided
as a comment without referencing a specific line.

Remember to **assume best intentions** and address the code, not the
submitter. Be as objective as possible. You should always justify your
comments, so that the submitter can learn. If you are unable to justify the
comment, consider that it might not be as objective a criticism as you
thought.

There are always subjective preferences in any code base. Respect those
preferences, unless you have team guidance on a given topic or the preference
is inconsistent with existing codebase. You can however point out if the
submitter's subjective choices aren't self-consistent.

**Don't forget it is good to say that everything is ok. You are not obligated
to point out at least one improvement.**

#### Submitters

As a submitter, you can also help to ensure productive code reviews, by:

- **Adhering to any standards of your code base**. Most teams agree on
  standards such as code formatting and style. Make sure your changes adhere
  to these standards. This will avoid wasting time in the review identifying
  formatting problems.
- **Assume best intentions from the reviewer**. Code review is not a battle,
  so try not to take criticism of your code personally. However, if criticism
  is personal, then you should say so. Try and reduce conflict resulting from
  misunderstandings – see if you can clear up such misunderstandings, either
  in the review, in the commit messages or through talking it through with
  the reviewer.

### You made it!

If you made it this far, you're awesome! 😀 You deserve to celebrate and relax.

Don't forget: if you have any thoughts or suggestions about how any of the
workshop materials could be improved, please don't hesitate to talk to one of
the mentors or even [submit a GitHub
issue](https://github.com/codessintheclassroom/classroom-material/issues).

----

[⏮ Previous step: Testing your code](./04-testing-your-code.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;⏭ ~~Next step~~