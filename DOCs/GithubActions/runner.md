# Specifications for GitHub-hosted runners

GitHub 托管的运行器的规格

## 文件系统

GiHub 在虚拟机上的特定目录中执行操作和 shell 命令。虚拟机上的文件路径不是静态的。

| 目录 | 上下文 | 环境变量 | 描述 |
| --- | --- | --- | --- |
| home | / | HOME | `home/runner`，包含用户相关的数据。例如，此目录可能包含登录凭据。 |
| workspace | `${{ github.workspace }}` |GITHUB_WORKSPACE | 在此目录中执行操作和 shell 命令。GitHub 工作空间目录路径。如果您的工作流程使用 `actions/checkout` 操作，则工作空间目录是仓库的副本。如果不使用 actions/checkout 操作，该目录将为空。例如 `/home/runner/work/my-repo-name/my-repo-name`。 |
| workflow/event.json | / | GITHUB_EVENT_PATH | 具有完整 web 挂钩事件有效负载的文件路径。例如 `/github/workflow/event.json` |

### Docker 文件系统

在 Docker 容器中运行的操作在 `/github` 下的静态目录中。但强烈建议使用默认环境变量在 Docker 容器中构建文件路径。

- `/github/home` — 映射虚拟机的 `/home/runner`。
- `/github/workspace` — 映射虚拟机的 `/home/runner/work/my-repo-name/my-repo-name`
  **注：** GitHub Actions 必须由默认 Docker 用户 (root) 运行。 确保您的 Dockerfile 未设置 USER 指令，否则您将无法访问 GITHUB_WORKSPACE。
- `/github/workflow` — 映射虚拟机的 `.github/workflows` 或 `.github/workflows/xxx.yml`？
