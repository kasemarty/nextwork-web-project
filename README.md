# Java Web App Deployment with AWS CI/CD

Welcome to this project combining Java web app development and AWS CI/CD tools!

<br>

## Table of Contents
- [Introduction](#introduction)
- [Technologies](#technologies)
- [Setup](#setup)
- [Contact](#contact)
- [Conclusion](#conclusion)

<br>

## Introduction
This project is used for an introduction to creating and deploying a Java-based web app using AWS, especially their CI/CD tools.

The deployment pipeline I'm building around the Java web app in this repository is invisible to the end-user, but makes a big impact by automating the software release processes.

I am doing this project to learn more about CI/CD and get hands on experience in automating the flow from developing code to deployed web app. This fits into my career goals because I want to become a DevOps engineer this year.

<br>

## Technologies
Here’s what I’m using for this project:
- Key pairs, SSH connections, Git, Maven
- **Amazon EC2**: I'm developing my web app on Amazon EC2 virtual servers, so that software development and deployment happens entirely on the cloud.
- **VS Code**: For my IDE, I chose Visual Studio Code. It connects directly to my development EC2 instance, making it easy to edit code and manage files in the cloud.
- **GitHub**: All my web app code is stored and versioned in this GitHub repository.
- **AWS CodeArtifact**: Once it's rolled out, CodeArtifact will store my artifacts and dependencies, which is great for high availability and speeding up my project's build process.
- **AWS CodeBuild**: Once it's rolled out, CodeBuild will take over my build process. It'll compile the source code, run tests, and produce ready-to-deploy software packages automatically.
- **[COMING SOON] AWS CodeDeploy**: Once it's rolled out, CodeDeploy will automate my deployment process across EC2 instances.
- **[COMING SOON] AWS CodePipeline**: Once it's rolled out, CodePipeline will automate the entire process from GitHub to CodeDeploy, integrating build, test, and deployment steps into one efficient workflow.


<br>

## Setup
To get this project up and running on your local machine, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/nextwork-web-project.git
    ```
2. Navigate to the project directory:
    ```bash
    cd nextwork-web-project
    ```
3. Install dependencies:
    ```bash
    mvn install
    ```

<br>

## Projects 1 - 7

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

## 1 Set Up a Web App in the Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-vscode)

**Author:** Martin Kaše  
**Email:** kase.martin@hotmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

In this project, we're going to set up the foundations of a CI/CD pipeline by creating the web app from scratch. We will need to launch an EC2 instance and connect to the instance using VSCode to generate a web app inside.

### Key tools and concepts

The key services and concepts learned in this AWS DevOps project involved setting up a cloud-based web app using AWS and VS Code. The project covered fundamental AWS steps such as creating an IAM user, launching an EC2 instance, connecting with VS Code, and configuring developer tools for building and testing applications in a DevOps workflow. Essential DevOps concepts included CI/CD practices, infrastructure automation, and application deployment leveraging AWS services like EC2, IAM, and integration with VS Code for streamlined development.

### Project reflection

One thing I didn't expect in this project was such a detailed walkthrough guide, which was easy to follow and straightforward. I also liked the instructive video with Natasha, which was very helpful.

This project took me approximately 3 hours to complete. The most challenging part was setting up the AWS instance but it was the most rewarding experience when all the work was worth it and everything worked in the end.

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project in a day.

---

## Launching an EC2 instance

I started this project by launching an EC2 instance because EC2 instances are like computers that live in a cloud. We want our web app to live entirely in the cloud where we develop it also.

### I also enabled SSH

SSH is the protocol that authorizes users to access remote servers like EC2 instances. It is also a type of traffic that lets me transfer data back and forth with my EC2 instance once I am connected to it. I enabled SSH to securely connect to EC2.

### Key pairs

A key pair is a mechanism for me to get access to EC2 instances we launch in AWS. I've created a keypair for EC2 instance Keypairs work by having two halves public key and private key, that we download. AWS will authenticate the public key by matchin

Once I set up my key pair, AWS automatically downloaded the private key file called nextwork-key-pair.pem for safekeeping. I moved that private key file into a folder called DevOps in my desktop.

---

## Set up VS Code

VS Code is an IDE to write and edit web app code. It is one of the most popular code for engineers and developers.

I installed VS Code to write and edit my app code. It also has handy extensions that let me directly connect to an EC2 instance so that I can read and edit code that will live inside the instance.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

A terminal is a place for me to send commands to my computer in the terminal, i.e. tell it what I want it to do. The first command I ran for this project is cd "C:\Users\kasem\Onedrive\Plocha\DevOps" which navigates the terminal to the DevOps folder.

I updated my private key's permissions by running these commands: icacls "nextwork-keypair.pem" /reset
icacls "nextwork-keypair.pem" /grant:r "kasem:R"
icacls "nextwork-keypair.pem" /inheritance:r. These commands give me access to connect to EC2.


![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_9328ada1)

---

## SSH connection to EC2 instance

To connect to my EC2 instance, I ran the command ssh -i  [path to private key] ec2-user@[ipv4 address of EC2 instance]. This command sets up an SSH connection directly between our local computer and the instance.

### This command required an IPv4 address

A server's IPv4 DNS is a public address that identifies where the server lives in the cloud. In my case, EC2 instance IPv4 DNS is useful information to give to my local computer. It tells the computer where we launch the EC2 computer.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_e3069dca)

---

## Maven & Java

Apache Maven is a tool that helps me with creating and organizing Java projects (like this web app). It comes with a lot of use cases, like being a package manager and the tool that uses archetypes (templates) for spinning up projects like web apps.

Maven is required in this project because I want to use its ability to spin web apps using archetypes. I am to set up my Java web app using the web app archetype.

Java is the programming language that I use to develop my web app. It's a very popular and versatile choice, as you can use it to develop all different types of apps, including web apps and enterprise systems.

Java is required in this project because it lays the foundation for writing my web app code. It is like needing to know a language in order to speak it. Maven also needs Java in order to work.

---

## Create the Application

I generated a Java web app using the command 'mvn archetype:generate'. This command tells Maven to generate a web app using an existing template. It also tells Maven to call the generated web app project 'nextwork-webapp-project'.

I installed Remote - SSH, which is an extension within VS Code. This extension lets me connect VS Code directly to a remote server, like an EC2 instance.

Configuration details required to set up a remote connection include the host (i.e. the EC2 instance's address), the identity file (i.e. the location of my private key) and the user (i.e. the user that I log into for my instance).

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_2939cf01)

---

## Create the Application

Using VS Code's file explorer, I could see folders and subfolders that define my web app. Folders can be expanded by clicking on all of the angled brackets >

These folders organize different parts of the web app; the resources subfolder stores connection details, while webapp subfolder stores files for the app's appearance. Src is the parent folder that contains all the source code for the web app. 

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

The index.jsp is the file in our web app that defines both HTML content (i.e. the static elements that go into our web app's page), as well as any code for generating dynamic content (i.e. content that's always changing)

I edited index.jsp by updating the HTML code to also say Hello Martin! I also added a paragraph i.e. some text that says, "This is my web app working!"

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

An alternative to using IDEs is within the terminal itself. To edit index.jsp, I ran "cd" commands to navigate my terminal to the right subfolder and then ran the "nano" command to use nano to open up and start editing the index.jsp file.

Compared to using an IDE, editing index.jsp in the terminal felt less intuitive as you have to use your keyboard to navigate your cursor. I would be more likely to use an IDE if I had lots of bits of code to update and delete, or copy and paste (i.e. lots of navigating within the file.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-vscode_a3324ad41)

---

---


<br>

<br>
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# 2 Connect a GitHub Repo with AWS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-github)

**Author:** Martin Kaše  
**Email:** kase.martin@hotmail.com

---

## Connect a GitHub Repo with AWS

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-github_dd9d254e)

---

## Introducing Today's Project!

I will set up a Git repository for my web app's code. By the end of this project, the code that I write for my Java web app will be stored securely in GitHub.

### Key tools and concepts

Services I used were GitHub, Amazon EC2 (development instance), key pairs and VS Code. Key concepts I learnt include setting up a Git repository, the difference between Git and Github, and the commands for staging, saving, and pushing changes to my code. I also learnt about upstream repositories, and setting a remote origin and branches.

### Project reflection

This project took me approximately 2 hours to do, including demo time. The most challenging part was to push changes into GitHub repository for the first time... It was most rewarding to set up a README that ties the entire repository together.

I did this project because I wanted to learn more about Git and GitHub so I can better understand my ongoing CI/CD project.

This project is part two of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

---

## Git and GitHub

Git is a version control system, which means it is used to track changes that I make to my code. It is also incredibly helpful, as for collaboration - with Git, you can see who made what change, and the handover from development to deployment is a lot smoother when everyone is looking at the same shared repository of code. I installed Git using the commands "sudo dnf update -y" and "sudo dnf install git -y".

GitHub is a platform that lets me store, share, and collaborate on my code. It is called GitHub because it uses Git as the tool for version control (one of its main features), but GitHub also adds much more that makes collaboration, seeing public repositories, and managing multiple repositories/projects much easier. I am using GitHub in this project to store my web app's code.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-github_efaadbf7)

---

## My local repository

A Git repository is like an online folder that you can use to store your web app's code and all the versions of that code. Think of it as a go-to place for all the code and updates and changes related to a specific project.

Git init is a command that initializes git in my local repository. I ran git init in my web app project folder, which tells my terminal that I want to start tracking changes locally.

After running git init, the response from the terminal was that I initialized Git, and by default I used the "main" branch. A branch in Git is like a version of your code—you make changes to your code over a branch and then merge those changes into the main branch when you are done + want to introduce that change in your code.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-github_7bf21bae)

---

## To push local changes to GitHub, I ran three commands

### git add

The first command I ran was "git add .", which adds our changes to a staging area. A staging area in Git is like the place to review all changes made to the code so you can decide what changes you would like to save in a commit.

### git commit

The second command I ran was "git commit", which is the command for saving the changes in our staging area. Using '-m' means leaving a message for that commit e.g.  "made changes to index.jsp".

### git push

The third command I ran was "git push -u origin master".  This command pushes code changes I saved to my remote origin. -u is a special  flag that makes my remote origin the default upstream repository. Next time I have changes I want to push, I simply run "git push" and Git already knows where to push those changes to.

---

## Authentication

When I commit changes to GitHub, Git asks for my credentials because it needs to authenticate me before letting me make code changes to the GitHub repository—it needs to do this to know that you have the right to change the code.

### Local Git identity

Git needs my name and email because it is a version control system, which means it is used for tracking who made what change to a piece of code. To really identify the people that made x changes, Git will need to know your name and email.

Running git log showed me that by default, Git is saving my code changes to a username called "EC2 Default User"  instead of my actual name details.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-github_9a27ee3b)

---

## GitHub tokens

GitHub authentication failed when I entered my password because password authentication support was already removed in 2021. There are too many security risks associated with entering a password over the terminal to GitHub, so more secure ways are now available.

A GitHub token is like a temporary password that grants access to your GitHub account. I'm using one in this project because it lets me safely authenticate to my GitHub repository while in my EC2 instance.

I could set up a GitHub token by visiting the Developer Settings in GitHub, and we set one up that expires in 7 days and only allows permissions to repositories.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-github_fa11169d)

---

## Making changes again

I wanted to see Git working in action, so I made another change to my index.jsp file. I couldn't see the changes in my GitHub repo initially because I had not added, committed, or pushed those changes.

I finally saw the changes in my GitHub repo after running the same three commands and then refreshing index.jsp in my GitHub repository.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-github_6becb2bc)

---

## Setting up a READMe file

As a finishing touch to my GitHub repository, I added a README file, which is a document that lives at the root of my repository and introduces my project and what it does, how to use it, etc. I added a README file by running "touch README.md" in my EC2 instance's terminal.

My README is written in Markdown because that is the common text language that lets me format in a document. Special characters can help you format text in Markdown, such as a backtick (`) for code, or double asterisks (**) for bolding.

My README file has 6 sections that outline a table of contents, introduction, technologies (i.e. AWS services), how to set up the repository locally, and then a section for contacting the author plus a thank you message.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-github_c94976902)

---

---

<br>
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# 3 Secure Packages with CodeArtifact

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codeartifact-updated)

**Author:** Martin Kaše  
**Email:** kase.martin@hotmail.com

---

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codeartifact-updated_1d79e699)

---

## Introducing Today's Project!

In this project, I will demonstrate how to set up CodeArtifact as our CI/CD pipeline's artifact repository. I'm doing this project to learn the importance and value of having an artifact repository. It is a huge time saver.

### Key tools and concepts

Services I used were CodeArtifact. IAM, Amazon EC2, GitHub and VS Code. Key concepts I learned include using artifact repositories, connecting Maven with CodeArtifact, setting up IAM permissions to give my EC2 instance the permission to access CodeArtifact.

### Project reflection

This project took me approximately 2.5 hours, including demo, secret mission, Q&A, and troubleshooting time. The most challenging part was finding a typo when downloading file from my custom repository which caused an error. It was most rewarding to see all working at the end especially the CLI commands in CloudShell in AWS.

This project is part three of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project the next day.

---

## CodeArtifact Repository

CodeArtifact is an artifact repository service, which means I can use it to create repositories to store my web app's packages and dependencies. Engineering teams use artifact repositories for security, control, and reliability.

A domain is like a folder that holds together multiple repositories under the same project or under the same organization. They are helpful for setting up permission settings for multiple CodeArtifact repositories in one go. My domain is called nextwork.

A CodeArtifact repository can have an upstream repository, which means a public source of packages that Maven can visit if they can't find it in our local CodeArtifact repository. My repository's upstream repository is Maven Central Repository, which is the largest Java repository (and is extremely helpful when building a Java web app).

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codeartifact-updated_n4o5p6q7)

