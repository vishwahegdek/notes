# Git 

## Most Useful for me

To view your remote repository settings:

```bash
git remote -v
```

To add a remote for the repo
```bash
git remote add origin <your-new-repo-URL>
```

To explicitly set the upstream branch for your current branch:
```bash
git push --set-upstream origin master
git branch --set-upstream-to=origin/master
```

To untrack files:
```bash
git rm -r --cached <file>
```

To move or remane files:
```bash
git mv old/path/file.txt new/path/file.txt
```


To set your default push configuration:

```bash
git config --global push.default simple
```

This configuration ensures that Git pushes to the upstream branch with the same name as your local branch. When you're on the master branch, it will push to origin/master.


## Advanced Configuration

For more specific push behavior, you can use:

```bash
git config --global push.default matching
git remote set-url --push origin https://github.com/your-username/your-repo.git
```

The `matching` option pushes all branches with matching names on both ends.

## Push Behavior Options

Git offers several push.default behaviors:

- **simple**: Push the current branch to its upstream branch (recommended)
- **current**: Push the current branch to a branch of the same name
- **matching**: Push all branches having the same name on both ends
- **upstream**: Push the current branch to its upstream branch
- **nothing**: Do not push anything unless a refspec is explicitly given

## Verifying Your Configuration

To check your current Git push configuration:

```bash
git config --get push.default
```

To view your remote repository settings:

```bash
git remote -v
```

This will display the fetch and push URLs for each remote repository.
