# Creating Pull Requests
1. push your changes to remote branch. If your local branch is tracking remote branch, `git push` will do. If you have just local branch, create a remote branch and push you changes with `git push origin HEAD:<remote branch>`.
2. go to Pull requests tab on repository github page and click on **New pull request** button.
3. select the source and target branches (usually `master <- <remote branch>`)
4. fill in a pull request title and description and click create pull request
5. wait for your reviewer. If there are any issues or improvements, fix the problems locally and push again. The pull request will be automatically updated with any changes in the remote branch. You can also answer to the pull request comments and once the issue is fixed or you have explained your reasoning, you can mark the conversation as finished.
6. once the pull request is reviewed and approved, merge the pull request

#Reviewing Pull Requests
1. go to Pull requests tab, select the pull request you want to review from list
2. go to Files changed tab to see the changes
3. if you hover over line, a blue **+** button appears. Click the button to add a comment for the line. Once you have written down a comment, click Start a review (if you have already done so, you can click Add review comment). 
4. once you are happy with your comments you can send them to the submitter by clicking Review changes and then Submit Review. You can also add a general comment for the review there. When you are submitting the review you can decide whether 
- you request changes based on your comments
- your comments are general feedback without explicitly approving the changes or requesting additional changes
- you approve merging the changes proposed in the pull request
5. click submit review

# Pull Request Reviews
**Adopt a positive attitude!**
This is just as important for reviewers as well as submitters. Code reviews are not the time to prove who is a better programmer, nor is it a time to ventilate any personal grudges. You do not need to get defensive. Go in to it with a positive attitude, the code review is a time when more people are working together to make the code better. As a reviewer you can help other person improve their code and you can learn from other people code as well as keeping up your knowledge about the codebase. As submitter you have the opportunity to truly polish up your code and catch any mistakes without real harm done, because it takes place before merging to master. If a mistake is found or improvement is pointed out, everyone wins, because it means the codebase is going to be better after the review. Note that is is not necessary that the senior reviews the code of junior, usually everybody is expected to participate in the review regardless of seniority.

## Reviewers
First of all, you have to **understand the change** you’re reviewing. If you don’t understand the change, you can’t positively review the change. If you are unsure what the pull request is about after reading the description/commit messages, you need to ask the author for a better description.
When you understand the change, there are a few key levels of code review:
1. architecture – Is the code required, are there any improvements to be made through abstractions, reuse of other code. Does the code tie in with the rest of the codebase? These are examples of principles the code should follow
- code re-usability
- naming - e.g, code should be named based on what it does, not based on how it may be used, data models should describe the data and not contain UI concepts, etc.
- encapsulation
- single responsibility
- separation of concerns
to learn more about the principles of clean code and architecture, Clean Code and Clean Architecture books by Robert C. Martin are a good read.
2. functional – Does the code do what it’s supposed to do?
3. style – Is the code idiomatic for the language, are common error-prone patterns for that language avoided, is the code easily understood?
4. syntax – Is the code well formatted, meeting indentation and whitespace standards and free from parse errors?
Comment on specific lines of code if you can to say where the code doesn’t meet standards or could be improved. General feedback on the change as a whole can typically be provided as a comment without referencing a specific line.
**Assume best intentions** and address the code, not the submitter. Code reviews should be objective where possible. You should always justify your comments, so that the submitter can learn. Also if you are unable to justify the comment, it is probably a subjective one.
There are always subjective preferences in any code base. Respect those preferences, unless you have a team guidance on a given topic, the preference is inconsistent with existing codebase or there is an approach that is objectively better than the submitted one. You should however point out if the submitter is inconsistent with him/herself in his subjective choices.
Don't forget it is good to say that everything is ok. You are not obligated to point out at least one improvement.

## Submitters
**Adhere to the standards of your code base**. Most teams agree on standards such as code formatting and style. Make sure your changes adhere to these standards. This will avoid wasting time in the review identifying formatting problems.
**Assume best intentions from the reviewer**. Code review is not a battle, do not take criticism of your code personally. However, if criticism is personal, then you should say so.
Try and reduce conflict resulting from misunderstandings – see if you can clear up such misunderstandings, either in the review, in the commit messages or through talking it through with the reviewer.
