# MieMiePreset / 咩咩预设

这里托管面向 SillyTavern 的咩咩预设（MieMiePreset）及其专用配套正则，用于版本发布和在线分发。首个配套正则版本 [MieMiePreset Regex 7.7](https://github.com/SheepSheepLab/MieMie-Presets/releases/tag/miemie-preset-regex-v7.7) 已发布，提供标准版和大字体版。目前暂无正式预设。

This is the official repository for MieMiePreset and its companion regex resources for SillyTavern. The first companion regex release, [MieMiePreset Regex 7.7](https://github.com/SheepSheepLab/MieMie-Presets/releases/tag/miemie-preset-regex-v7.7), is available in Standard and LargeFont variants. Preset releases are pending.

| 项目身份 / Project identity | |
| --- | --- |
| 创始人及作者 / Founder and author | SheepSheep |
| 仓库及维护方 / Repository and maintenance | [SheepSheepLab](https://github.com/SheepSheepLab/MieMie-Presets) |

## 仓库结构 / Repository layout

| 路径 / Path | 用途 / Purpose |
| --- | --- |
| [`presets/`](presets/) | 正式预设文件，按 `presets/ver<version>/` 分目录 / Official presets, grouped under `presets/ver<version>/` |
| [`regex/`](regex/) | 配套正则文件，按 `regex/ver<version>/` 分目录 / Companion regex resources, grouped under `regex/ver<version>/` |
| [`catalog.json`](catalog.json) | 在线资源索引 / Online resource catalog |
| [`docs/EVOLUTION.md`](docs/EVOLUTION.md) | 预设功能与设计演化史，待作者整理 / Preset feature and design history, pending author review |
| [`docs/RELEASE_PROCESS.md`](docs/RELEASE_PROCESS.md) | 资源发行与目录维护流程 / Resource release and catalog maintenance |

预设与正则独立版本化。预设升级时，可继续使用已确认兼容的正则版本。

Presets and regex resources are versioned independently. A preset update can continue to use a regex version whose compatibility has been confirmed.

## 资源身份与命名 / Resource identity and naming

预设本体和配套正则均属于 MieMiePreset。各自独立维护版本和发行记录。版本目录和 JSON 文件名使用 `ver` 前缀，Git Tag 使用 `v` 前缀，Release Title 使用英文产品名和裸版本号。下表中的版本用于说明命名规则。

The preset and its companion regex both belong to MieMiePreset. Each has its own versions and releases. Version directories and JSON filenames use the `ver` prefix. Git tags use `v`. Release titles use the English product name and the bare version number. The table shows naming examples.

| 资源 / Resource | Resource ID | 版本 / Version | Git Tag 示例 / Example | Release Title 示例 / Example | 文件名示例 / Example filename |
| --- | --- | --- | --- | --- | --- |
| 预设本体 / Preset | `miemie.preset` | `X.X.X` | `miemie-preset-v6.2.0` | `MieMiePreset 6.2.0` | `MieMiePreset-ver6.2.0.json` |
| 专用配套正则 / Preset Regex | `miemie.preset.regex` | `X.X` | `miemie-preset-regex-v7.7` | `MieMiePreset Regex 7.7` | `MieMiePreset-Regex-ver7.7.json` |

同一正则版本可包含标准版及不同适配变体。所有经 Owner 批准并实际发行的同版本变体，共用资源 ID、版本号、Git Tag、Release 和发行说明，各自作为独立 JSON 附件发布。标准版文件名不添加变体后缀；大字体版使用 `-LargeFont`；非 SillyTavern 版使用 `-NonSillyTavern`。其他变体的名称和后缀须经 Owner 确认。下载列表中的完整中文展示名称以 `catalog.json` 中对应变体的 `variants[].name` 为准，不得根据英文文件名或 Release Title 自动生成。

A regex version may include the standard variant and additional compatibility variants. All Owner-approved variants actually published under the same version share one resource ID, version number, Git tag, GitHub release, and release notes. Each variant is distributed as a separate JSON asset. The standard variant has no filename suffix; the large-font variant uses `-LargeFont`, and the non-SillyTavern variant uses `-NonSillyTavern`. Additional variant names and suffixes require Owner approval. Download lists must use the exact Chinese display name recorded in the corresponding `variants[].name` entry in `catalog.json`, rather than deriving it from filenames or release titles.

## 在线分发计划 / Planned online distribution

咩咩预设管理（MieMie Preset Manager）是独立的软件工具。

未来计划在[咩咩预设管理](https://github.com/SheepSheepLab/MieMie-Preset-Manager)中支持选择预设和兼容的配套正则，下载后导入 SillyTavern，通过原生机制自动绑定预设专属正则，再保存并回读确认。这个流程尚未实现。

MieMie Preset Manager is a separate software tool.

The planned [MieMie Preset Manager](https://github.com/SheepSheepLab/MieMie-Preset-Manager) workflow will let users select a preset and a compatible regex version, download and import both into SillyTavern, and use its native mechanism to bind the regex to the preset. The workflow will save and read back the result to confirm it. This workflow has yet to be implemented.

## 授权 / Licensing

**Copyright © 2026 SheepSheep**，适用于 SheepSheep 享有相应权利的原创贡献。SheepSheep 是原作者和项目发起者，SheepSheepLab 是官方 GitHub 开发、维护与发布命名空间。实际社区贡献者保留自己的署名与版权，第三方内容适用其各自的授权条款。

本仓库中 SheepSheep 有权授权的原创预设和正则采用 **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International（CC BY-NC-SA 4.0）**，涵盖相应的文本、正则表达式、配置和内嵌 JavaScript、HTML、CSS。完整条款见 [LICENSE](LICENSE)。

你可以按许可非商业使用、转载、分享和改编这些内容。分享时按许可保留适当署名和原始来源，提供许可信息并注明修改。公开分享改编作品时，使用相同或许可允许的兼容许可。超出非商业条款范围的使用需要另行授权。

二创作者可以为自己新增的原创内容署名，同时保留 SheepSheep 对原作品的署名。下列写法可按发布场景调整：

> - 原始作品：咩咩预设（MieMiePreset）
> - 原作者：SheepSheep
> - 原始项目：[SheepSheepLab/MieMie-Presets](https://github.com/SheepSheepLab/MieMie-Presets)
> - 二创作者：填写实际作者
> - 许可：[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
> - 修改说明：如实说明改动

在 LN 等支持提及的平台，可选用 @SheepSheep 提示来源。平台提及是自愿做法，署名义务以许可证为准。

咩咩 / MieMie 品牌、Logo、角色形象及其他独立受保护的品牌视觉资产适用各自的授权。可以如实说明作品源自或基于 MieMie Presets，独立 Fork 应清楚标明自己的身份，避免让用户误认为是官方发布。MieMie Hub、MieMie Preset Manager 等项目的软件继续适用各自的许可证。

SheepSheep is the original author and project initiator. SheepSheepLab is the official GitHub namespace for development, maintenance, and releases. The copyright notice covers SheepSheep's original contributions. Contributors and third-party rightsholders retain their own attribution and rights.

Original preset and regex content that SheepSheep has the rights to license is available under [CC BY-NC-SA 4.0](LICENSE), including covered text, expressions, configuration, and embedded JavaScript, HTML, and CSS. For noncommercial sharing or adaptations, credit the original author, link to the source and license, and indicate changes. If you share an adaptation, use the same license or a compatible license permitted by its terms. You may also credit your own original additions.

The MieMie / 咩咩 brand, logos, character imagery, and independently protected brand assets are governed by their own permissions. Describe the source of your work accurately and identify independent forks as such. Other MieMie software projects retain their respective licenses.
