how this was used:   there are key things a noob will need

pi@raspberrypi:~ $ cd gitdocuments
pi@raspberrypi:~/gitdocuments $ echo "# gitpi" >> README.md
pi@raspberrypi:~/gitdocuments $ git init
Initialized empty Git repository in /home/pi/gitdocuments/.git/
pi@raspberrypi:~/gitdocuments $ git add README.md
pi@raspberrypi:~/gitdocuments $ git commit -m "first commit"
[master (root-commit) 88b4f66] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
pi@raspberrypi:~/gitdocuments $ git remote add origin https://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@github.com/jimsybeldon/gitpi.git
pi@raspberrypi:~/gitdocuments $ git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 223 bytes | 223.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/jimsybeldon/gitpi.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
pi@raspberrypi:~/gitdocuments $ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
pi@raspberrypi:~/gitdocuments $ ls
README.md
pi@raspberrypi:~/gitdocuments $ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
pi@raspberrypi:~/gitdocuments $ git commit -am "updated the pi README.md"
[main d7013fb] updated the pi README.md
 1 file changed, 3 insertions(+)
pi@raspberrypi:~/gitdocuments $ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
pi@raspberrypi:~/gitdocuments $ git log
commit d7013fba74e8bfbf0c09af6d287332af8accb99c (HEAD -> main)
Author: JimSybeldon <JimPiSybeldon@yahoo.com>
Date:   Thu Nov 10 09:47:07 2022 -0600

    updated the pi README.md

commit 88b4f66751e2eb66de3febe7077db7d7064ff816 (origin/main)
Author: JimSybeldon <JimPiSybeldon@yahoo.com>
Date:   Thu Nov 10 09:37:15 2022 -0600

    first commit

pi@raspberrypi:~/gitdocuments $ git push -u origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 316 bytes | 316.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/jimsybeldon/gitpi.git
   88b4f66..d7013fb  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
pi@raspberrypi:~/gitdocuments $ 




this next shit is about git pull and conflicting updates



pi@raspberrypi:~ $ cd gitdocuments
pi@raspberrypi:~/gitdocuments $ git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/jimsybeldon/gitpi
   d7013fb..2de0400  main       -> origin/main
pi@raspberrypi:~/gitdocuments $ git status
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
pi@raspberrypi:~/gitdocuments $ git status
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
pi@raspberrypi:~/gitdocuments $ git commit -am "once around for README.md"
[main c2fee80] once around for README.md
 1 file changed, 2 insertions(+)
pi@raspberrypi:~/gitdocuments $ git push -u origin main
To https://github.com/jimsybeldon/gitpi.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://<KEYHERE>@github.com/jimsybeldon/gitpi.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pi@raspberrypi:~/gitdocuments $ git pull --help
pi@raspberrypi:~/gitdocuments $ git pull
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
pi@raspberrypi:~/gitdocuments $ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
pi@raspberrypi:~/gitdocuments $ git add README.md
pi@raspberrypi:~/gitdocuments $ git pull
error: You have not concluded your merge (MERGE_HEAD exists).
hint: Please, commit your changes before merging.
fatal: Exiting because of unfinished merge.
pi@raspberrypi:~/gitdocuments $ git commit -am "once around for README.md"
[main 46c9616] once around for README.md
pi@raspberrypi:~/gitdocuments $ git push -u origin main
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 677 bytes | 677.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/jimsybeldon/gitpi.git
   2de0400..46c9616  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
pi@raspberrypi:~/gitdocuments $ git pull
Already up to date.

