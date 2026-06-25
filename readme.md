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

