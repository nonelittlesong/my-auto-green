# Actions

| Action | Status | Reference |
| --- | --- | --- |
| Auto Green | ![autogreen.yml](https://github.com/nonelittlesong/none-actions/actions/workflows/autogreen.yml/badge.svg)| [justjavac/auto-green](https://github.com/justjavac/auto-green) |
| Hub Mirror | ![coldwar2.yml](https://github.com/nonelittlesong/none-actions/actions/workflows/coldwar2.yml/badge.svg) | [Yikun/hub-mirror-action](https://github.com/Yikun/hub-mirror-action)
| Gitee Mirror | ![gitee-mirror.yml](https://github.com/nonelittlesong/none-actions/actions/workflows/gitee-mirror.yml/badge.svg) | [Hub Mirror Action](https://github.com/marketplace/actions/hub-mirror-action)

- [Github Actions 简介](https://docs.github.com/cn/actions/learn-github-actions/introduction-to-github-actions)

## Cron

```
┌───────────── 分钟 (0 - 59)
│ ┌───────────── 小时 (0 - 23)
│ │ ┌───────────── 日 (1 - 31)
│ │ │ ┌───────────── 月 (1 - 12 或 JAN-DEC)
│ │ │ │ ┌───────────── 星期 (0 - 6 或 SUN-SAT)
│ │ │ │ │
│ │ │ │ │
│ │ │ │ │
* * * * *
```

每个时间字段的含义  

|符号   | 描述        | 举例                                        |
| ----- | -----------| -------------------------------------------|
| `*`   | 任意值      | `* * * * *` 每天每小时每分钟                  |
| `,`   | 值分隔符    | `1,3,4,7 * * * *` 每小时的 1 3 4 7 分钟       |
| `-`   | 范围       | `1-6 * * * *` 每小时的 1-6 分钟               |
| `/`   | 每         | `*/15 * * * *` 每隔 15 分钟                  |

**注**：由于 GitHub Actions 的限制，如果设置为 `* * * * *` 实际的执行频率为每 5 分执行一次。

## License

- [auto-green](https://github.com/justjavac/auto-green) is released under the MIT License. See the bundled [LICENSE](./LICENSE) file for details.
