junk1
junk2

- [Git Module 1 Extra exercises](#git-module-1-extra-exercises)
  - [Command line exercise](#command-line-exercise)
  - [IDE exercise (PyCharm)](#ide-exercise-pycharm)
  - [IDE exercise (IntelliJ)](#ide-exercise-intellij)
- [How to add SSH key to the BitBucket](#how-to-add-ssh-key-to-the-bitbucket)
- [How to make remote repository after you create a local Git project](#how-to-make-remote-repository-after-you-create-a-local-git-project)

## Git Module 1 Extra exercises

Please do the following exercises in addition to the one from the class material

### Command line exercise

- Create a new project directory called my-project
- Add myfile1.txt, myfile2.txt using commands below
  - echo "I am file1" > myfile1.txt
  - echo "I am file2" > myfile2.txt
- Make "my-project" git enabled
- Make 2 changes (I will call it change1 and change2) to myfile1.txt and commit each change
- Revert change2
- Make change to both myfile1.txt and myfile2.txt
- Commit the change

### IDE exercise (PyCharm)

- Create a new Pycharm project
- Make it a Git project
- Make changes and commit changes using IDE's Git support

### IDE exercise (IntelliJ)

- Create a new Maven project
- Make it a Git project
- Make changes and commit changes using IDE's Git support

## How to add SSH key to the BitBucket

Instructor will demonstrate this.

- In a terminal, do "ssh-keygen" and accept all defaults

```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/Administrator/.ssh/id_rsa
Your public key has been saved in /c/Users/Administrator/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:01SVx04wyMxOmcFSUKIEG5ccfwMOiHHN5fwpLfiWO5Q Administrator@EC2AMAZ-8RI616P
The key's randomart image is:
+---[RSA 3072]----+
|    .o+*=+=O=*++ |
|    ...==B.+X ..+|
|      . . *+o  + |
|         + +.o  .|
|        S +.+    |
|         oE+     |
|         .+      |
|         ...     |
|          ..     |
+----[SHA256]-----+
```

- Verify that relevant files are generated

```
$ ll  ~/.ssh
total 10
-rw-r--r-- 1 Administrator 197121 2622 Jul 22 13:41 id_rsa
-rw-r--r-- 1 Administrator 197121  583 Jul 22 13:41 id_rsa.pub
-rw-r--r-- 1 Administrator 197121  837 Jul 19 17:26 known_hosts
-rw-r--r-- 1 Administrator 197121   95 Jul 19 17:26 known_hosts.old
```

- Copy the content of "id_rsa.pub" file by "cat ~/.ssh/id_rsa.pub"
- Now go to your BitBucket website, click Settints button in the top-right corner
- Select Workspace settings or Personal Bitbucket settings
- Select SSH Keys
- Click Add Key button
- Enter description of this key to the Label: i.e. my VM ssh key
- Paste the content of "id_rsa.pub" file to the Key area
- Click Add key at the right bottom corner

- Now you should be able to use ssh for cloning and pushing

## How to make remote repository after you create a local Git project

Let's assume you have a local Git project called "my_project", now you want to make a corresponding remote BitBucket project.

- Create a remote repository called "my_project" (technically they don't have to have a same project name even though having a same project name is a good convention to follow)
- Make sure to use the same default branch you are using in local repository
  - It is either "master" or "main"
- Remember the URL of the remote project 
- In your local repository, do the following

```
cd <project-root>
git remote add origin <url-of-the-remote-repository>
git push -u origin main (assuming if your default branch is main)
```
