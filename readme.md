1.first init 
2. first add . or only for specific file will be added right 
3. git commit 

mv   -> normal move
mv -f -> force move

git branch -m -> normal rename
git branch -M -> force rename

-M (force rename)
git branch -M main


Git will overwrite the existing main branch name.

Example:

Before:

main
feature-auth   ← current branch

Run:

git branch -M main

Now the old main branch reference is replaced, and your current branch becomes main.

The -u option means --set-upstream.

git push -u origin main

Git remembers:

main  <----tracks---->  origin/main

Now you can simply use:

git push

and

git pull

because Git already knows which remote branch to use.

-u Creates a tracking relationship between:

Local branch: main
Remote branch: origin/main


after that future push or pull simple make 
git push 
git pull 

but make sure that does not have multiple upstrem will be set right 

check origin 
git remote -v


git branch -vv

Does git branch -vv show upstream for all branches?

Yes.

git branch -vv

shows:

All local branches
Their last commit
Their upstream (if configured)

Example:

* dev          abc123 [origin/dev]
  feature-auth def456 [origin/feature-auth: ahead 2]
  test         ghi789


  ------------------

  Why use git fetch --all?  all remote tarck branching 

git fetch --all fetches updates from all remotes.

Suppose you have:

origin
upstream

If you run:

git fetch origin

Only origin is updated.

If you run:

git fetch --all

Git updates:

origin/*
upstream/*

all remote-tracking branches.

