# Git 代码规范

## Git 命名方式
- 所有的branch 分支的名字必须是小写英语字母来防止Windows客户端有两个不同分支有相同的字母但是大小写不同。

### Master Branch(主分支)
这个分支主要是拿来放稳定的、上线中的版本，通常不会直接 `commit` 到这个分支上，而是在别的分支测试到稳定后才会 `merge` 到这个 `branch` 上。

### Feature Branch (功能分支)
- 顾名思义，就是当要新增功能时就会使用这条分支，然后再 `merge` 到 `Master` 上。 
- 在添加新的功能内容之时，需要创建一个`Pull Request`， 并且需要最少一个人Review 之后才能`merge` 到 `Master`。
- 需要解决所有对话（Resolve all Conversations）才可以将 `PR` merge 至 `Master`

### 代码作者
作者应当
- 指派所需的拉取请求审核者。
- 检查所有信息是否完整，并开放拉取请求以供审查。
- 向相关的审核者和利益相关者通报新的拉取请求以供审查。
- 需要简单描述 commit message

### 代码审核者
- 需要根据代码Guide 对作者的代码进行检查， 并对其代码提出相应的建议

### Git 流程举例
* 第一步：`git checkout -b <branch_name>` 创建一个分支
* 第二步： 对代码进行修改
* 第三步： 对代码进行提交
    ```bash
    git add <your changes>
    git commit -m "commit messages"
    git push -u origin <branch_name>
    ```
* 第四步：创建PR
* 第五步：请求Review
* 第六步：根据Reviewer 修改代码
* 第七步：Merge 进入 Master