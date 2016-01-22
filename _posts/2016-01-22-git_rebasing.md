---
layout: post
title: Git Rebasing Tips 
---

Almost everything can be saved by git, and while a recent rebasing fiasco is fresh in my head, here are some of the steps I recently took in order to 'save' a pull request.  These are mostly gleaned from stackoverflow pages and google searches, and this is generally what ended up working but there is no guarantee that this is the best possible practice as this is completely learning from experience/the internet.

### Listing what went wrong

The easiest way to see where things might have went wrong is to use

    git log
     
which will list all of the commits made to the branch as:

```
  commit 14d1d859d47502c63c897f60b156862797599f52
  Author: Steven Crawford <crawfordsm@gmail.com>
  Date:   Fri Jan 22 11:36:13 2016 +0200
  
  adding re-identify
  
  commit c2dddcfeb7b24ce31af63a474bd8ce20a88c7f1f
  Author: Steve Crawford <crawfordsm>
  Date:   Tue Jan 19 14:16:19 2016 +0200

  updated version.py
```

The important bit is the hash for teh commit (the long line after the word commit above -- although you typically only need the first 7 letters to identify it).   Although I also liked this [version](https://feeding.cloud.geek.nz/posts/cherry-picking-range-of-git-commits/) which produces a bit of a pretty output
   
    git log --oneline --decorate --graph
     

Also if you want to see what is currently added or not, the following is fairly helpful as well:

    git status

### Removing one commit

A single commit can be easily reverted by using

    git revert <hash number>
    
This does create an entry in the log indicating the reversion.  Also, this may introduce conflicts if you try to revert an early commit when a later commit also changes that file.  The later commit has to be removed before that early commit.

### Rebasing the commit

Alternavitvely, multiple commits can be removed by using rebase.    To be honest, I have found almost every (description of rebasing)[https://git-scm.com/book/en/v2/Git-Branching-Rebasing] confusing.   It's just not how my brain works and will require a lot of re-programming to figure it out.   So this is basically what I have figured out so far and once again, may not be the right way to do it at all.  I stil don't understand it, but I feel like I have made a little progress. 

You can rebase things interactively by using:

    git rebase -i HEAD~5
   
This will allow you to interactively (the `-i` option) choose how to handle the last 5 commits on your current branch (`HEAD~5`).  You can delete a commit, but if so, make sure you delete all the commits after that one that effect the same files because otherwise you may have conflicts to deal with.    You can also squash a commit, which hides the commit in the previous commit and cleans up the commit log.    It is also possible to edit a commit message to update it appropriately. 


### Example

Let's ssay that you have a pull request with three files.   Unfortunately, you have not pulled from the master branch for quite some time and someone has changed something in file2.   You also have five comits with two of the commits dealing with file2.   

I have a feeling this is one of those cases where there are several ways to deal with this.  In the past, I would have just created a new branch, pulled from the upstream master, and then copied over my changes to the new branch.  Sufficient to get the job done, but highly inelegant.  

The next option is to remove your commits that have caused this conflict.   For example, you can run:

    git rebase -i HEAD~5
    
Then, delete the two commits that have differences with the master.   The master can be merged with the current branch without any conflicts with:
   
    git pull upstream master
    
And then the changes can be added back into the correct files and commited.  Any additional commits due to merging can be squashed or cleaned up with another rebase.

But now, that I think I know more than I probably do, I think I would suggest flipping those two steps.   Pull from the master and there will be conflicts to be merged.   Edit the appropriate files, commit them, and finalize the merge.  Then do a rebase to clean up the previous commits and any problems.  Of course, I'll have to wait until the next time I have screwed up a pull request to see if that does work better for me.     

Then again, I probably should start a swear jar just for pull requests I have managed to screw up. 




    
