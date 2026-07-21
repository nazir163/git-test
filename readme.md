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

-----------------------------------

git blame filename (commits responsible for changes for all lines in code)

git blame filename -L 1,10 (commits responsible for changes on lines 1 to 10)


To view output for a range of lines

git blame -L start-line,end-line <file-name>

as sample output command will be see this 

git blame -L 2,5 CONTRIBUTING.md

Run:

git blame user-service.ts

Get commit:

f4d5e6a

Then:

git show f4d5e6a

Maybe the commit message says:

Fix issue #542 for legacy customers

first blame and sepcify fiel name after show command run with specfic commit 

Rule of thumb

Use:

git blame

when you ask:

"Who changed this line and why?"

Use:

git bisect

when you ask:

"Which commit introduced this bug?"

# Show blame with email addresses
git blame -e config.txt

# Show blame ignoring whitespace changes
git blame -w config.txt

# Show blame for specific line range (lines 2-4)
git blame -L 2,4 config.txt

# Show blame with timestamps
git blame --date=short config.txt

# Show blame at a specific point in time
git blame --before="2024-01-16" config.txt
----------------------------
Git Bisect 

Real-world scenario

Suppose:

Monday: app works
Friday: app broken

Between Monday and Friday:

150 commits

Instead of checking 150 commits manually, Git may find the culprit in about:

7-8 tests


because binary search reduces the search space dramatically


Git Tags 

Check all tags
git tag

Output

v1.0.0

See where the tag points
git show v1.0.0

Output

commit 6fd83...

Author:
Date:

Added login

Git shows the commit associated with the tag.

Delete tag

Local

git tag -d v1.0

Remote

git push origin --delete v1.0

Creating a tag locally

git tag v1.0.0

does not automatically send it to GitHub.

Push one tag

git push origin v1.0.0


Types of Tags

There are two kinds.

1. Lightweight Tag

Just a pointer.

git tag v1.0.0

No extra information.

Think of it like

Bookmark
2. Annotated Tag (Recommended)

Contains metadata.

git tag -a v1.0.0 -m "First production release"

Stores

tag name
creator
date
message

View it

git show v1.0.0

You'll see something like

Tag: v1.0.0

Message:

First production release


How npm Uses Tags

When library maintainers publish a package version like:

npm publish

the source code usually corresponds to a Git tag such as:

v5.1.0

At which point create  a Tag 
Only when you want to mark a release/version.

Example timeline as 
1.initial project 
2.feature/login
3. signup 
4. profile
or first production relaeas 

Who decides the version number?

Usually the team follows Semantic Versioning (SemVer):

v1.0.0
Major (1.x.x) → Breaking changes.
Minor (x.1.x) → New features that don't break existing users.
Patch (x.x.1) → Bug fixes only.


A tag only points to one commit.

For example:

A ---- B ---- C ---- D
                    ▲
                 v1.0.0

The tag only says:

"Version 1.0.0 is commit D."


What happens when production has a bug?

Suppose production is running

v1.1.0

Users report:

"Payment isn't working."

Now you know:

Production is running v1.1.0
The bug exists in v1.1.0
It did not exist in v1.0.0

So you compare the two versions.

git diff v1.0.0 v1.1.0

This shows everything that changed between those releases.

Or you can view the commits:

git log v1.0.0..v1.1.0 --oneline

Example output:

a52f34 Added payment

d28f98 Fixed login

bc8921 Dashboard

Now you know which commits (and therefore which merged PRs) were introduced in the new release.

So the investigation is usually:

Production Bug

↓

Which version is running?

↓

v1.1.0

↓

Compare v1.0.0 → v1.1.0

↓

Find suspicious commit

↓

Fix it

↓

Release v1.1.1

This is one of the biggest reasons tags are valuable.

Why tags are so useful

Imagine there are 500 commits.

Without tags:

Which commit is production?

I don't know.

With tags:

Production = v1.3.0

Very easy.

-----------------

git fetch safely downloads the latest commits and updates my remote-tracking branches without changing my current working branch.

git pull performs a fetch and then immediately integrates those changes into my current branch, which may trigger merge conflicts right away."





