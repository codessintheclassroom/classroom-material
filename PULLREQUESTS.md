# Creating Pull Requests

# Pull Request Reviews
**Adopt a positive attitude!**
This is just as important for reviewers as well as submitters. Code reviews are not the time to prove who is a better programmer, nor is it a time to ventilate any personal grudges. You do not need to get defensive. Go in to it with a positive attitude, the code review is a time when more people are working together to make the code better. As a reviewer you can help other person improve their code, as submitter you have the opportunity to truly polish up your code and catch any mistakes without real harm done, because it takes place before merging to master. If a mistake is found or improvement is pointed out, everyone wins, because it means the codebase is going to be better after the review. 

## Reviewers
First of all, you have to **understand the change** you’re reviewing. If you don’t understand the change, you can’t positively review the change. If you are unsure what the pull request is about after reading the description/commit messages, you need to ask the author for a better description.
When you understand the change, there are a few key levels of code review:
1. architecture – Is the code required, are there any improvements to be made through abstractions, reuse of other code. Does the code tie in with the rest of the codebase?
2. functional – Does the code do what it’s supposed to do?
3. style – Is the code idiomatic for the language, are common error-prone patterns for that language avoided, is the code easily understood?
4. syntax – Is the code well formatted, meeting indentation and whitespace standards and free from parse errors?
Comment on specific lines of code if you can to say where the code doesn’t meet standards or could be improved. General feedback on the change as a whole can typically be provided as a comment without referencing a specific line.
**Assume best intentions** and address the code, not the submitter. Code reviews should be objective where possible. There are always subjective preferences in any code base. Respect those preferences, unless you have a team guidance on a given topic, the preference is inconsistent with existing codebase or there is an approach that is objectively better than the submitted one. You should however point out if the submitter is inconsistent with him/herself in his subjective choices.
Don't forget it is good to say that everything is ok. You are not obligated to point out at least one improvement.

## Submitters
**Adhere to the standards of your code base**. Most teams agree on standards such as code formatting and style. Make sure your changes adhere to these standards. This will avoid wasting time in the review identifying formatting problems.
**Assume best intentions from the reviewer**. Code review is not a battle, do not take criticism of your code personally. However, if criticism is personal, then you should say so.
Try and reduce conflict resulting from misunderstandings – see if you can clear up such misunderstandings, either in the review, in the commit messages or through talking it through with the reviewer.
