在日常开发中，打 **patch(补丁)** 是将某段代码变更应用到另一个代码库或分支的常用方式. Git 提供了两种主要方法来应用 patch，分别应用不同场景.

1. 用 `git format-patch` 生成的 Git 专用补丁文件 (.patch).
2. 用 `git diff` 生成的 UNIX 标准补丁文件 (.diff).

* *.patch* 记录了内容更改，有提交记录信息，一个提交只能对应一个 patch 文件.
* *.diff* 记录了内容更改，无提交记录信息，多个提交可以合并成一个 diff 文件.


**一、创建 patch 和 diff 文件**

* 创建 patch 文件
```batch
:: 将最近的一个提交，生成 .patch 文件
git format-patch -1

:: 将指定提交，生成 .patch 文件
git format-patch -1 b703f4d56

:: 将（b703f4d56, 最近的一个提交] 区间的所有提交，逐个生成 .patch 文件
git format-patch b703f4d56

:: 将 (915304, 94e737] 区间的所有提交，逐个生成 .patch 文件 (提交顺序915304..94e737)
git format-patch 915304..94e737
```

* 创建 diff 文件
```batch
:: 将最近的一个提交，生成 .diff 文件(文件名为 test)
git diff HEAD^ test.diff

:: 将指定提交，生成 .diff 文件
暂缺

:: 将（b703f4d56, 最近的一个提交] 区间的所有提交，生成一个 .diff 文件(文件名为 test)
git diff b703f4d56 > test.diff

:: 将 (915304, 94e737] 区间的所有提交，生成一个 .diff 文件(文件名为 test)
git diff 915304 94e737 > test.diff
```

**二、应用 patch 和 diff 文件**

* 应用 patch 文件
```batch
:: 应用生成的 patch 文件
git apply $"C:\Users\admin\Desktop\temp\testgit\0001-add123.patch"
```

* 应用 diff 文件
```batch
:: 应用生成的 diff 文件
git apply $"C:\Users\admin\Desktop\temp\testgit\test.diff"
```


