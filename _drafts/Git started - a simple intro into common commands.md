There are a thousand (or more) git tutorials out there. Here's my what—what's most useful to me and trying to make it simple to understand.

I've created a sample repo, so all these commands should work if [fork my GitStarted](https://github.com/Fammy/GitStarted) repository on GitHub.

I'm not an expert so this won't be a complete list of all the things you need to do. So, here are the git commands that I regularly use on the command line.


## git clone
In fairness, I don't use this one a lot, but it's hard to get started without it.

Git clone will create a local copy of a remote git repository. It's hard to work locally without a copy of your code. 😁

First, go to your `projects` or `code` directory on your local machine. If you want the repo to live in `~/code/GitStated`, go to the `/code` folder. When you clone, it'll create the folder name based on the repo name, GitStarted.

(You can specify other options, such as target directory, but I'm trying to keep it simple)

Now, let's clone.

Via HTTPS
```git clone https://github.com/YourUserName/GitStarted.git```

Via SSH
```git clone git@github.com:YourUserName/GitStarted.git```

Yay, you've got a copy of a repository. Let's `cd` into the directory and keep going.

## git status

Let's make a change. Open README.md in your text editor of choice and add some text, save and exit. Now let's see what's changed by running a command.

```git status```

The output tells us we have one modified file, README.md. That's good, because that's the file we just edited.

When you add a file

## git add

## git commit

## git pull

## git push

## git checkout

## git checkout -b

## git merge

## Commands that didn't quite make the cut

### git init

### git branch

## Need more help?

The git website