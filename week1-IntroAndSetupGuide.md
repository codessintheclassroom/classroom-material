# Part 1
This chapter will cover getting setup on your repository and kick start your front end code.

## Setting up

As a preparation for this session you should have received a repository name (if you don't, let an instructor know), have git and some git client setup. Also, please make sure you have read and completed all the [Requirements](https://github.com/codessintheclassroom/classroom-material/blob/master/REQUIREMENTS.md) for this workshop.

Please have your repo name in hands (it will be your working repo for the duration of the project), and let's get started! 

 1. Create a local folder to keep your code. Ex: C:\CodessInTheClassroom
 2. Find your repo at [CodessInTheClassrom GitHub project](https://github.com/codessintheclassroom) 
 3.  `git clone` your repository -> Will we suggest a git client? So I can give detailed instructions on how to git clone? (or link a how to)

At this stage you have your code checked out locally, and by default you would be working off the `master` branch. We should avoid committing and pushing code straight to `master`, as this branch is usually where your stable code should be (we normally use `master` as a source for production code). We'll see a little more of this when we discuss Pull Requests. 
To address the different branching strategies, a few different models were proposed, the most notable being [GitFlow](https://nvie.com/posts/a-successful-git-branching-model/) or some variation of it.
Having that in mind, we will now:

 1. Create a new branch for the next coding steps
 1.1. Give specifics on the git client they will use? 

## Starting the app 
 This section will give you the steps to generate the base code to start our application. We'll start by creating a [React](https://reactjs.org/) app: 
 
1. Install the latest long term support (LTS) version of node js from https://nodejs.org/en/. Currently this is version 10.
1.1. Avoid non LTS versions, e.g. version 11, since they tend to have bugs.
2. Launch Visual Studio Code and use `File -> Open Folder` and open the folder `front-end`. It will be under the folder we created on the previous sections (Ex: CodessInTheClassroom)  
3. Open a terminal by clicking on `Terminal -> New Terminal`. 
4. Create and start a basic typescript based web application. Run the following commands:
	 `> npx create-react-app web-application --typescript`
	 `> cd web-application`
	 `> npm start` 
	 See [create-react-app on github](https://github.com/facebook/create-react-app)  for more info.
5. Navigate to http://localhost:3000/ to see the running application.

