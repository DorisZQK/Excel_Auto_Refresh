# Excel Auto Refresh 新手教程

这份教程写给完全不会写代码、不会用 GitHub、不会配置自动化工具的用户。你只需要按步骤操作即可。

## 0. 先弄清楚你是哪类用户

如果你只是想每天自动刷新 Excel 文件，你是“普通使用者”。你只需要下载并运行 `ExcelAutoRefresh.exe`。

如果你想让 Codex 以后也能理解和维护这个工具，你是“Codex / Skill 配置者”。你需要下载整个 GitHub 项目，并把它放到 Codex 的 skills 目录。

大多数业务同事只需要看第 1 部分和第 2 部分。

## 1. 普通用户：如何下载并使用 exe

### 1.1 准备条件

请确认你的电脑满足这些条件：

- 电脑是 Windows 系统。
- 电脑已经安装 Microsoft Excel 桌面版。
- 你要刷新的 Excel 文件没有被别人占用，也没有正在被你手动打开。

### 1.2 下载 exe

推荐方式是从 GitHub Releases 下载。

1. 打开项目页面：  
   https://github.com/DorisZQK/Excel_Auto_Refresh
2. 找到右侧或页面中的 `Releases`。
3. 点击最新版本，例如 `v1.0.0`。
4. 下载 `ExcelAutoRefresh.exe`。
5. 把它放到一个固定位置，例如：

```text
D:\Tools\ExcelAutoRefresh\ExcelAutoRefresh.exe
```

如果还没有 Release，可以请维护者先发布 Release，或者由维护者把 exe 文件单独发给你。

### 1.3 第一次打开

1. 双击 `ExcelAutoRefresh.exe`。
2. 如果 Windows 弹出安全提醒，确认文件来源是你信任的项目后，再选择继续运行。
3. 打开后你会看到中英双语界面。

界面上的隐私提示意思是：文件只在你的电脑本机打开和刷新，不会上传到云端。

### 1.4 添加一个自动刷新任务

1. 点击 `Add task / 添加任务`。
2. 点击 `Browse / 浏览`。
3. 选择你要自动刷新的 Excel 文件。
4. 在时间框里输入每天刷新时间，例如：

```text
09:30
```

5. 确认 `Enable this task / 启用此任务` 已勾选。
6. 点击 `Save / 保存`。

保存后，主界面会出现一行任务。

### 1.5 立即测试一次

建议每个任务刚添加后都先测试一次。

1. 在主界面选中刚添加的任务。
2. 点击 `Run now / 立即运行`。
3. 等待刷新完成。
4. 如果看到成功提示，说明这个 Excel 文件可以被自动刷新。

如果失败，点击 `Logs / 日志` 查看错误信息。常见原因包括：

- Excel 文件正在被打开。
- 文件路径不存在。
- Excel 文件需要登录某个数据源。
- Excel 弹出了权限或更新链接提示。
- 电脑没有安装 Excel 桌面版。

### 1.6 每天自动运行

保存任务后，工具会自动创建 Windows 计划任务。

你不需要一直打开这个工具。即使主窗口关闭，Windows 到时间也会尝试自动运行刷新。

如果电脑在计划时间关机，Windows 会在电脑下次可用时尽快补跑。

### 1.7 暂停、恢复、编辑、删除任务

先在任务列表里点击选中一个任务，然后：

- `Run now / 立即运行`：马上刷新一次。
- `Edit / 编辑`：修改文件路径或刷新时间。
- `Pause / Enable / 暂停 / 启用`：暂停或恢复自动刷新。
- `Delete / 删除`：删除这个刷新任务。
- `Logs / 日志`：打开本地日志文件夹。
- `Refresh / 刷新`：刷新界面显示。

## 2. 普通用户常见问题

### 2.1 文件会被上传吗？

不会。这个工具只调用你电脑本机的 Excel 打开、刷新、保存文件。

### 2.2 它会修改我的公式吗？

不会。当前版本不会填充公式，不会解除工作表保护，也不会重新保护工作表。

