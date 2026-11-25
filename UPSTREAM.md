# 上游同步记录

- 上游仓库：https://github.com/Meloong-Git/MeloongCore
- 基线分支/提交：`master` / $(git rev-parse --short=12 upstream/master 2>/dev/null || git rev-parse --short=12 master)
- 本 fork 默认开发分支：`avalonia`（基于 `upstream/pcl-dev`）

## 本 fork 的本地修改（相对上游）

- 仅保留 `Shared/` 非 WPF 基础库；`Wpf/` 目录保留但不参与 PCL.Avalonia 构建（可忽略）。
- `Shared/` 内容：裁剪并适配 PCL.Avalonia 所需的 Config/Logger/PathUtils/FileUtils/Worker/扩展方法等。
- 目标框架：net10.0（上游为 netstandard2.0）。
- `Shared/General/Config.cs`：`JsonConfigProvider` 增加同路径共享实例（`GetShared`），供 PCL.Avalonia 单实例设置使用。
- 其余修改见 `git log upstream/master..avalonia`。

## 同步检查清单

1. `git fetch upstream && git log --oneline upstream/master..avalonia` 检查冲突风险；
2. 合并/摘取上游改动后 `dotnet build Shared/MeloongCore.csproj`；
3. 回到 PCL.Avalonia 更新子模块并跑全量 `dotnet test`；
4. 更新本文件的基线提交与修改说明。
