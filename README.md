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

## Exercise 11.8 Back to green
**Task:**
Investigate which test fails and fix the issue in the code (do not change the tests).

Once you have fixed all the issues and the Pokedex is bug-free, the workflow run will succeed and show green!

**Solution:**
Pokemon page links were fixed in the code.

## Exercise 11.9 Simple end to end -tests
**Task:**
The current set of tests use Jest to ensure that the React components work as intended. This is exactly the same thing that is done in section [Testing React apps](https://fullstackopen.com/en/part5/testing_react_apps) of part 5.

Testing components in isolation is quite useful but that still does not ensure that the system as a whole works as we wish. To have more confidence about this, let us write a couple of really simple end to end -tests with the Cypress library similarly what we do in section [End to end testing](https://fullstackopen.com/en/part5/end_to_end_testing) of part 5.

So, setup Cypress (you'll find [here](https://fullstackopen.com/en/part5/end_to_end_testing/) all info you need) and use this test at first:
```
describe('Pokedex', function() {
it('front page can be opened', function() {
cy.visit('http://localhost:5000')
cy.contains('ivysaur')
cy.contains('Pokémon and Pokémon character names are trademarks of Nintendo.')
})
})
```
Define a npm script `test:e2e` for running the e2e tests from the command line.

Note do not include the word spec in the Cypress test file name, that would cause also Jest to run it, and it might cause problems.

Note2 end to end tests are pretty slow and than can cause problems when run with the GitHub Actions. Slowness can be remedied by changing App.jsx to fetch a bit less Pokemons, eg. 50 works fine:
```
const {
data: pokemonList, error, isLoading
} = useApi('https://pokeapi.co/api/v2/pokemon/?limit=50', mapResults)
```
The same change must be done in the test file App.jest.spec.jsx

The change is now (16th September 2022) done in the repository, but if you have fetched the code earlier, there might still be a bigger number.

Another thing to note is that despite the page renders the Pokemon names by starting with a capital letter, the names are actually written with lower case letters in the source, so it is ivysaurinstead of Ivysaur!

Ensure that the test passes locally. Remember that the Cypress tests assume that the application is up and running when you run the test! If you have forgotten the details (that happened to me too!), please see [part 5](https://fullstackopen.com/en/part5/end_to_end_testing) how to get up and running with Cypress.

Once the end to end test works in your machine, include it in the GitHub Action workflow. By far the easiest way to do that is to use the ready-made action [cypress-io/github-action](https://github.com/cypress-io/github-action). The step that suits us is the following:
```
- name: e2e tests
  uses: cypress-io/github-action@v2
  with:
  command: npm run test:e2e
  start: npm run start-prod
  wait-on: http://localhost:5000
  Three options are used. command specifies how to run Cypress tests. start gives npm script that starts the server and wait-on says that before the tests are run, the server should have started in url http://localhost:5000.
```
If you are using Cypress 10.X, you may need to revise the steps as follows:
```
- name: e2e tests
  uses: cypress-io/github-action@v4
  with:
  build: npm run build
  start: npm run start-prod
  wait-on: http://localhost:5000
  Once you are sure that the pipeline works, write another test that ensures that one can navigate from the main page to the page of a particular Pokemon, e.g. ivysaur. The test does not need to be a complex one, just check that when you navigate a link, the page has some right content, such as the string chlorophyll in the case of ivysaur.
```
Note also the Pokemon abilities are written with lower case letters, the capitalization is done in CSS, so do not search eg. for Chlorophyll but chlorophyll.

Note2 that you should not try bulbasaur, for some reason the page of that particular Pokemon does not work properly...

End to end -tests are nice since they give us confidence that software works from the end user's perspective. The price we have to pay is the slower feedback time. Now executing the whole workflow takes quite much longer.

**Solution:**
The task was done as instructed.

## Exercises 11.10-11.12. (Fly.io)
Before going to the below exercises, you should setup your application in Fly.io hosting service like the one we did in [part 3](https://fullstackopen.com/en/part3/deploying_app_to_internet#application-to-the-internet).

If you rather want to use Heroku, there is an alternative set of exercises for that.

In contrast to part 3 now we do not deploy the code to Fly.io ourselves (with the command flyctl deploy), we let the GitHub Actions workflow do that for us!

Create a new app in Fly.io and after that generate a Fly.io API token with command
```
flyctl auth token
```
You'll need the token soon for your deployment workflow!

Before setting up the deployment pipeline let us ensure that a manual deployment with the command flyctl deploy works.

You most likely need to do at least two changes. Firstly, define the Node version to use in the file package.json to match one used in your machine. For me it is 16.13.2:
```
{
"engines" : {
"node" : "16.13.2"
},
"name": "fullstackopen-cicd",
"version": "1.0.0",
"description": "Full Stack Open",
// ...
}
```
The configuration file fly.toml should also be modified to include the following:
```
[deploy]
release_command = "npm run build"

[processes]
app = "node app.js"
```
The release_command under [deploy](https://fly.io/docs/reference/configuration/) now ensures that the production built will be done before starting up the app. In [processes](https://fly.io/docs/reference/configuration/#the-processes-section) we define the command that starts the application. Without these changes Fly.io just starts the React dev server and that causes it to shut down since the app itself does not start up.

Here the app refers to the application process that is started up in the [services](https://fly.io/docs/reference/configuration/#the-services-sections) section:
```
[[services]]
http_checks = []
internal_port = 8080
processes = ["app"]  // highlight-line
```

**Solution:**
I had to check different discussion forums, discord channels and other solutions to configure deployment to fly. There seemed to be a significant changes since I worked with fly.io last time.

## Exercise 11.10 Deploying your application to Fly.io
**Task:**
Before starting this exercise, make sure that the manual deployment with the command flyctl deploy works!

Extend the workflow with a step to deploy your application to Fly.io by following the advice given [here](https://fly.io/docs/app-guides/continuous-deployment-with-github-actions/).

You need the authorization token that you just created for the deployment. The proper way to pass it's value to GitHub Actions is to use repository secrets.

Now the workflow can access the token value as follows:
```
${{secrets.FLY_API_TOKEN}}
```
You can then try the app with a browser, but most likely you run into a problem. If we read carefully the section ['Application to the Internet' in part 3](https://fullstackopen.com/en/part3/deploying_app_to_internet#application-to-the-internet)

Remember that it is always essential to keep an eye on what is happening in server logs when playing around with product deployments, so use flyctl logsearly and use it often. No, use it all the time!

**Solution:**
Configured as instructed, after merge to master app deployed without any errors in logs.

## Exercise 11.11 Health check and rollback
**Task:**
Each deployment in Fly.io creates a [release](https://fly.io/docs/flyctl/releases/). Releases can be checked from the command line:
```
$ flyctl releases
VERSION	STABLE	TYPE    	STATUS   	DESCRIPTION            	USER           	DATE
v13    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	30m6s ago
v12    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	51m30s ago
v11    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	59m25s ago
v10    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	1h6m ago
```
It is essential to ensure that a deployment ends up to a succeeding release, where the app is in healthy functional state. Fortunately Fly.io has several configuration options that take care of the application health check.

The default fly.toml has already a section [services.tcp_checks](https://fly.io/docs/reference/configuration/#services-tcp_checks)
```
[[services.tcp_checks]]
grace_period = "1s"
interval = "15s"
restart_limit = 0
timeout = "2s"
```
This section defines a basic health check of the deployment. The TCP check ensures that the virtual machine where the app resides is up and running and reachable from outside, by opening a TCP connection to the virtual machine.

This check notices if something is fundamentally broken in the configurations. E.g. in my case for the app of this part, it took several trials until I got the app up and running:
```
$ fly releases
VERSION	STABLE	TYPE    	STATUS   	DESCRIPTION            	USER           	DATE
v4     	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	5h39m ago
v3     	false 	release 	failed   	Deploy image           	mluukkai@iki.fi	5h50m ago
v2     	false 	release 	failed   	Deploy image           	mluukkai@iki.fi	5h57m ago
v1     	false 	release 	failed   	Deploy image           	mluukkai@iki.fi	6h12m ago
v0     	false 	release 	failed   	Deploy image           	mluukkai@iki.fi	6h19m ago
```
So finally in the 5th deployment (version v4) I got the configuration right and that ended in a succeeding release.

Besides the rudimentary TCP health check, it is extremely beneficial to have also some "application level" health checks that ensure that the app for real is in functional state. One possibility for this is a HTTP-level check defined in section [services.http_checks](https://fly.io/docs/reference/configuration/#services-tcp_checks) that can be used to ensure that the app is responding to the HTTP requests.

Add a simple endpoint for doing an application health check to the backend. You may e.g. copy this code:
```
app.get('/health', (req, res) => {
res.send('ok')
})
```
Configure then a [HTTP-check](https://fly.io/docs/reference/configuration/#services-http_checks) that ensures the health of the depyments based on the HTTP request to the defined health check endpoint.

Note that the default fly.toml has defined that http_checks is an empty array. You need to remove this line when you are adding a manually defined HTTP-check:
```
[[services]]
http_checks = []
```
It might also be a good idea to have a dummy endpoint in the app that makes it possible to do some code changes and to ensure that the deployed version has really changed:
```
app.get('/version', (req, res) => {
res.send('1') // change this string to ensure a new version deployed
})
```
Ensure that Actions notices if a deployment breaks your application:

fullstack content
You may simulate this e.g. as follows:
```
app.get('/health', (req, res) => {
throw 'error...'
// eslint-disable-next-line no-unreachable
res.send('ok')
})
```
As can be seen in the command line, when a deployment fails, Fly.io rolls back to the previous working release:
```
$ fly releases
VERSION	STABLE	TYPE    	STATUS   	DESCRIPTION            	USER           	DATE
v15    	true  	rollback	succeeded	Reverting to version 13	               	16m48s ago
v14    	false 	release 	failed   	Deploy image           	mluukkai@iki.fi	21m53s ago
v13    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	30m6s ago
v12    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	51m30s ago
v11    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	59m25s ago
v10    	true  	release 	succeeded	Deploy image           	mluukkai@iki.fi	1h6m ago
```
So despite the problems in the relese, the app stays functional!

Before moving to next exercise, fix your deployment and ensure that the application works again as intended.

**Solution:**
Configured and tested as instructed.

# Restarted work on this course
> I did not notice any major changes in the content of the course from the version 
> when I completed exercises 11.1 - 11.9.
> For this reason, I picked up from where I finished.
> 
> However, there have been changes in Fly.io and their free tier. 
> For this reason, I will redo that part to ensure it still works.

## Redo Exercise 11.10 Deploying your application to Fly.io
*Before completing the exercise, the pipeline is green. The previously done 11.10 is removed.*

**Task:**

Setup your application in [Fly.io](https://fly.io/) hosting service like the one we did in [part 3](https://fullstackopen.com/en/part3/deploying_app_to_internet#application-to-the-internet).

In contrast to part 3, in this part we do not deploy the code to Fly.io ourselves (with the command flyctl deploy), we let the GitHub Actions workflow do that for us.

Before going to the automated deployment, we shall ensure in this exercise that the app can be deployed manually.

So, create a new app in Fly.io. After that generate a Fly.io API token with the command
```
flyctl auth token
```
You'll need the token soon for your deployment workflow so save it somewhere (but do not commit that to GitHub)!

As said, before setting up the deployment pipeline in the next exercise we will now ensure that a manual deployment with the command flyctl deploy works.

A couple of changes are needed.

The configuration file fly.toml should be modified to include the following:
```
[env]
PORT = "3000" # add this where PORT matches the internal_port below

[processes]
app = "node app.js" # add this

[http_service]
internal_port = 3000
force_https = true
auto_stop_machines = true
auto_start_machines = true
min_machines_running = 0
processes = ["app"]
```
In [processes](https://fly.io/docs/reference/configuration/#the-processes-section) we define the command that starts the application. Without this change Fly.io just starts the React dev server and that causes it to shut down since the app itself does not start up. We will also set up the PORT to be passed to the app as an environment variable.

We also need to alter the file .dockerignore a bit, the next line should be removed:
```
dist
```
If the line is not removed, the product build of the frontend does not get downloaded to the Fly.io server.

Deployment should now work if the production build exists in the local machine, that is, the command npm build is run.

Before moving to the next exercise, make sure that the manual deployment with the command `flyctl deploy` works!

**Solution:**
I could not build the app locally due to mismatch in node.js versions, and no willingness to go through workarounds.
Also, building Dockerfile was not an easy option since some of the packages were not available for ARM architecture.
However, I used an older built (from before I restarted the work on the course) which worked.

## Redo Exercise 11.11 Automatic deployments
**Task:**
Extend the workflow with a step to deploy your application to Fly.io by following the advice given [here](https://fly.io/docs/app-guides/continuous-deployment-with-github-actions/).

Note that the GitHub Action should create the production build (with npm run build) before the deployment step!

You need the authorization token that you just created for the deployment. The proper way to pass it's value to GitHub Actions is to use Repository secrets.

Now the workflow can access the token value as follows:
```
${{secrets.FLY_API_TOKEN}}
```

> Remember that it is always essential to keep an eye on what is happening 
> in server logs when playing around with product deployments, 
> so use `flyctl logs` early and use it often. 
> No, use it all the time!


**Solution**
Updated [pipeline.yml](.github/workflows/pipeline.yml). Deploy was successful after merging a PR to master branch.

...from logs:
```
Running muddy-thunder-3474-icy-shape-7791 release_command: npm run build
> Created release_command machine e784ee72c54558
> Waiting for e784ee72c54558 to have state: started
> Machine e784ee72c54558 has state: started
> Waiting for e784ee72c54558 to have state: destroyed
> Machine e784ee72c54558 has state: destroyed
> Waiting for e784ee72c54558 to get exit event
✔ release_command e784ee72c54558 completed successfully
Updating existing machines in 'muddy-thunder-3474-icy-shape-7791' with rolling strategy
> Updating d8d9919cee9778 [app]
> Updating d8d9919cee9778 [app]
✔ Machine d8d9919cee9778 [app] update succeeded
Checking DNS configuration for muddy-thunder-3474-icy-shape-7791.fly.dev

Visit your newly deployed app at https://muddy-thunder-3474-icy-shape-7791.fly.dev/
```

## Exercise 11.12 Health check
**Task**

Each deployment in Fly.io creates a [release](https://fly.io/docs/flyctl/releases/). Releases can be checked from the command line:
```
$ flyctl releases
VERSION	STATUS  	DESCRIPTION	USER           	DATE
v18    	complete	Release    	mluukkai@iki.fi	16h56m ago
v17    	complete	Release    	mluukkai@iki.fi	17h3m ago
v16    	complete	Release    	mluukkai@iki.fi	21h22m ago
v15    	complete	Release    	mluukkai@iki.fi	21h25m ago
v14    	complete	Release    	mluukkai@iki.fi	21h34m ago
```
It is essential to ensure that a deployment ends up in a succeeding release, where the app is in healthy functional state. Fortunately, Fly.io has several configuration options that take care of the application health check.

If we change the app as follows, it fails to start:
```
app.listen(PORT, () => {
this_causes_error
// eslint-disable-next-line no-console
console.log(`server started on port ${PORT}`)
})
```
In this case, the deployment fails:
```
$ flyctl releases
VERSION	STATUS  	DESCRIPTION	USER           	DATE
v19    	failed  	Release    	mluukkai@iki.fi	3m52s ago
v18    	complete	Release    	mluukkai@iki.fi	16h56m ago
v17    	complete	Release    	mluukkai@iki.fi	17h3m ago
v16    	complete	Release    	mluukkai@iki.fi	21h22m ago
v15    	complete	Release    	mluukkai@iki.fi	21h25m ago
v14    	complete	Release    	mluukkai@iki.fi	21h34m ago
```
The app however stays up and running, Fly.io does not replace the functioning version (v18) with the broken one (v19).

Let us consider the following change
```
// start app in a wrong port
app.listen(PORT + 1, () => {
// eslint-disable-next-line no-console
console.log(`server started on port ${PORT}`)
})
```
Now the app starts but it is connected to the wrong port, so the service will not be functional. Fly.io thinks this is a successful deployment, so it deploys the app in a broken state.

One possibility to prevent broken deployments is to use an HTTP-level check defined in section [http_service.http_checks](https://fly.io/docs/reference/configuration/#http_service-checks). This type of check can be used to ensure that the app for real is in a functional state.

Add a simple endpoint for doing an application health check to the backend. You may e.g. copy this code:
```
app.get('/health', (req, res) => {
res.send('ok')
})
```
Configure then an [HTTP check](https://fly.io/docs/reference/configuration/#http_service-checks) that ensures the health of the deployments based on the HTTP request to the defined health check endpoint.

You also need to set the [deployment strategy](https://fly.io/docs/reference/configuration/#picking-a-deployment-strategy) (in the file fly.toml) of the app to be either canary or bluegreen. These strategies ensure that only an app with a healthy state gets deployed.

Ensure that GitHub Actions notices if a deployment breaks your application.

You may simulate this e.g. as follows:
```
app.get('/health', (req, res) => {
// eslint-disable-next-line no-constant-condition
if (true) throw('error...  ')
res.send('ok')
})
```

**Solution:**
Implemented http health check as instructed.
simulated error in /health endpoint failed the deploy:
```
2024-02-26T10:47:42.435 app[0806994b69e908] arn [info] WARN hallpass exited, pid: 307, status: signal: 15 (SIGTERM)
```

```
% flyctl releases
VERSION STATUS          DESCRIPTION     USER                            DATE       
v7      failed          Release         rohal.dominik.123@gmail.com     7m45s ago       
v6      complete        Release         rohal.dominik.123@gmail.com     17m30s ago      
v5      complete        Release         rohal.dominik.123@gmail.com     24m15s ago      
v4      complete        Release         rohal.dominik.123@gmail.com     37m7s ago       
v3      complete        Release         rohal.dominik.123@gmail.com     1h1m ago        
```

*The application was fixed back to green state.*

## Exercise 11.13 Pull request
**Task:**

Update the trigger of the existing workflow as suggested above to run on new pull requests to your main branch.

Create a new branch, commit your changes, and open a pull request to your main branch.

If you have not worked with branches before, check e.g. [this tutorial](https://www.atlassian.com/git/tutorials/using-branches) to get started.

Note that when you open the pull request, make sure that you select here your own repository as the destination base repository. By default, the selection is the original repository by https://github.com/fullstack-hy2020 and you do not want to do that.

In the "Conversation" tab of the pull request you should see your latest commit(s) and the yellow status for checks in progress.

**Solution:**
Updated [pipeline.yml](.github/workflows/pipeline.yml) to trigger pipeline when PR is opened.

## Exercise 11.14 Run deployment step only for the main branch
**Task:**

All looks good, but there is actually a pretty serious problem with the current workflow. All the steps, including the deployment, are run also for pull requests. This is surely something we do not want!

Fortunately, there is an easy solution for the problem! We can add an [if condition](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idstepsif) to the deployment step, which ensures that the step is executed only when the code is being merged or pushed to the main branch.

The workflow [context](https://docs.github.com/en/free-pro-team@latest/actions/reference/context-and-expression-syntax-for-github-actions#contexts) gives various kinds of information about the code the workflow is run.

The relevant information is found in [GitHub context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context), the field event_name tells us what is the "name" of the event that triggered the workflow. When a pull request is merged, the name of the event is somehow paradoxically push, the same event that happens when pushing the code to the repository. Thus, we get the desired behavior by adding the following condition to the step that deploys the code:
```
if: ${{ github.event_name == 'push' }}
```
Push some more code to your branch, and ensure that the deployment step is not executed anymore. Then merge the branch to the main branch and make sure that the deployment happens. 

**Solution:**
Updated [pipeline.yml](.github/workflows/pipeline.yml) to trigger deploy step only on push event.

## Exercise 11.15 Adding versioning
**Task:**
We will extend our workflow with one more step:
```
- name: Bump version and push tag
  uses: anothrNick/github-tag-action@1.64.0
  env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
Note: you should use the most recent version of the action, see [here](https://github.com/anothrNick/github-tag-action) if a more recent version is available.

We're passing an environmental variable secrets.GITHUB_TOKEN to the action. As it is third party action, it needs the token for authentication in your repository. You can read more [here](https://docs.github.com/en/actions/configuring-and-managing-workflows/authenticating-with-the-github_token) about authentication in GitHub Actions.

You may end up having "Tag was not created properly" error which is most likely caused by the token not having write permission to your repository.

The [anothrNick/github-tag-action](https://github.com/anothrNick/github-tag-action) action accepts some environment variables that modify the way the action tags your releases. You can look at these in the [README](https://github.com/anothrNick/github-tag-action) and see what suits your needs.

As you can see from the documentation by default your releases will receive a minor bump, meaning that the middle number will be incremented.

Modify the configuration above so that each new version is by default a patch bump in the version number, so that by default, the last number is increased.

Remember that we want only to bump the version when the change happens to the main branch! So add a similar if condition to prevent version bumps on pull request as was done in [Exercise 11.14](https://fullstackopen.com/en/part11/keeping_green#exercises-11-13-11-14) to prevent deployment on pull request related events.

Complete now the workflow. Do not just add it as another step, but configure it as a separate job that [depends](https://docs.github.com/en/actions/using-workflows/advanced-workflow-features#creating-dependent-jobs) on the job that takes care of linting, testing and deployment. So change your workflow definition as follows:
```
name: Deployment pipeline

on:
  push:
    branches:
      - main
  pull_request:
    branches: [main]
    types: [opened, synchronize]

jobs:
  simple_deployment_pipeline:
    runs-on: ubuntu-20.04
    steps:
      // steps here
  tag_release:
    needs: [simple_deployment_pipeline]
    runs-on: ubuntu-20.04
    steps:
      // steps here
```
As was mentioned [earlier](https://fullstackopen.com/en/part11/getting_started_with_git_hub_actions#getting-started-with-workflows) jobs of a workflow are executed in parallel but since we want the linting, testing and deployment to be done first, we set a dependency that the tag_release waits the another job to execute first since we do not want to tag the release unless it passes tests and is deployed.

If you're uncertain of the configuration, you can set DRY_RUN to true, which will make the action output the next version number without creating or tagging the release!

**Solution:**
Implemented as instructed. Tak [0.0.1](https://github.com/drohal3/fullstackopen-part11/releases/tag/0.0.1) automatically created.

## Exercise 11.16 Skipping a commit for tagging and deployment
**Task:**
In general, the more often you deploy the main branch to production, the better. However, there might be some valid reasons sometimes to skip a particular commit or a merged pull request to become tagged and released to production.

Modify your setup so that if a commit message in a pull request contains #skip, the merge will not be deployed to production and it is not tagged with a version number.

Hints:

The easiest way to implement this is to alter the if conditions of the relevant steps. Similarly to [exercise 11-14](https://fullstackopen.com/en/part11/keeping_green#exercises-11-13-11-14) you can get the relevant information from the [GitHub context](https://docs.github.com/en/free-pro-team@latest/actions/reference/context-and-expression-syntax-for-github-actions#github-context) of the workflow.

You might take this as a starting point:
```
name: Testing stuff

on:
  push:
    branches:
      - main

jobs:
  a_test_job:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v4
      - name: github context
        env:
          GITHUB_CONTEXT: ${{ toJson(github) }}
        run: echo "$GITHUB_CONTEXT"
      - name: commits
        env:
          COMMITS: ${{ toJson(github.event.commits) }}
        run: echo "$COMMITS"
      - name: commit messages
        env:
          COMMIT_MESSAGES: ${{ toJson(github.event.commits.*.message) }}
        run: echo "$COMMIT_MESSAGES"
```

See what gets printed in the workflow log!

Note that you can access the commits and commit messages only when pushing or merging to the main branch, so for pull requests the github.event.commits is empty. It is anyway not needed, since we want to skip the step altogether for pull requests.

You most likely need functions [contains](https://docs.github.com/en/actions/learn-github-actions/expressions#contains) and [join](https://docs.github.com/en/actions/learn-github-actions/expressions#join) for your if condition.

Developing workflows is not easy, and quite often the only option is trial and error. It might actually be advisable to have a separate repository for getting the configuration right, and when it is done, to copy the right configurations to the actual repository.

It would also be possible to install a tool such as [act](https://github.com/nektos/act) that makes it possible to run your workflows locally. Unless you end up using more involved use cases like creating your [own custom actions](https://docs.github.com/en/free-pro-team@latest/actions/creating-actions), going through the burden of setting up a tool such as act is most likely not worth the trouble.

**Solution:**
[pipline.yml](.github/workflows/pipeline.yml) modified as instructed and worked as expected.

## Exercise 11.17 Adding protection to your main branch
**Task:**
Add protection to your main branch.

You should protect it to:
- Require all pull request to be approved before merging
- Require all status checks to pass before merging

**Solution:**
The branch protection rule was added.

## Exercise 11.18 Build success/failure notification action
**Task:**

You can find quite a few third-party actions from [GitHub Action Marketplace](https://github.com/marketplace?type=actions) by using the search phrase [discord](https://github.com/marketplace?type=actions&query=discord). Pick one for this exercise. My choice was [discord-webhook-notify](https://github.com/marketplace/actions/discord-webhook-notify) since it has quite many stars and decent documentation.

Setup the action so that it gives two types of notifications:

- A success indication if a new version gets deployed
- An error indication if a build fails

In the case of an error, the notification should be a bit more verbose to help developers find quickly which is the commit that caused it.

See [here](https://docs.github.com/en/actions/learn-github-actions/expressions#status-check-functions) how to check the job status!

**Solution:**
Implemented as instructed.

## Exercise 11.19 Periodic health check
**Task:**

We are pretty confident now that our pipeline prevents bad code from being deployed. However, there are many sources of errors. If our application would e.g. depend on a database that would for some reason become unavailable, our application would most likely crash. That's why it would be a good idea to set up a periodic health check that would regularly do an HTTP GET request to our server. We quite often refer to this kind of request as a ping.

It is possible to [schedule](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule) GitHub actions to happen regularly.

Use now the action [url-health-check](https://github.com/marketplace/actions/url-health-check) or any other alternative and schedule a periodic health check ping to your deployed software. Try to simulate a situation where your application breaks down and ensure that the check detects the problem. Write this periodic workflow to an own file.

Note that unfortunately it takes quite long until GitHub Actions starts the scheduled workflow for the first time. For me, it took nearly one hour. So it might be a good idea to get the check working firstly by triggering the workflow with Git push. When you are sure that the check is properly working, then switch to a scheduled trigger.

Note also that once you get this working, it is best to drop the ping frequency (to max once in 24 hours) or disable the rule altogether since otherwise your health check may consume all your monthly free hours.

**Solution:**
Simulated with trigger on push