---

## CodeArtifact Security

### Issue

To access CodeArtifact, I need an authorization token that allows our EC2 instance to access CodeArtifact repository for 12 hours. I ran into an error when retrieving a token because my EC2 instance does not have the permissions to access my AWS resources by default. This follows the principle of least priviledge.

### Resolution

To resolve the error with my security token, I set up an IAM Policy that grants access to CodeArtifact and then an IAM role that I can attach to my EC2 instance. This resolved the error because my EC2 instance now has access to request an authorization token from my repository.

It's security best practice to use IAM roles because IAM roles are more secure and scalable than hardcoded credentials.Hardcoded credentials are much more vulnerable to security attacks and getting misused (resulting in errors, losses, delays). IAM roles are applied via AWS and do not require and hardcoding credentials which is much more secure and encrypted. IAM roles are also the better option if you want to give the same set of permissions for multiple instances.

---

## The JSON policy attached to my role

The JSON policy I set up grants access to CodeArtifact. Specifically, it grants access to three key actions related to CodeArtifact—retrieving an authorization token, finding the repository (endpoint), viewing the packages inside the repository.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codeartifact-updated_23rp7q8r9)

---

## Maven and CodeArtifact

### To test the connection between Maven and CodeArtifact, I compiled my web app using settings.xml

