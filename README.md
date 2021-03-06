# Test And Learning

## Git 

From https://git-scm.com/book/zh/v2/

### 2019.03.17

- Test git clone  ➡️  `git clone [address]` //将远端的代码以及相关分支信息clone到本地
- Test git add  ➡️  `git add [file name]`
- Test git commit  ➡️  `git commit -m [description]`
- Test git push  ➡️  `git push`
- Test git pull  ➡️  `git pull`
- Test git status  ➡️  `git status` //查看相关文件的状态

### 2019.03.18

- Test git version 2.21.0

- Test git diff  ➡️  `git diff` //查看尚未暂存的文件更新了哪些部分

- Test git diff --cached  ➡️  `git diff --cache or git diff —staged` //查看已暂存的将要添加到下次提交里的内容

- 跳过使用暂存区域 `git commit -a -m [description]`

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

- `git rm [file name]` 下一次提交时该文件不再纳入版本管理

  `git rm -f [file name]` 如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 `-f`（译注：即 force 的首字母）

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

  `-p` 用来心事每次提交的内容差异，`-2` 来仅显示最近两次提交

  `git log --pretty=oneline` 将每个提交放在一行显示，查看的提交数很大时非常有用

  `git log —pretty=format:"format"` 定制显示的记录格式：

  | 选项  | 说明                                        |
  | :---: | :------------------------------------------ |
  | `%H`  | 提交对象（commit）的完整哈希字串            |
  | `%h`  | 提交对象的简短哈希字串                      |
  | `%T`  | 树对象（tree）的完整哈希字串                |
  | `%t`  | 树对象的简短哈希字串                        |
  | `%P`  | 父对象（parent）的完整哈希字串              |
  | `%p`  | 父对象的简短哈希字串                        |
  | `%an` | 作者（author）的名字                        |
  | `%ae` | 作者的电子邮件地址                          |
  | `%ad` | 作者修订日期（可以用 --date= 选项定制格式） |
  | `%ar` | 作者修订日期，按多久以前的方式显示          |
  | `%cn` | 提交者（committer）的名字                   |
  | `%ce` | 提交者的电子邮件地址                        |
  | `%cd` | 提交日期                                    |
  | `%cr` | 提交日期，按多久以前的方式显示              |
  | `%s`  | 提交说明                                    |

- 取消对文件的暂存 `git reset HEAD [file]`

- 撤销对文件的修改 `git checkout -- [file]`

   `git checkout -- [file]` 是一个危险的命令，这很重要。 你对那个文件做的任何修改都会消失 - 你只是拷贝了另一个文件来覆盖它。 除非你确实清楚不想要那个文件了，否则不要使用这个命令。

- Git 别名

  在创建你认为应该存在的命令时这个技术会很有用。 例如，为了解决取消暂存文件的易用性问题，可以向 Git 中添加你自己的取消暂存别名：

  ```console
  $ git config --global alias.unstage 'reset HEAD --'
  ```

  这会使下面的两个命令等价：

  ```console
  $ git unstage fileA
  $ git reset HEAD -- fileA
  ```

  这样看起来更清楚一些。 通常也会添加一个 `last` 命令，像这样：

  ```console
  $ git config --global alias.last 'log -1 HEAD'
  ```

  这样，可以轻松地看到最后一次提交：

  ```console
  $ git last
  ```


### 2019.03.24

### 2019.03.28