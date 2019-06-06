

 git 命令简单操作过程 
=====

wu-liang@wingame MINGW64 /y/Documents/blog/blog
`$ git clone https://github.com/sikongzaixing/blog.git`
Cloning into 'blog'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.

wu-liang@wingame MINGW64 /y/Documents/blog/blog
`$ git add . `
fatal: Not a git repository (or any of the parent directories): .git
wu-liang@wingame MINGW64 /y/Documents/blog/blog
`$ git push -u origin master`
fatal: Not a git repository (or any of the parent directories): .git
此处失败原因，【需要切换目录】
wu-liang@wingame MINGW64 /y/Documents/blog/blog
`$ ls`
blog/
wu-liang@wingame MINGW64 /y/Documents/blog/blog
`$ cd blog/`
wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ ls`
README.md  test.txt

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git push -u origin master`
fatal: HttpRequestException encountered.
   ▒▒▒▒▒▒▒▒ʱ▒▒▒▒
fatal: HttpRequestException encountered.
   ▒▒▒▒▒▒▒▒ʱ▒▒▒▒
Username for 'https://github.com': sikongzaixing
Everything up-to-date
Branch 'master' set up to track remote branch 'master' from 'origin'.

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git status`
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        test.txt

nothing added to commit but untracked files present (use "git add" to track)

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git add . `

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git commit -m "test"`
[master 642a7f9] test
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git push -u origin master`
fatal: HttpRequestException encountered.
   ▒▒▒▒▒▒▒▒ʱ▒▒▒▒
fatal: HttpRequestException encountered.
   ▒▒▒▒▒▒▒▒ʱ▒▒▒▒
Username for 'https://github.com': sikongzaixing
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 277 bytes | 138.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/sikongzaixing/blog.git
   1ea463a..642a7f9  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git help`
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Reapply commits on top of another base tip
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git rm test.txt`
rm 'test.txt'

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git commit -m "rm-test"`
[master 573b243] rm-test
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 test.txt

wu-liang@wingame MINGW64 /y/Documents/blog/blog/blog (master)
`$ git push origin master`
fatal: HttpRequestException encountered.
   ▒▒▒▒▒▒▒▒ʱ▒▒▒▒
fatal: HttpRequestException encountered.
   ▒▒▒▒▒▒▒▒ʱ▒▒▒▒
Username for 'https://github.com': sikongzaixing
Counting objects: 2, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (1/1), done.
Writing objects: 100% (2/2), 237 bytes | 118.00 KiB/s, done.
Total 2 (delta 0), reused 0 (delta 0)
To https://github.com/sikongzaixing/blog.git
   642a7f9..573b243  master -> master