The settings.xml file configures Maven to use my CodeArtifact repository. It supplies Maven with the name and authentication token to get access to the CodeArtifact repository, and also sets up a profile section in case I ever have multiple repositories and I need to tell Maven when to use which one.

Compiling means the process of translating my web app source into something that machines can run. Maven is my compiler, so I asked Maven to compile my web app code. While it is compiling, maven will need to put together all of the packages that my web app needs in order to run. To retrieve these packages, Maven visits CodeArtifact (which will say it does not have any packages available), then Maven would go upstream to request the exact same packages from the upstream repository (Maven Central), and once Maven has those packages, it stores local copies in the CodeArtifact repository.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codeartifact-updated_c17eace8)

---

## Verify Connection

After compiling, I checked my CodeArtifact repository and I noticed 4 pages of packages inside. This tells that I have successfully stored our web app's dependencies in an artifact repository.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codeartifact-updated_1d79e699)

---

## Uploading My Own Packages

In a project extension, I also decided to become a package publisher—which means publishing my own packages into my CodeArtifact repository. This is useful in situations where you might have internal team members developing their own packages—and wanting their fellow teammates to have access to it (without giving the entire world access).

To create my own package, I set up a text file and used tar to package up that text file. I also generated a security hash because that will give CodeArtifact a way to figure out whether or not the package has been tampered with in transit. If it has been tampered with, security hash that CodeArtifact generates does not match up to the security has I generate.

