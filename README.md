# git learn
## 一、基础

## 二、git分支管理策略
### 2.1 Vincent Driessen 分支管理策略
> 只存在两套分支
> 主分支master：所有提供给用户使用的正式版本，都在这个主分支上发布。
> 开发分支develop：主分支只用来分布重大版本，日常开发应该在另一条分支上完成。我们把开发用的分支，叫做Develop。
这个分支可以用来生成代码的最新隔夜版本（nightly）。如果想正式对外发布，就在Master分支上，对Develop分支进行"合并"（merge）。

git 创建 develop 分支的命令
```shell script
git checkout -b develop master
```

将develop分支发布到master分支的命令：
```shell script
# 切换到Master分支
　　git checkout master
# 对Develop分支进行合并
　　git merge --no-ff develop
```

> --no-ff 参数是什么意思。默认情况下，Git执行"快进式合并"（fast-farward merge），会直接将Master分支指向Develop分支。

临时性分支
除了常设分支以外，还有一些临时性分支，用于应对一些特定目的的版本开发。临时性分支主要有三种：

* 功能（feature）分支

* 预发布（release）分支

* 修补bug（fixbug）分支

1. 第一种是功能分支，它是为了开发某种特定功能，从Develop分支上面分出来的。开发完成后，要再并入Develop。
2. 第二种是预发布分支，它是指发布正式版本之前（即合并到Master分支之前），我们可能需要有一个预发布的版本进行测试。
   预发布分支是从Develop分支上面分出来的，预发布结束以后，必须合并进Develop和Master分支。它的命名，可以采用release-*的形式。
3. 修补bug分支最后一种是修补bug分支。软件正式发布以后，难免会出现bug。这时就需要创建一个分支，进行bug修补。
   修补bug分支是从Master分支上面分出来的。修补结束以后，再合并进Master和Develop分支。它的命名，可以采用fixbug-*的形式。

