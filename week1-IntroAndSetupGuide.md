# Part 1
This chapter will get you setup on your repository, and kick start your front end code.

## Setting up

As a preparation for this session you should have received a repository name (if you don't, let an instructor know), have git and some git client installed. Also, please make sure you have read and completed all the [Requirements](https://github.com/codessintheclassroom/classroom-material/blob/master/REQUIREMENTS.md) for this workshop.

With your repo name in hands (it will be your working repo for the duration of the project), let's get started! 

 1. Create a local folder to keep your code. Ex: C:\CodessInTheClassroom.
 2. Find your repo at [CodessInTheClassrom GitHub project](https://github.com/codessintheclassroom).
 3.  `git clone` your repository.
     3.1. If you're using GitHub desktop, see [this page](https://help.github.com/en/desktop/contributing-to-projects/cloning-a-repository-from-github-desktop) for further instructions on cloning.

At this stage you have your code checked out locally, and by default you would be working off the `master` branch. We should avoid committing and pushing code straight to `master`, as this branch is usually where your stable code should be (we normally use `master` as a source for production code). We'll talk about this in a bit more detail when we discuss Pull Requests. 
Having that in mind, we will now:

 1. Create a new branch for the next coding steps
     1.1. Make sure you have a descriptive branch name. Ex: `your-username/workshop1-adding-react-app`.
     1.2. If you're using GitHub desktop, see [this page](https://help.github.com/en/desktop/contributing-to-projects/creating-a-branch-for-your-work) for detailed instructions.

## Starting the app 
 This section will give you the steps to generate the base code to start our application. 
 We'll start by creating a [React](https://reactjs.org/) app: 
 
1. Install the latest long term support (LTS) version of node js from https://nodejs.org/en/. Currently this is version 10.
    1.1. Avoid non LTS versions, e.g. version 11, since they tend to have bugs.
2. Launch Visual Studio Code and use `File -> Open Folder` and open the folder `front-end`. It will be under the folder we created on the previous sections (Ex: CodessInTheClassroom).  
3. Open a terminal by clicking on `Terminal -> New Terminal`. 
4. Create and start a basic typescript based web application. Run the following commands:
	```
	 > npx create-react-app web-application --typescript
	 > cd web-application
	 > npm start
	```
	 See [create-react-app on github](https://github.com/facebook/create-react-app)  for more info.
5. Navigate to http://localhost:3000/ to see the running application.