### 2.3 为什么刷新失败？

最常见原因是 Excel 文件正在被打开。请先关闭 Excel 文件，再点击 `Run now / 立即运行` 测试。

如果你的 Excel 连接了公司数据库、Power BI、SharePoint 或其他数据源，请确认你已经有权限，并且本机 Excel 可以手动刷新成功。

### 2.4 日志在哪里？

点击界面里的 `Logs / 日志`。日志默认保存在：

```text
%APPDATA%\ExcelAutoRefresh\logs
```

### 2.5 配置保存在哪里？

任务配置默认保存在：

```text
%APPDATA%\ExcelAutoRefresh\config.json
```

普通用户一般不需要手动打开这个文件。

## 3. Codex 用户：如何从 GitHub 下载 skill

这一部分给需要把它配置成 Codex skill 的人看。

### 3.1 下载 GitHub 项目

1. 打开项目页面：  
   https://github.com/DorisZQK/Excel_Auto_Refresh
2. 点击绿色的 `Code` 按钮。
3. 点击 `Download ZIP`。
4. 下载完成后解压。

解压后你会得到一个文件夹，通常叫：

```text
Excel_Auto_Refresh-main
```

### 3.2 找到 Codex skills 目录

在这台电脑上，skills 目录通常是：

```text
E:\.codex\skills
```

如果你的 Codex 安装位置不同，也可能是：

```text
C:\Users\你的用户名\.codex\skills
```

如果没有 `skills` 文件夹，可以手动新建。

### 3.3 放入 skill

1. 在 skills 目录下新建一个文件夹：

```text
excel-pivot-auto-refresh
```

2. 把 GitHub 解压出来的这些内容复制进去：

```text
SKILL.md
agents
references
scripts
README.md
docs
```

最终结构应类似：

```text
E:\.codex\skills\excel-pivot-auto-refresh\SKILL.md
E:\.codex\skills\excel-pivot-auto-refresh\references\PRD.md
E:\.codex\skills\excel-pivot-auto-refresh\scripts\excel_auto_refresh_app.py
```

### 3.4 重启 Codex

复制完成后，关闭并重新打开 Codex。

之后你可以在 Codex 里这样说：

```text
使用 $excel-pivot-auto-refresh 帮我维护 Excel 自动刷新工具
```

或：

```text
Use $excel-pivot-auto-refresh to update the Excel auto refresh app.
```

## 4. 维护者：如何从源码重新生成 exe

普通用户不需要看这一部分。

### 4.1 下载源码

打开项目页面：

```text
https://github.com/DorisZQK/Excel_Auto_Refresh
```

点击：

```text
Code > Download ZIP
```

然后解压到本地。

### 4.2 安装 Python

如果电脑没有 Python，请先安装 Python 3.10 或更高版本。

安装时建议勾选：

```text
Add Python to PATH
```

### 4.3 构建 exe

在项目根目录打开 PowerShell，运行：

```powershell
powershell -ExecutionPolicy Bypass -File scripts\build.ps1
```

构建完成后，exe 会生成在：

```text
scripts\dist\ExcelAutoRefresh.exe
```

### 4.4 发布给普通用户

建议把 `ExcelAutoRefresh.exe` 上传到 GitHub Release。

不要让普通用户下载源码再自己构建，这会给他们带来不必要的心理负担。

## 5. 推荐分享方式

给普通业务用户，推荐只发 Release 下载链接和一句说明：

```text
下载 ExcelAutoRefresh.exe，双击打开，点击“添加任务”选择 Excel 文件并设置每日刷新时间即可。文件只在本机刷新，不会上传。
```

给技术同事或维护者，可以发 GitHub 项目链接：

```text
https://github.com/DorisZQK/Excel_Auto_Refresh
```

## 6. 安全提醒

请只刷新你自己有权限访问的 Excel 文件。

如果 Excel 连接了公司内部系统，自动刷新仍然会使用你电脑本机 Excel 的权限和登录状态。

如果公司 IT 对 exe 文件有限制，请先让 IT 或管理员确认后再分发。
