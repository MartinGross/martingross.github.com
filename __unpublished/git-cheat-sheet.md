# git Cheat Sheet

## Important things to understand
_What is git HEAD, exactly?_
HEAD is the tip of the current branch. You can see what HEAD points to looking into the file .git/HEAD . It is context dependent on which BRANCH you are on.

_What is master?_
master is the default git branch. Similar to trunk in Subversion.

## git Tips & Tricks
making git “forget” about a file that was tracked but is now “.gitignored”

.gitignore will prevent untracked files from being added (without an add -f) to the set of files tracked by git, however git will continue to track any files that are already being tracked.

To stop tracking a file you need to remove it from the index. This can be achieved with this command.

	git rm --cached <file>

The removal of the file from the head revision will happen on the next commit.

OR in short

Removing a file from Git source control but not from the source
	git rm --cached <file>


## git and subversion (a.k.a. svn)
Clone from svn unter Windows:
	git svn clone -s "svn://myidtravel-test01.cns.fra.dlh.de/myidtravel-projects/myidtravel-operation" --username martin.gross

View all branches (including svn branches)
	git branch -a

Switch back to trunk:
	git checkout master

Show branches and which branch you’re on:
	git branch

Switch to branch:
	git checkout axis2_v_1_3_local

Save local modified changes
	git stash

Show diff of stash to working copy:
	git stash show -p

Show diff of stash to working copy as stats:
	git stash show

Restore changes from the most recent stash to working tree
	git stash pop

View log in SVN format:
	git svn log

Show status of files
	git status

Updates working tree to the latest changes of the branch you are currently working on:
	git svn rebase

Commit changes to SVN:
	git svn dcommit

Fetch unfetched revisions from the Subversion remote we are tracking:
	git svn fetch

Create branch in svn repository:
	git svn branch -m "Branch for axis2 v1.3" axis2_v1_3

Create local branch from remote svn branch
	git checkout --track -b axis2_v1_3 remotes/axis2_v1_3

More:
http://www.viget.com/extend/effectively-using-git-with-subversion/

Return the entire working tree to the last committed state:
	git reset --hard HEAD

## Creating a remote repository for git

Set up the new bare repo on the file server:

	mkdir u:\gitRepos\myapp.git 
	cd u:\gitRepos\myapp.git
	git --bare init

Add the remote repository to your existing local git repo and push:

	cd c:\myapp
	git remote add origin u:\gitRepos\myapp.git
	git push origin master

Importing a Git tree into a Subversion repository
	git svn init -s svn://myidtravel-test01.cns.fra.dlh.de/myidtravel-projects/myidtravel-ws-mock

	git svn fetch

git show-ref trunk
6b9d8379e7138fcbc68d2ed01f8b5f3e96bc3045 refs/remotes/trunk

git log --pretty=oneline master | tail -n1
2bd5cb3aa02a40ee5c6324af253ac9fde71fd813 initial

echo 2bd5cb3aa02a40ee5c6324af253ac9fde71fd813 6b9d8379e7138fcbc68d2ed01f8b5f3e96bc3045 >> .git\info\grafts

git svn dcommit

More at: http://eikke.com/importing-a-git-tree-into-a-subversion-repository/

## git log
show all commits of file in all branches
	git log --all path/to/file

Show diff of last commit:
	git show

## gitk Commit Browser
Show all branches in commit browser
	gitk --all &

## How to fix git-svn if the svn repo moves
From http://ciaran-lee.com/2008/06/13/how-to-fix-git-svn-if-the-svn-repo-moves.html :

I’m using git-svn at the moment, as the owner of a project I’m working on is using subversion. The svn server has just moved to a new domain name. Unfortunately this broke git-svn as I couldn’t rebase (got an error like this: 
“RA layer request failed: PROPFIND request failed on ‘/svn’: PROPFIND of ‘/svn’: 200 OK (http://$OLD_DNS_NAME) at /usr/local/bin/git-svn line 1839” )

Just editing .git/config and changing the url for the svn repo doesn’t work as rebasing will produce the following error: Unable to determine upstream SVN information from working tree history.

The solution to this problem is as follows:

edit the svn-remote url URL in .git/config to point to the new domain name
run git svn fetch
change svn-remote url back to the original url
run git svn rebase -l to do a local rebase (with the changes that came in with the last fetch operation)
change svn-remote url back to the new url
git svn rebase should now work again!