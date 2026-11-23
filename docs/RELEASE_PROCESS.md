# 内容资源发行流程

本流程适用于 MieMiePreset 的预设本体和专用配套正则。维护规则见 [AGENTS.md](../AGENTS.md)，许可和署名说明见 [README](../README.md#授权--licensing)。预设与正则独立发版；修复正则时，按实际验证结果维护兼容记录。

## 发行前核验

1. 读取当前文档、Git 工作区、远端分支、Tag、Release 和索引。确认正式文件、版本、公开范围及 Owner 最终确认的 Release Notes。Release Notes 直接写入 GitHub Release，`EVOLUTION.md` 继续保留给预设演化史。
2. 核验原件来源、第三方署名及许可，检查隐私、凭据与内嵌代码。静态检查不运行原件。JSON 必须可解析，正式文件与 Owner 批准的原件逐字节一致，记录各自的大小和 SHA-256。来源、授权或安全问题未解决时，停止发布。
3. 以明确路径准备暂存区，核对全部文件、物件和待推送历史。检查有效 Author / Committer、SSH 签名和 GitHub SSH 认证，核对实际推送地址。所有检查通过后，签名提交，通过 SSH 推送并回读提交 SHA、文件白名单和 GitHub Verified。

## 版本、Tag 和附件

- 资源版本保留原始字符串。正式 Tag 指向包含批准资源的已核验提交。版本目录及正式 JSON 使用 `ver` 前缀，Git Tag 使用 `v` 前缀，Release Title 使用英文产品名和裸版本号。各项命名规则如下。

| 资源 | Resource ID | 版本 | Git Tag | Release Title | 正式文件名 |
| --- | --- | --- | --- | --- | --- |
| 预设本体 | `miemie.preset` | `X.X.X` | `miemie-preset-v<version>` | `MieMiePreset <version>` | `MieMiePreset-ver<version>.json` |
| 配套正则 | `miemie.preset.regex` | `X.X` | `miemie-preset-regex-v<version>` | `MieMiePreset Regex <version>` | `MieMiePreset-Regex-ver<version>.json`、`MieMiePreset-Regex-ver<version>-LargeFont.json` |

- 正式预设保存于 `presets/ver<version>/`，配套正则放在 `regex/ver<version>/`。正则特殊变体在版本号后追加 PascalCase 后缀，标准版沿用无后缀文件名。正则的两个变体共用版本、Tag、Release 和发行说明，各自记录附件。7.7 使用 `miemie-preset-regex-v7.7`、`MieMiePreset Regex 7.7`。
- 获批准后，以经过验证的 Tag 建立草稿 Release，通过已授权的 GitHub 界面或 API 上传正式附件。核对标题、发行文案、两个附件的实际名称、ID、字节大小、下载地址及 SHA-256；必要时在草稿阶段经授权下载复核。若 GitHub 规范化名称且影响下载契约，停止并交 Owner 确认。
- 草稿通过核验后公开 Release。随后匿名重新下载两个发布附件，校验与原件字节及 SHA-256 一致。仓库分支上的文件从推送时起即公开，独立报告其状态。正式发布后不静默替换附件。

## 公开资源索引

`catalog.json` 保留 `schemaVersion: 1` 及 `presets`、`regex` 两个数组。只有完成公开 Release 与附件回读的资源可登记。每个正则版本在 `regex` 中占一条记录。

| 字段 | 含义 |
| --- | --- |
| `id`、`version` | 资源 ID 与版本字符串，组合唯一。 |
| `release.id`、`release.tag`、`release.url` | 实际 GitHub Release ID、Tag 和公开页面地址。 |
| `variants[].id`、`variants[].name` | 版本内唯一的变体 ID 和 Owner 确定的完整中文展示名。客户端直接显示该名称。 |
| `variants[].path`、`variants[].size`、`variants[].sha256` | 仓库相对路径、字节数和最终附件的 SHA-256。按资源类型用 `presets/ver<version>/` 或 `regex/ver<version>/` 拼接正式文件名，保留变体后缀。 |
| `variants[].asset.id`、`variants[].asset.name`、`variants[].asset.downloadUrl` | 该 Release 返回的附件 ID、实际文件名和公开下载地址。 |
| `compatiblePresets[]` | 可省略。仅列已确认的预设 `id` 与 `version`；需要限定变体时附 `variantIds`。 |

7.7 的变体 `standard` 使用「咩咩预设-专用正则-ver7.7」，`large-font` 使用「咩咩预设-专用正则-ver7.7-大字体版(PC端推荐)」。登记时以实际公开 Release 和附件数据为准。

预设与正则可多对多匹配。兼容关系未知的正则可出现在独立下载列表，按预设筛选时仅展示已有兼容依据的变体。

提交索引前，解析实际 JSON，核对资源和变体键唯一、Tag 与 Release 身份匹配、每一条附件引用属于对应 Release、路径存在于 Tag 指向的提交、已登记的大小和 SHA-256 与重新下载的字节一致。最终通过 SSH 提交并推送索引，复核公开索引、Tag、Release 和附件的一致性。