To publish the package, I ran a CLI command that let me upload the package I created (in CloudShell) to my repository. When I look at the package details in CodeArtifact, I can see the version number, publish date, and even the origin (in this case, the CodeArtifact repo itself is the origin).

To validate my packages, I then tried to download my package back into the CloudShell terminal. I saw a package successfully downloaded/installed from CodeArtifact, and then I "unzipped" the package and read what was inside. I could see the text that I wrote inside the text file before I packaged it up. This proves that CodeArtifact successfully stored my own custom packages that I can retrieve later as well.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codeartifact-updated_sm12-upload)

---

---

<br>

<br>

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# 4 Continuous Integration with CodeBuild

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codebuild-updated)

**Author:** Martin Kaše  
**Email:** kase.martin@hotmail.com

---

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codebuild-updated_35588a47)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use AWS CodeBuild to automate the build process in the CI/CD pipeline. Building means compressing my web app's files into a single compressed file (like a zip file) that we can later deploy. This project is just going to focus on CodeBuild and creating that compressed file automatically. Deploying it comes in the next project.

### Key tools and concepts

Services we used include CodeBuild, COdeConnection, CodeArtifact, S3, EC2, GitHub, and VS Code, Key concepts I learnt include the build process, resolving Git issues in terminal, buildspec.yml, and using CodeConnections to connect AWS with GitHub.

