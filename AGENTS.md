# MieMiePreset 仓库维护规范

## 资源与版本

- MieMiePreset（咩咩预设）是主体作品。预设本体与其专用配套正则分别使用资源 ID `miemie.preset` 和 `miemie.preset.regex`。配套正则不设独立产品身份。
- `presets/ver<version>/` 保存该版本的正式预设，`regex/ver<version>/` 保存该版本的配套正则。目录和正式 JSON 文件使用 `ver` 前缀，Git Tag 使用 `v` 前缀。Release Title 使用英文产品名和裸版本号。两类资源独立版本化，分别核验各自版本及兼容关系。预设升级不要求正则同步升版。
- 预设版本使用 `X.X.X`，Tag 为 `miemie-preset-v<version>`，英文标题为 `MieMiePreset <version>`，正式文件名为 `MieMiePreset-ver<version>.json`。
- 正则版本使用 `X.X`，Tag 为 `miemie-preset-regex-v<version>`，英文标题为 `MieMiePreset Regex <version>`。标准版与大字体版使用 `MieMiePreset-Regex-ver<version>.json` 和 `MieMiePreset-Regex-ver<version>-LargeFont.json`。特殊变体在版本号后追加 PascalCase 后缀，标准版沿用无后缀文件名。正则修复按两段式版本递增。
- 同一个正则版本可包含多个变体，统一放在 `regex/ver<version>/`，共用资源 ID、版本、Tag、Release 和发行说明。各变体有独立的变体 ID、文件、字节大小和 SHA-256。入库文件与原件逐字节一致。
- 正则版本与预设版本可多对多兼容。仅登记已确认的预设资源 ID 和版本，两种变体共用兼容记录时在正则版本上登记，存在差异时记录适用变体。修复旧版正则或升版时，按实际核验结果记录兼容性。
- 修改正式资源时，保留原始 JSON 数据结构、未知字段和未涉及的内容。按任务范围增量修改，禁止擅自重写或整体格式化。
- 公开任何预设、正则或历史文件前，必须取得 Owner 对该文件和版本的明确批准。草稿、备份、未获批准的历史文件及测试材料不得纳入公开提交或发布附件。

## 目录与发布

- `catalog.json` 是独立的内容资源索引，协议版本由 `schemaVersion` 表示。它不沿用 Hub Extension Package v1。资源版本与索引协议版本独立维护。
- 仅登记经 Owner 批准、实际公开且已验证的资源。录入前核对版本、资源路径、文件大小和最终公开字节的 SHA-256，并根据实际验证记录登记兼容关系。禁止伪造数据、添加占位记录或将未发布资源标为可用。
- 资源版本以字符串保存。索引按资源和版本归并变体，每个变体登记实际附件身份，客户端可将变体各自列为一个选项。没有确认兼容关系的已发布正则可以独立展示，不能作为某个预设的兼容推荐。
- `variants[].name` 保存 Owner 确定的完整中文展示名，客户端直接读取。不得根据英文文件名或 Release Title 推断展示名，也不得为显示名称修改原始 JSON 的 `scriptName`。
- Release Notes 由 Owner 提供并确认。公开资源或创建发行 Tag 前，须取得明确发布批准。先在草稿 Release 核验实际附件名称、ID、大小和 SHA-256，公开后再验证下载路径及字节，最后更新索引。若 GitHub 改写附件名且影响预期下载方式，停止发布，由 Owner 确认。
- 正式 Release 禁止静默替换附件。通常通过发布新版本更正；刚发布且尚未广泛分发的验收阶段，只有得到 Owner 明确授权才可撤回并重新发行同一版本。保留真实贡献记录和既有版权归属。

## 文档维护

- 修改项目文档前，完整阅读原文和本文件，确认原文用途、读者、结构、写法、技术详细程度与历史范围。默认增量维护，保留有效说明和真实历史。
- `docs/EVOLUTION.md` 只记录经确认的功能和设计演变。根据 Owner 核准的资料写明适用版本，禁止推测历史或追溯改写历史设计、审计、测试与验收结论。
- 大规模删除、历史内容迁移、文档用途改变或全文重写前，先向 Owner 报告并取得批准。为 Codex 编写维护任务时，明确要求遵守本文件及 MieMie 官方文档维护规则。

## 身份与授权

- SheepSheep 是 Founder / Project Initiator 与产品作者。SheepSheepLab 是官方 GitHub 开发、维护与发布命名空间。官方仓库为 `https://github.com/SheepSheepLab/MieMie-Presets`。
- 按本仓库实际贡献记录保留 Contributor 的 Git 作者、PR、贡献记录、署名与版权。禁止把 Contributor 自动加入产品作者字段、改署其贡献，或从其他项目沿用 Contributor 名单。
- 修改作者、维护方、贡献者、仓库、发行身份、许可或版权信息前，核对本项目现有文档、适用的元数据、Git 历史、原始来源及实际授权范围。身份模型以 MieMie Hub 的 BRAND / README 为优先参考。发现冲突时交由 Owner 确认。资源授权条款由 Owner 确定，分别核对预设文本、正则及可能包含的代码。
- 本仓库采用 CC BY-NC-SA 4.0 授权 SheepSheep 有权授权的原创预设和正则，包括适用的文本、配置、正则表达式和内嵌 JavaScript、HTML、CSS。Copyright © 2026 SheepSheep 仅覆盖其原创贡献。保留官方 LICENSE 正文，未经 Owner 批准不得修改适用许可或版权声明。
- 分享二创内容时，依据许可保留 SheepSheep 的原作署名、来源与许可信息并注明修改。二创作者可为新增原创内容署名。保留第三方署名、版权和许可；平台 @ 提及为自愿做法，不增设许可条件。
- 每份新资源发行前，核对原件、第三方来源、授权证据和既有声明，并静态检查内嵌代码的外部通信、动态执行及对宿主的影响。发现来源不明、许可冲突或安全疑点时，停止正式发行并报告 Owner。不得通过删改声明或正则内容绕过审核。
- 品牌、Logo、角色形象和独立的品牌视觉资产按各自的授权管理。真实来源说明应避免暗示官方认可。其他 MieMie 项目的软件继续适用各自许可证。

## Git 预检与隐私

- 每次提交、推送、打标签或发布前，检查 Git 配置、环境变量和实际 Author / Committer。Owner 提交必须使用 `SheepSheep <331468872+SheepSheepLab@users.noreply.github.com>`。使用经 Owner 授权的 SSH 签名密钥签名，签名失败时停止。
- Git 推送必须使用 `git@github.com:SheepSheepLab/MieMie-Presets.git`。检查实际 fetch / push 地址及 SSH 认证身份，禁止用 HTTPS 或 PAT 代替 SSH 推送。
- 用明确路径暂存文件。逐项审计暂存内容、实际提交对象、待推送记录和发布材料，确保没有凭据、私钥、私人身份信息、本地路径、Codex 工作记录、缓存、备份或未经授权的资源。首次提交必须来自干净仓库。
- 检查失败时停止并报告 Owner。未经 Owner 授权，禁止重写历史、强制推送或发布。推送后核对远端文件、Commit SHA 和 GitHub Verified 状态。
