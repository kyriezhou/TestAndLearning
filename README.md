# WebTest

### 2019.03.17

- Test git clone  ➡️  `git clone <地址>` //将远端的代码以及相关分支信息clone到本地
- Test git add  ➡️  `git add <文件名>`
- Test git commit  ➡️  `git commit -m "description"`
- Test git push  ➡️  `git push`
- Test git pull  ➡️  `git pull`
- Test git status  ➡️  `git status` //查看相关文件的状态

### 2019.03.18

- Test git version 2.21.0

- Test git diff  ➡️  `git diff` //查看尚未暂存的文件更新了哪些部分

- Test git diff --cached  ➡️  `git diff --cache or git diff —staged` //查看已暂存的将要添加到下次提交里的内容

- 跳过使用暂存区域 `git commit -a -m "description"`

  #### 跳过使用暂存区域

  尽管使用暂存区域的方式可以精心准备要提交的细节，但有时候这么做略显繁琐。 Git 提供了一个跳过使用暂存区域的方式， 只要在提交的时候，给 `git commit` 加上 `-a` 选项，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 `git add` 步骤：

  ```console
  $ git status
  On branch master
  Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)
  
      modified:   CONTRIBUTING.md
  
  no changes added to commit (use "git add" and/or "git commit -a")
  $ git commit -a -m 'added new benchmarks'
  [master 83e38c7] added new benchmarks
   1 file changed, 5 insertions(+), 0 deletions(-)
  ```

- `git rm <file name>` 下一次提交时该文件不再纳入版本管理

  `git rm -f <file name>` 如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 `-f`（译注：即 force 的首字母）

  ```console
  $ git rm PROJECTS.md
  rm 'PROJECTS.md'
  $ git status
  On branch master
  Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)
  
      deleted:    PROJECTS.md
  ```

- 移动文件 `git mv`

  `git mv file_from file_to`

  运行 `git mv` 就相当于运行了下面三条命令：

  ```console
  $ mv README.md README
  $ git rm README.md
  $ git add README
  ```

- 查看提交历史 `git log`

  `-p` 用来心事每次提交的内容差异，`-2` 来仅显示最近两次提交 Kyrie