### Project reflection

This project took me approximately 3 hours to do including troubleshooting time. The most challenging part was resolving the error I ran into while setting up builspec.yml file but I figured that out. It was most rewarding to see the buil succeed in the end.

This project is part four of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

---

## Setting up a CodeBuild Project

CodeBuild is a continuous integration (CI) service, which means it helps me to compile and package code (i.e. turn my web app code into something computers can run, and then compress it all into a neat little package). Engineering teams use it because CI services automate this process for us - if CI does not exist, engineers would have to manually compile and package code themselves before they deploy it.

My CodeBuild project's source configuration means where the code lives and I selected GitHub. That is my web app's source code repository.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codebuild-updated_fewgrhte)

---

## Connecting CodeBuild with GitHub

There are multiple credential types for GitHub, like GitHub App, personal access tokens and OAuth App. I used GitHub App because it is the most simple and secure way to set up a connection between GitHub and AWS - AWS handles all of the  credentials (e.g. the tokens) in the background for me. I need to log in once to Github using a special AWS managed GItHub App.

The service that helped connect my AWS environment with GitHub is AWS CodeConnection. CodeConnection also let me connect my environment with other third-party platforms; in this case, it makes sure that I have secure connection to GitHub, so that my CodeBuild project can use my GitHub repository as the source with the correct permissions.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codebuild-updated_a7c98e2d)

---

## CodeBuild Configurations

### Environment

My CodeBuild project's Environment configuration means the environment set up for the compute power (i.e. the EC2 instance) that will be compiling and compressing the files when I run my CodeBuilder project. it includes settings like provisioning model, compute, operation system, image and service role. These settings determine how a new EC2 instance will be spun up and conduct the build process. It is important here that the EC2 instance has the correct permissions to everything it needs to work properly.

### Artifacts

Build artifacts are files/resources that get created as a part of the CodeBuild process. They are important because they represent artifacts that need be used later on in the CI/CD pipeline - for example, my build process will create a compressed file that represents my web app. I will need to use that compressed file to deploy the web app later on. To store my build artifacts, I created a S3 bucket

### Packaging

When setting up CodeBuild, I also chose to package artifacts into a Zip file—this helps with package management as files are organized neatly in a single executable file. It also helps to compress the size of my compiled web app.

### Monitoring

For monitoring, I enabled CloudWatch Logs, which is a service that will note down commands that are run and any errors that happen. This is extremely helpful for troubleshooting.

---

## buildspec.yml

