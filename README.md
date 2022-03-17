### Git basics - commit - merge - push - pull - checkout -switch -amend - rebase
```
[root@ip-172-31-5-172 mydir]# git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.yml

no changes added to commit (use "git add" and/or "git commit -a")
[root@ip-172-31-5-172 mydir]# git add .
[root@ip-172-31-5-172 mydir]# git commit -m "atop installation"
[master cb4b75d] atop installation
 1 file changed, 5 insertions(+)
[root@ip-172-31-5-172 mydir]# git log
commit cb4b75d1402427ab623a85d1ca041737baf39e36 (HEAD -> master)
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
[root@ip-172-31-5-172 mydir]# git remote add origin git@github.com:jomyg/git-repo-test.git
[root@ip-172-31-5-172 mydir]# git remote
origin
[root@ip-172-31-5-172 mydir]# git remote -v
origin  git@github.com:jomyg/git-repo-test.git (fetch)
origin  git@github.com:jomyg/git-repo-test.git (push)

================================================================================================================================
>> We have pushed the contents to github
[root@ip-172-31-5-172 mydir]# git push origin master
The authenticity of host 'github.com (13.234.210.38)' can't be established.
ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
ECDSA key fingerprint is MD5:7b:99:81:1e:4c:91:a5:0d:5a:2e:2e:80:13:3f:24:ca.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,13.234.210.38' (ECDSA) to the list of known hosts.
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 625 bytes | 625.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To github.com:jomyg/git-repo-test.git
 * [new branch]      master -> master
[root@ip-172-31-5-172 mydir]# git log
commit cb4b75d1402427ab623a85d1ca041737baf39e36 (HEAD -> master, origin/master)
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
    
    
[root@ip-172-31-5-172 mydir]# git log --oneline
cb4b75d (HEAD -> master, origin/master) atop installation
2e29323  Apache installation task 1
===========================================================================================================================

[root@ip-172-31-5-172 mydir]# git log
commit cb4b75d1402427ab623a85d1ca041737baf39e36 (HEAD -> master, origin/master)    >>> Now its pointing to github master too and one is local branch
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
    
    
    
Now i have added some chnages to main.yml localy and commit

[root@ip-172-31-5-172 mydir]# >main.yml
[root@ip-172-31-5-172 mydir]# nano main.yml
[root@ip-172-31-5-172 mydir]# git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.yml

no changes added to commit (use "git add" and/or "git commit -a")
[root@ip-172-31-5-172 mydir]# git add .
[root@ip-172-31-5-172 mydir]# git commit -m "docker added"
[master 8831c9f] docker added
 1 file changed, 12 insertions(+), 8 deletions(-)
[root@ip-172-31-5-172 mydir]# git log
commit 8831c9fee4badf1c424aee18393d15115845bfc8 (HEAD -> master)
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:25:04 2022 +0000

    docker added

commit cb4b75d1402427ab623a85d1ca041737baf39e36 (origin/master)
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
#### Now we can push this new chnages to git hub

[root@ip-172-31-5-172 mydir]# git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 355 bytes | 355.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:jomyg/git-repo-test.git
   cb4b75d..8831c9f  master -> master
    
[root@ip-172-31-5-172 mydir]# git log --oneline
8831c9f (HEAD -> master, origin/master) docker added
cb4b75d atop installation
2e29323  Apache installation task 1
=================================================================================================================================

>>>>>>>>>>>>>>>>>>>>>>>  Now we can setup a remote server to access this git repo

[root@ip-172-31-2-99 ~]# git clone https://github.com/jomyg/git-repo-test.git
Cloning into 'git-repo-test'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 9 (delta 2), reused 9 (delta 2), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
[root@ip-172-31-2-99 ~]# ls
git-repo-test
[root@ip-172-31-2-99 ~]# cd git-repo-test/
[root@ip-172-31-2-99 git-repo-test]# ll
total 4
-rw-r--r-- 1 root root 547 Mar 17 11:32 main.yml
[root@ip-172-31-2-99 git-repo-test]# git log         >>>>>>>>>>>>>>>>>>> We can see the same on our remote meachine tho
commit 8831c9fee4badf1c424aee18393d15115845bfc8 (HEAD -> master, origin/master, origin/HEAD)
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:25:04 2022 +0000

    docker added

commit cb4b75d1402427ab623a85d1ca041737baf39e36
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
[root@ip-172-31-2-99 git-repo-test]#

================================================================================================================

Now we can add some contents to project on Main server and push it


[root@ip-172-31-5-172 mydir]# git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.yml

no changes added to commit (use "git add" and/or "git commit -a")
[root@ip-172-31-5-172 mydir]# git add .
[root@ip-172-31-5-172 mydir]# git commit -m "added git"
[master 1a5e99e] added git
 1 file changed, 5 insertions(+)
[root@ip-172-31-5-172 mydir]# git log --oneline
1a5e99e (HEAD -> master) added git
8831c9f (origin/master) docker added
cb4b75d atop installation
2e29323  Apache installation task 1
[root@ip-172-31-5-172 mydir]# git push origin master
Warning: Permanently added the ECDSA host key for IP address '13.234.176.102' to the list of known hosts.
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 274 bytes | 274.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:jomyg/git-repo-test.git
   8831c9f..1a5e99e  master -> master
    
>> Now inorder to get the new contents we have added on the github on remote meachine use the below

[root@ip-172-31-2-99 git-repo-test]# git remote
origin
[root@ip-172-31-2-99 git-repo-test]# git remote -v
origin  https://github.com/jomyg/git-repo-test.git (fetch)
origin  https://github.com/jomyg/git-repo-test.git (push)
[root@ip-172-31-2-99 git-repo-test]# git pull origin master                   >>>>>>>>>>>>>>>>>>>>>>>>>>> Used command
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (3/3), 254 bytes | 254.00 KiB/s, done.
From https://github.com/jomyg/git-repo-test
 * branch            master     -> FETCH_HEAD
   8831c9f..1a5e99e  master     -> origin/master
Updating 8831c9f..1a5e99e
Fast-forward
 main.yml | 5 +++++
 1 file changed, 5 insertions(+)
[root@ip-172-31-2-99 git-repo-test]# git log
commit 1a5e99e33fbb94fed739c0bead96d5e10cb93fbc (HEAD -> master, origin/master, origin/HEAD)
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:36:12 2022 +0000

    added git

commit 8831c9fee4badf1c424aee18393d15115845bfc8
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:25:04 2022 +0000

    docker added

commit cb4b75d1402427ab623a85d1ca041737baf39e36
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
[root@ip-172-31-2-99 git-repo-test]#

Now I have added some new chnages on main server contents and pushed.
[root@ip-172-31-5-172 mydir]# nano main.yml
[root@ip-172-31-5-172 mydir]# git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.yml

no changes added to commit (use "git add" and/or "git commit -a")
[root@ip-172-31-5-172 mydir]# git add .
[root@ip-172-31-5-172 mydir]# git commit -m "added mysql"
[master f31c622] added mysql
 1 file changed, 5 insertions(+)
[root@ip-172-31-5-172 mydir]# git log --oneline
f31c622 (HEAD -> master) added mysql
1a5e99e (origin/master) added git
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1
[root@ip-172-31-5-172 mydir]# git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 280 bytes | 280.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:jomyg/git-repo-test.git
   1a5e99e..f31c622  master -> master
    
[root@ip-172-31-5-172 mydir]# git log --oneline
f31c622 (HEAD -> master, origin/master) added mysql
1a5e99e added git
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1
    =================================================================================================================================
Now on remote meachine, we can fetch the contents using the fetch but its all fetch commits not contents
[root@ip-172-31-2-99 git-repo-test]# git fetch origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (3/3), 260 bytes | 260.00 KiB/s, done.
From https://github.com/jomyg/git-repo-test
 * branch            master     -> FETCH_HEAD
   1a5e99e..f31c622  master     -> origin/master
[root@ip-172-31-2-99 git-repo-test]# git log --oneline
1a5e99e (HEAD -> master) added git
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1
#### Listing all branches

[root@ip-172-31-2-99 git-repo-test]# git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
[root@ip-172-31-2-99 git-repo-test]# git branch -a -v
* master                1a5e99e [behind 1] added git
  remotes/origin/HEAD   -> origin/master
  remotes/origin/master f31c622 added mysql                   ................. This is last commit we have added on main. 
[root@ip-172-31-2-99 git-repo-test]#

Now we can Switch to remote master branch

[root@ip-172-31-2-99 git-repo-test]# git switch -c remote-master origin/master 
Branch 'remote-master' set up to track remote branch 'master' from 'origin'.
Switched to a new branch 'remote-master'
[root@ip-172-31-2-99 git-repo-test]# git log --oneline
f31c622 (HEAD -> remote-master, origin/master, origin/HEAD) added mysql    >>> Now the contents also downloaded when we switch
1a5e99e (master) added git
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1
[root@ip-172-31-2-99 git-repo-test]# git branch
  master
* remote-master
[root@ip-172-31-2-99 git-repo-test]# git branch -v
  master        1a5e99e [behind 1] added git
* remote-master f31c622 added mysql

[root@ip-172-31-2-99 git-repo-test]# git log
commit f31c622538413db983843850517d0f9ea5496bb5 (HEAD -> remote-master, origin/master, origin/HEAD)        >> HEAD towards remote-master
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:43:31 2022 +0000

    added mysql

commit 1a5e99e33fbb94fed739c0bead96d5e10cb93fbc (master)
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:36:12 2022 +0000

    added git

commit 8831c9fee4badf1c424aee18393d15115845bfc8
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:25:04 2022 +0000

    docker added

commit cb4b75d1402427ab623a85d1ca041737baf39e36
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1

Now we have moved to master and the mysql contents is unavailble
[root@ip-172-31-2-99 git-repo-test]# git switch master
Switched to branch 'master'
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)
[root@ip-172-31-2-99 git-repo-test]# git log --oneline
1a5e99e (HEAD -> master) added git
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1

[root@ip-172-31-2-99 git-repo-test]# git branch
* master
  remote-master
[root@ip-172-31-2-99 git-repo-test]# git merge remote-master       >>>> By merging we can fetch the last commit mysql contents
Updating 1a5e99e..f31c622
Fast-forward
 main.yml | 5 +++++
 1 file changed, 5 insertions(+)

[root@ip-172-31-2-99 git-repo-test]# git log --oneline
f31c622 (HEAD -> master, origin/master, origin/HEAD, remote-master) added mysql
1a5e99e added git
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1
[root@ip-172-31-2-99 git-repo-test]#


### Now we can checkout to a commit ID using below

[root@ip-172-31-2-99 git-repo-test]# git log --oneline
f31c622 (HEAD -> master, origin/master, origin/HEAD, remote-master) added mysql
1a5e99e added git
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1
[root@ip-172-31-2-99 git-repo-test]# git checkout 8831c9f   >>>>> This will show the contents we have commited on the docker added
Note: switching to '8831c9f'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 8831c9f docker added

### BAck to master now
[root@ip-172-31-2-99 git-repo-test]# git checkout master
Previous HEAD position was 8831c9f docker added
Switched to branch 'master'
Your branch is up to date with 'origin/master'

[root@ip-172-31-2-99 git-repo-test]# git log
commit 8831c9fee4badf1c424aee18393d15115845bfc8 (HEAD -> development)         >>> From the commit id we have selected the new branch
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:25:04 2022 +0000

    docker added

commit cb4b75d1402427ab623a85d1ca041737baf39e36
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
    
====================================================================================================================================
Now I have added some content on remote and commit
[root@ip-172-31-2-99 git-repo-test]# nano main.yml
[root@ip-172-31-2-99 git-repo-test]# git config user.name "jomy-remote"
[root@ip-172-31-2-99 git-repo-test]# git config user.email "jomy12@gmail.com"
[root@ip-172-31-2-99 git-repo-test]# git add .
[root@ip-172-31-2-99 git-repo-test]# git commit -m "mariadb-remote"
[development 87ca5ee] mariadb-remote
 1 file changed, 5 insertions(+)
[root@ip-172-31-2-99 git-repo-test]#
[root@ip-172-31-2-99 git-repo-test]# git log
commit 87ca5eef3ad738a3db5b2a21081695b3fb095182 (HEAD -> development)
Author: jomy-remote <jomy12@gmail.com>
Date:   Thu Mar 17 12:15:07 2022 +0000

    mariadb-remote

commit 8831c9fee4badf1c424aee18393d15115845bfc8
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:25:04 2022 +0000

    docker added

commit cb4b75d1402427ab623a85d1ca041737baf39e36
Author: jomy <jomy1@gmail.com>
Date:   Thu Mar 17 11:08:41 2022 +0000

    atop installation

commit 2e293233608c2d1b6cbe563a80d2d8818c7b292d
Author: root <root@ip-172-31-5-172.ap-south-1.compute.internal>
Date:   Thu Mar 17 11:05:44 2022 +0000

     Apache installation task 1
    
    
[root@ip-172-31-2-99 git-repo-test]# git commit --amend -m "mariabd-remote -started" --reset-author
[development f4da44e] mariabd-remote -started
 1 file changed, 5 insertions(+)
[root@ip-172-31-2-99 git-repo-test]# git log --oneline
f4da44e (HEAD -> development) mariabd-remote -started
8831c9f docker added
cb4b75d atop installation
2e29323  Apache installation task 1
[root@ip-172-31-2-99 git-repo-test]#
