# [上下文和表达式](https://docs.github.com/cn/free-pro-team@latest/actions/reference/context-and-expression-syntax-for-github-actions)

**表达式**

`${{ expression }}`

在 `if` 条件语句下，可省略 `${{}}`。

**上下文**

| 上下文名称 | 类型 | 描述 |
| --- | --- | --- |
| github | 对象 | 工作流程运行的相关信息 |
| env | 对象 | 包含工作流程、作业或步骤中设置的环境变量 |
| job | 对象 | 当前执行的作业相关信息 |
| steps | 对象 | 此作业中已经运行的步骤的相关信息 |
| runner | 对象 | 运行当前作业的运行程序相关信息 |
| secrets | 对象 | 启用对密码的访问权限 |
| strategy | 对象 | 用于访问配置的策略参数及当前作业的相关信息。策略参数包括 `fail-fast`、`job-index`、`job-total` 和 `max-parallel`。|
| matrix | 对象 | 用于访问当前作业配置的矩阵参数。例如，如果使用 `os` 和 `node` 版本配置矩阵构建，`matrix` 上下文对象将包含当前作业的 `os` 和 `node` 版本。|
| needs | 对象 | 允许访问定义为当前作业依赖项的所有作业的输出 |

可以使用以下两种形式访问上下文信息：

- 索引语法 — `github['sha']`
- 属性取值语法 — `github.sha`

要使用属性取值语法，属性名称必须：

- 以 `a-Z` 或 `_` 开头
- 后跟 `a-Z` `0-9` `-` 或 `_`

## runner

| 属性名称 | 类型 | 描述 |
| --- | --- | --- |
| runner.os | 字符串 | 执行作业的运行器的操作系统，`Linux`、`Windows` 或 `macOS` |
| runner.temp | 字符串 | 运行器临时目录的路径。此目录保证在每个作业开始时为空，即使在自托管的运行器上也是如此。 |
| runner.tool_cache | 字符串 | 包含 [Github 托管运行器](https://docs.github.com/cn/free-pro-team@latest/actions/reference/specifications-for-github-hosted-runners#supported-software)一些预安装工具的目录路径。|

