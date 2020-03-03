⏮ ~~Previous step~~&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Add endpoints](./02-create-endpoints.md)

----

## Step 1: Get your environment set up

In this step, you will be using the repository we've created for you for the [previous workshop](../workshop1), and you'll use [.NET Core CLI] to set up the project for your animal shelter REST API.

### Pre-requisites

For this workshop we are going to use [Visual Studio Code] with the C# extension and [.NET Core CLI] to create the project and add nuget packages to it.

You can download and install everything from these links:
- [Visual Studio Code]
- [C# for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
- [.NET Core CLI]

### Cloning your repository

In the previous workshop, you were assigned with a repository where you commited all the UI work. In this workshop, we will continue using that repository to commit the REST API code.

If you can't remember what was the name of your repo, you can go to your github account and in the repositories look for one with a name something like `happy-rover` within the [CodessInTheClassroom GitHub organisation].

If you still have the repo cloned locally, you can continue with the next section. If you delete it, you can clone it again. For this open up your preferred shell:

1. Create a local folder to keep your code and change to it. For example, to
   create `C:\CodessInTheClassroom`:

       mkdir C:\CodessInTheClassroom
       cd C:\CodessInTheClassroom

2. Find your repository within the [CodessInTheClassroom GitHub organisation].

3. Clone your repository using the instructions in [our Git
   cheatsheet](../git-cheatsheet.md#clone). For example:

       git clone https://github.com/codessintheclassroom/happy-rover.git

### Creating a branch for this workshop work

Now we'll create a new branch to hold all the new code for the REST API. This will allow to submit a pull request at the end and get your code review.

1. [Follow the instructions for creating a branch in the Git
   cheatsheet](../git-cheatsheet.md#create-a-branch). You should give it a
   descriptive name so that you know what it's for, such as
   `yourname/shelter-backend` (on some teams developers prefix their branch
   names with their usernames) or `shelter-backend`.

### Creating the initial application code

Now we'll use [.NET Core CLI] to create the initial code for our
application:

1. Using your favourite shell, go to the cloned repo location, for example, if you repository was called `happy-rover`, run `cd c:\CodessInTheClassroom\happy-rover` and run the following command to  generate a web api project `dotnet new webapi -n backend`. This will create a new C# project with some example code for a weather forecast api, that we will override to create our animal shelter API.
2. Run `code -r c:\CodessInTheClassroom\happy-rover\backend` to open the new created project in Visual Studio Code.
If you're interested in what other options you can pass when creating a project using `.NET Core CLI` , you can [read more here](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-new).
3. Let's test now the generated web api, hit `Ctrl+F5` in Visual Studio Code, and it will compile and run the project. If there are no errors, in a browser go to the following URL: [https://localhost:5001/WeatherForecast](https://localhost:5001/WeatherForecast), and the server will return a json document with the weather forecat for the next week.

### Commit the code changes and push to GitHub

So far, we've generated a very basic web api, that we will use to create our animal shelter backend. The `dotnet new webapi` command has created a few files in the repository folder that will be the base for our application.

We'll commit and push this code to our development branch to have a start point. To do that:
1. [Read the guidance on staging changes and committing in the Git cheatsheet](../git-cheatsheet.md#commit).

   For example, you could open a new terminal using `Terminal → New Terminal` and run:

       git add .
       git commit

2. [Read the guidance on pushing your changes in the Git cheatsheet](../git-cheatsheet.md#push).

   For example, in a terminal, you could run:

       git push

[.NET Core CLI]: https://dotnet.microsoft.com/download/dotnet-core/3.1
[Visual Studio Code]: https://code.visualstudio.com/download
[CodessInTheClassroom GitHub organisation]: https://github.com/codessintheclassroom

----

⏮ ~~Previous step~~&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Add endpoints](./02-create-endpoints.md)