# 更新约定（CONTRIBUTING）

本仓库是**本机 DSH 正在使用插件**的可读汇总，维护权归属仓库所有者。

## 硬性规则

> **未经仓库所有者明确同意，任何更新都不得合并或推送。**

## 更新流程

1. 新增/修改/删除条目，请先提出 **Issue**（说明变更原因）或提交 **Pull Request**。
2. 由所有者审阅并明确同意后，才可合并。
3. 本机实际启用的插件若发生变化（安装/卸载/升级），先更新本机配置
   （`~/.dsh/profiles/web/package.json` 的 `dsh.profile.bundles`、`cordis.patch.yml`），
   再按上述流程同步本清单。

## 内容范围

- 插件名（npm 包名 / 本地 link 名）
- 仓库（GitHub 地址或本地路径）
- 介绍（一句话功能说明）
- 本机使用频率（基于实际使用的主观分级：每回合 / 每次打开 / 常用 / 按需 / 常驻 / 未运行）

## 数据来源

- 运行中插件：`~/.dsh/profiles/web/package.json`（`dsh.profile.bundles`）+ `cordis.patch.yml`
- 本机源码工程：`D:/1` 下的 `dsh-*` 目录

欢迎通过 Issue 提出更新建议。