# Full Stack open CI/CD

This repository is used for the CI/CD module of the Full stack open course

Fork the repository to complete course exercises

## Commands

Start by running `npm install` inside the project folder

`npm start` to run the webpack dev server
`npm test` to run tests
`npm run eslint` to run eslint
`npm run build` to make a production build
`npm run start-prod` to run your production build

## # Exercise 11.1.
**Task:**
Write a short text, say 200-300 words, where you answer or discuss some of the points below. You can check the length with https://wordcounter.net/. Save your answer to the file named exercise1.md in the root of the repository that you shall create in exercise 11.2.

The points to discuss:
- Some common steps in a CI setup include linting, testing, and building. What are the specific tools for taking care of these steps in the ecosystem of the language you picked? You can search for the answers by google.
- What alternatives are there to set up the CI besides Jenkins and GitHub Actions? Again, you can ask google!
- Would this setup be better in a self-hosted or a cloud-based environment? Why? What information would you need to make that decision?

The answer is provided in the [exercise1.md](./exercise1.md) file.

## 11.2 The example project
**Task:**
The first thing you'll want to do is to fork the example repository under your name. What it essentially does is it creates a copy of the repository under your GitHub user profile for your use.

To fork the repository, you can click on the Fork button in the top-right area of the repository view next to the Star button:

Once you've clicked on the Fork button, GitHub will start the creation of a new repository called {github_username}/full-stack-open-pokedex.

Once the process has been finished, you should be redirected to your brand new repository:

Clone the project now to your machine. As always, when starting with a new code, the most obvious place to look first is the file package.json

Try now the following:

- install dependencies (by running `npm install`)
- start the code in development mode
- run tests
- lint the code
You might notice that project contains some broken tests and linting errors. Just leave them as they are for now. We will get around those later in the exercises.

As you might remember from [part 3](https://fullstackopen.com/en/part3/deploying_app_to_internet#frontend-production-build), the React code should not be run in development mode once it is deployed in production. Try now the following

- create a production build of the project
- run the production version locally
Also for these two tasks, there are ready-made npm scripts in the project!

Study the structure of the project for a while. As you notice both the frontend and the backend code is now [in the same repository](https://fullstackopen.com/en/part7/class_components_miscellaneous#frontend-and-backend-in-the-same-repository). In earlier parts of the course we had a separate repository for both, but having those in the same repository makes things much simpler when setting up a CI environment.

In contrast to most projects in this course, the frontend code does not use create-react-app, but it has a relatively simple [webpack](https://fullstackopen.com/en/part7/webpack) configuration that takes care of creating the development environment and creating the production bundle.

**Solution:**

*Note:* I decided to choose different name of the repository than instructed in the materials to ensure the consistency in naming repositories for different parts of this course.
The production build did not work when running the predifined scripts:

```
% npm run start-prod                             

> fullstackopen-cicd@1.0.0 start-prod
> node app.js

node:events:491
      throw er; // Unhandled 'error' event
      ^

Error: listen EADDRINUSE: address already in use :::5000
    at Server.setupListenHandle [as _listen2] (node:net:1432:16)
    at listenInCluster (node:net:1480:12)
    at Server.listen (node:net:1568:7)
    at Function.listen (/Users/rohal/projects/fullstackopen/fullstackopen-part11/node_modules/express/lib/application.js:618:24)
    at Object.<anonymous> (/Users/rohal/projects/fullstackopen/fullstackopen-part11/app.js:9:5)
    at Module._compile (node:internal/modules/cjs/loader:1126:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1180:10)
    at Module.load (node:internal/modules/cjs/loader:1004:32)
    at Function.Module._load (node:internal/modules/cjs/loader:839:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
Emitted 'error' event on Server instance at:
    at emitErrorNT (node:net:1459:8)
    at processTicksAndRejections (node:internal/process/task_queues:83:21) {
  code: 'EADDRINUSE',
  errno: -48,
  syscall: 'listen',
  address: '::',
  port: 5000
}
```

## Exercise 11.3 Hello world!
**Task:**
Create a new Workflow which outputs "Hello World!" to the user. For the setup, you should create the directory .github/workflowsand a file hello.ymlto your repository.

To see what your GitHub Action workflow has done, you can navigate to the Actions tab in GitHub where you should see the workflows in your repository and the steps they implement. The output of your Hello World workflow should look something like this with a properly configured workflow.

You should see the "Hello World!" message as an output. If that's the case then you have successfully gone through all the necessary steps. You have your first GitHub Actions workflow active!

Note that GitHub Actions also informs you on the exact environment (operating system, and its setup) where your workflow is run. This is important since if something surprising happens, it makes debugging so much easier if you can reproduce all the steps in your machine!

**Solution:**
The task was completed as instructed.

## Exercise 11.4 Date and directory contents
**Task:**
Extend the workflow with steps that print the date and current directory content in long format.

Both of these are easy steps, and just running commands [date](https://man7.org/linux/man-pages/man1/date.1.html) and [ls](https://man7.org/linux/man-pages/man1/ls.1.html) will do the trick.

As the output of command `ls -l` shows, by default, the virtual environment that runs our workflow does not have any code!

**Solution:**
The task was completed as instructed.

## Exercise 11.5 Linting workflow
**Task:**
Implement or copy-paste the "Lint" workflow and commit it to the repository. Use a new yml file for this workflow, you may call it e.g. pipeline.yml.

Push your code and navigate to "Actions" tab and click on your newly created workflow on the left. You should see that the workflow run has failed.

**Solution:**
The task was completed as instructed.

## Exercise 11.6 Fix the code
**Task:**
There are some issues with the code that you will need to fix. Open up the workflow logs and investigate what is wrong.

A couple of hints. One of the errors is best to be fixed by specifying proper env for linting, see [here](https://fullstackopen.com/en/part3/validation_and_es_lint#lint) how it can be done . One of the complaints concerning console.logstatement could be taken care of by simply silencing the rule for that specific line. Ask google how to do it.

Make the necessary changes to the source code so that the lint workflow passes. Once you commit new code the workflow will run again and you will see updated output where all is green again.

**Solution:**
The linting problems were fixed as instructed.

## Exercise 11.7 Building and testing
**Task:**
Let's expand on the previous workflow that currently does the linting of the code. Edit the workflow and similarly to the lint command add commands for build and test.

**Solution:**
The task was completed as instructed.