My first build failed because I was missing buildspec.yml in my root folder of my web app repository. A buildspec.yml file is needed because it is like a detailed instruction manual for CodeBuild. Placed in the root of your repository, it tells CodeBuild exactly what to do at each stage of the build process—what tools to install, what commands to run, and what files to package up when it's done. CodeBuild automatically looks for a file named buildspec.yml in the root directory of your source code. If it finds one, it uses it to execute the build.

The first two phases in my buildspec.yml file installs Java and gets me access to CodeArtifact. The third phase in my buildspec.yml file compiles the web app The fourth phase in my buildspec.yml file packages the web app into a single, compressed artifact.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codebuild-updated_35588a47)

---

## Success!

My second build also failed, but with a different error that said PREBUILD PHASE failed. To fix this, I went straight to VS Code and check lines of code in buildspec.yml file where I found out that I had a typo in AWS account number format.

To resolve the second error, I attached a policy for accessing CodeArtifact to my CodeBuild role. When I built my project again, I saw a success. With the privilige to CodeArtifact granted by the role, CodeBuild now has access to the repository.

To verify the build, I checked my artifacts bucket in S3. Seeing the build artifact tells me that CodeBuild was a success. The build process compiled the code from the source repository [GitHub], compressed it into a file and stored that file in my S3 bucket.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codebuild-updated_d9cc6191)

---

## Automating Testing

In a project extension, I added a test script that checks whether there is an src folder and an index.jsp file in my project directory or not.

To add the test script to the build process, I updated everything from the build stage in buildspec.yml file to include run-tests.sh commands.

After pushing my code to GitHub, I checked the the buildspec.yml file for the changes. Once checked, I switch to CodeBuild in AWS Cloud to start build again. I looked for lines saying "./run-tests.sh".

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codebuild-updated_sm-test-script-upload)

---

---


<br>

<br>

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# 5 Deploy a Web App with CodeDeploy

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codedeploy-updated)

**Author:** Martin Kaše  
**Email:** kase.martin@hotmail.com

---

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codedeploy-updated_val-27)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use CodeDeploy to deploy a web app. I am doing this project to learn about how deployment works, and how it can be automated using a combination of CodeDeploy and deployment scripts. By the end of this project, I wil see a live website.

### Key tools and concepts

Services I used were CodeDeploy, CodeBuild, CodeArtifact, IAM, Cloudformation, EC2, S3, CodeConnection, VS Code and Github. Key concepts I learnt include deployment, deployment groups, deployment scripts, appspec.yml, and the importance of rebuilding my project before deploy.

### Project reflection

This project took me approximately 3 hours including troubleshoting and demo time. The most challenging part was understanding the separation of the deployment instance from the development instance - all these deployment commands are run there. It was most rewarding to see the deployed web app.

This project is part five of a series of DevOps projects where I'm building a CI/CD pipeline. I'll be working on the next project tomorrow.

---

## Deployment Environment

To set up for CodeDeploy, I launched an EC2 instance and VPC because they will make up our production environment. I need to separate my development environment (where I am writing the code) with the production environment (where I am deploying the web app) so that the code I am writing as developers do not get shown to users until I am ready to push them into production.

Instead of launching these resources manually, I used CloudFormation. When I need to delete these resources created by my CloudFormation template, I can simply delete the Cloud Formation stack. This will automatically delete all the resources that are inside that stack

Other resources created in this template include networking resources like VPCs, internet gateways, route tables and subnets. They're also in the template because  a production environment has specific requirements around traffic that it should enable and block out. Setting up all of the networking resources that will help the deployment work is common practice.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codedeploy-updated_val-5)

---

## Deployment Scripts

Scripts are mini programs that helps me automate the running of commands. To set up CodeDeploy, I also wrote scripts to autoamte deployment commands (i.e. these are the commands that my deployment EC2 instance needs to run in order to host my web app).

The 'install_dependencies will help my EC2 instance install all the dependencies it needs to host a web app, like Tomcat (a web server).

The start_server.sh is another script that is all about starting up two servers that I am using in my EC2 instance - one, it starts Tomcat (responsible for running my Java app); and two, it starts Apache (the web server responsible for handling web traffic and passing requests to Tomcat).

