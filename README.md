# MeloongCore.Avalonia

本仓库是 [Meloong-Git/MeloongCore](https://github.com/Meloong-Git/MeloongCore) 的项目专用 fork，
供 [PCL.Avalonia](https://github.com/SuyihQwQ/PCL.Avalonia) 使用；从上游 `master` 分支建立，
去掉了 WPF 相关部分的使用需求，并针对 .NET 10 / Linux / macOS 做了裁剪与适配。

## 分支

- `master`：上游原样，用于对比与合并上游更新。
- `avalonia`：本 fork 的默认开发分支（当前默认分支请以仓库设置为准）。

## 同步上游

```bash
git remote add upstream https://github.com/Meloong-Git/MeloongCore.git  # 已配置时可跳过
git fetch upstream
git checkout avalonia
git merge upstream/master   # 或 cherry-pick 需要的提交
dotnet build Shared/MeloongCore.csproj
```

同步后请更新 `UPSTREAM.md` 中的基线提交，并在 PCL.Avalonia 重新跑测试。

## 许可

本 fork 保留上游 Apache License 2.0（见 `LICENSE.txt`）。对共享代码的修改同样以 Apache-2.0 发布；
PCL.Avalonia 中的 PCL 派生代码不受本仓库许可影响。