The stop_server.sh is a script that stops our Apache and Tomcat servers when they are no longer needed to serve the web app to a user.

---

## appspec.yml

Then, I wrote an appspec.yml file to give CodeDeploy the instructions for deploying my web app. The key sections in appspec.yml are BeforeInstall (i.e. use the install_dependencies.sh script to install dependencies like Tomcat), ApplicationStart (i.e. use the start_server.sh script), and ApplicationStop (i.e. use the stop_server.sh script).

I also updated buildspec.yml to tell CodeBuild that it should also package up the new appspec.yml and set up scripts that I created inside teh build artifact (i.e. the compressed war file).

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codedeploy-updated_val-12)

---

## Setting Up CodeDeploy

A deployment group is a group of EC2 instances that you can deploy to, and also the collection of settings that determine how you want to deploy your web app. A CodeDeploy application is simply a folder that holds together all the deployment groups for the same app.

To set up a deployment group, you also need to create an IAM role to give CodeDeploy the permission to access the EC2 instances that it needs to coordinate. Otherwise, CodeDeploy does not have access to EC2 = not being able to give your deployment instances the instructions for deploying the web app.

Tags are helpful for identifying the instaces that will be deploying the web app. I used the tag "role:webserver" to automatically match the EC2 instance I deployed with my CloudFormation template. Now in the future, when we have other EC2 instances, we want to also be in this deployment group. We can simply tag that new instance with the same "role:webserver" tag. They will automatically get added to the same deployment group .

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codedeploy-updated_val-18)

---

## Deployment configurations

Another key settings is the deployment configuration, which affects how quickly and risky we are deploying the web app. I used CodeDeployDefault.AllAtOnce, so any changes that CodeDeploy deploys affects all the instances in the deployment group at once. This is the fastest way to deploy a change/code update.

In order to connect the deployment instance with CodeDeploy, CodeDeploy Agent is also set up to receive instructions from CodeDeploy, and make sure that the commands in appspec.yml are run.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codedeploy-updated_val-20)

---

## Success!

A CodeDeploy deployment is a specific update to my application that I am deploying to my users. The difference between the CodeDeploy deployment and a deployment group is that a deployment group is like a settings file, and the deployment itself like a specific update I roll out using the that settings file.

I had to configure a revision location, which means where my web app's war file (i.e. the compressed file ready to be deployed) lives. My revision location was is the S3 bucket that I have created and linked with CodeBuild i.e. build artifacts automatically go into that bucket.

To check that the deployment was a success, I visited the Public DNS address of my deployment EC2 instance.  I saw a live web app that is working and serving my web app code to end users.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codedeploy-updated_val-27)

---

## Disaster Recovery

In a project extension, I decided to set up a broken deployment in order to learn troubleshoot it. The intentional error I created was a typo "systemctll" in the script "stop_server.sh". This will cause the deployment to fail because it could not find the proper command (See scripts/stop_server.sh run as user root failed with exit code 1 ).

I also enabled rollbacks with this deployment, which means that settings from the last deployment will be applied if the new deployment settings fails. If the previous deployment selected for recovery also contains an error, rollbacks won't help and it fails.

When my deployment failed, the automatic rollback took the lead because it was set up. To actually recover from S3 bucket that updated itself from github repository to the latest version I'd have to go to the VS Code production environment and pushed fixed version of stop_server.sh to my github repository.

![Image](http://learn.nextwork.org/appreciative_blue_adorable_medlar/uploads/aws-devops-codedeploy-updated_rollback-validation-upload)

---

---


<br>

<br>

## Contact
If you have any questions or comments about the NextWork Web Project, please contact:
Martin - [kase.martin@hotmail.com](mailto:kase.martin@hotmail.com)
[LinkedIn]
- (www.linkedin.com/in/martin-kaše-220a8b112)

<br>

## Conclusion
Thank you for exploring this project! I'll continue to build this pipeline and apply my learnings to future projects.

A big shoutout to **[NextWork](https://learn.nextwork.org/app)** for their project guide and support. [You can get started with this DevOps series project too by clicking here.](https://learn.nextwork.org/projects/aws-devops-vscode?track=high)

