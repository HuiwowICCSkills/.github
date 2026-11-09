# HuiwowICCSkills

国际法检索、ICC 模拟法庭与法律研究工具集合。

本组织以“一个站点，一个 skill”为基本组织方式：每个来源尽量独立成仓，保留自己的检索入口、访问边界、运行脚本、测试和验证记录；聚合器只负责跨来源编排，不把不同站点的访问逻辑混在一起。

> 组织内仓库均为公开仓库；所有 skill、测试和来源说明可直接查看。

## 我们在做什么

| 方向 | 内容 |
|---|---|
| 国际刑法（ICL） | ICC Legal Tools、ICC 官网、Lexsitus/CLICC、OPIL（MPIL/ORIL-ICL）、ICRC、ICD、ICTY/ICTR/IRMCT 判例与记录 |
| 一般国际法（GIL） | ICJ、ECHR/HUDOC、UNTS、联合国文件、CILRAP/FICHL、国际法博客与期刊元数据 |
| ICC 模拟法庭 | 书状写作、审校、脚注核验与引证校正 |
| 检索编排 | `icl-research`、`gil-research` 两个聚合器，以及来源目录和来源开关控制台 |
| 人工补检 | 登录、订阅全文、UCR/UNTS/ODS 等自动路径无法覆盖的交接流程 |
| 获取与会话 | GDUFS 统一认证会话、HeinOnline 机构访问、EJIL: Talk!、Anna’s Archive/Breadl 图书链路 |

## 仓库地图

### 核心工具

- [`InternationalLawRetrieval`](https://github.com/HuiwowICCSkills/InternationalLawRetrieval)：国际法检索工具本体，包含 `icl-research`、`gil-research`、`international-law-manual-research` 和来源目录。
- [`InternationalLawSourceConsole`](https://github.com/HuiwowICCSkills/InternationalLawSourceConsole)：本地来源开关控制台，读取外部 `source-catalog.json`。
- [`ICCMootCourtWorkflow`](https://github.com/HuiwowICCSkills/ICCMootCourtWorkflow)：ICC 模拟法庭书状写作工作流，内含 `icc-moot-memorial-writing` 与 `icc-moot-footnote-verifier`；脚注核验与最小校正为默认步骤，交付时附核验报告和校正记录。

### 国际刑法单站技能

- [`LegalToolsSearcher`](https://github.com/HuiwowICCSkills/LegalToolsSearcher)：ICC Legal Tools Database。
- [`ICCSearcher`](https://github.com/HuiwowICCSkills/ICCSearcher)：ICC 官网、案件页与文件。
- [`LexsitusSearcher`](https://github.com/HuiwowICCSkills/LexsitusSearcher)：Lexsitus/CLICC 评注、判例记录与要件。
- [`OPILSearcher`](https://github.com/HuiwowICCSkills/OPILSearcher)：Oxford Public International Law（MPIL、ORIL、ORIL-ICL）。
- [`ICRCSearcher`](https://github.com/HuiwowICCSkills/ICRCSearcher)：ICRC IHL 数据库与 Customary IHL。
- [`ICDSearcher`](https://github.com/HuiwowICCSkills/ICDSearcher)：International Crimes Database。
- [`IRMCTCldSearcher`](https://github.com/HuiwowICCSkills/IRMCTCldSearcher)：IRMCT Case Law Database。
- [`UCRSearcher`](https://github.com/HuiwowICCSkills/UCRSearcher)：IRMCT Unified Court Records 公开 recent-filings。
- [`ICTYSearcher`](https://github.com/HuiwowICCSkills/ICTYSearcher) / [`ICTRSearcher`](https://github.com/HuiwowICCSkills/ICTRSearcher)：ICTY/ICTR 官网与公开遗产页面。

### 一般国际法单站技能

- [`ICJSearcher`](https://github.com/HuiwowICCSkills/ICJSearcher)：国际法院 Document Search 与判决 PDF。
- [`HUDOCSearcher`](https://github.com/HuiwowICCSkills/HUDOCSearcher)：欧洲人权法院 HUDOC。
- [`UNTSSearcher`](https://github.com/HuiwowICCSkills/UNTSSearcher)：联合国条约集 MTDSG 标题目录。
- [`UNDocsSearcher`](https://github.com/HuiwowICCSkills/UNDocsSearcher)：UNITE 与 ODS 联合国文件。
- [`CILRAPSearcher`](https://github.com/HuiwowICCSkills/CILRAPSearcher)：CILRAP 主站与 FICHL 板块。
- [`OpinioJurisSearcher`](https://github.com/HuiwowICCSkills/OpinioJurisSearcher) / [`IntlLawObserverSearcher`](https://github.com/HuiwowICCSkills/IntlLawObserverSearcher)：国际法博客。

### 获取、会话与图书

- [`gdufs-auth-session`](https://github.com/HuiwowICCSkills/gdufs-auth-session)：广东外语外贸大学统一认证与图书馆 VPN 会话。
- [`HeinOnlineSearcher`](https://github.com/HuiwowICCSkills/HeinOnlineSearcher)：HeinOnline 机构检索与分节 PDF。
- [`EJILTalkSearcher`](https://github.com/HuiwowICCSkills/EJILTalkSearcher)：EJIL: Talk!。
- [`AnnaBreadlBookFinder`](https://github.com/HuiwowICCSkills/AnnaBreadlBookFinder)：Anna’s Archive 书目与 Breadl 下载候选。

## 设计原则

1. **一站点一 skill。** 单站技能不共享隐式运行时；每个仓库有自己的 `SKILL.md`、`run.ps1`/`run.sh`、依赖、测试和 `doctor`。
2. **先一手材料，再评注。** 判决、条约、官方文件与评注分层报告；摘要、元数据和 headnote 不冒充全文。
3. **边界写清楚。** 每个 skill 明确说明 `metadata`、`full text`、`fallback`、`degraded`、`auth-required` 等状态，不把访问失败当成“没有资料”。
4. **凭据不落仓库。** 机构登录态保存在用户目录，不写入仓库、报告或引用；需要登录时走人工交接。
5. **可复现。** 关键来源保留 endpoint、验证日期、请求参数、哈希和已知限制；变更后运行离线测试和实网自检。

## 快速开始

```powershell
git clone https://github.com/HuiwowICCSkills/InternationalLawRetrieval.git "$env:USERPROFILE\Documents\InternationalLawRetrieval"
Copy-Item -Recurse -Force `
  "$env:USERPROFILE\Documents\InternationalLawRetrieval\skills\*" `
  "$env:USERPROFILE\.codex\skills\"

python -X utf8 -m pip install -r "$env:USERPROFILE\Documents\InternationalLawRetrieval\skills\icl-research\scripts\requirements.txt"
python -X utf8 -m pip install -r "$env:USERPROFILE\Documents\InternationalLawRetrieval\skills\gil-research\requirements.txt"
```

ICC 书状工作流单独安装：

```powershell
git clone https://github.com/HuiwowICCSkills/ICCMootCourtWorkflow.git "$env:USERPROFILE\Documents\ICCMootCourtWorkflow"
Copy-Item -Recurse -Force `
  "$env:USERPROFILE\Documents\ICCMootCourtWorkflow\skills\*" `
  "$env:USERPROFILE\.codex\skills\"
python -m pip install lxml
```

每个单站 skill 可单独克隆到 `~/.codex/skills/<SkillName>`；具体命令见对应仓库的 `README.md`。

## 外部通用技能

`multi-search-engine`、`web-access`、`agent-browser`、`spider-mind` 是通用联网/浏览器能力，不随本组织的国际法检索仓库打包，需从各自上游单独获取。来源目录中的 `local-skills` 分组只记录本机能力，不代表组织仓库包含这些项目。

## 当前规模

- 24 个公开仓库：23 个检索仓库 + 1 个 ICC 书状工作流仓库（另加 `.github` 组织主页仓库）
- 来源目录 37 项，默认启用 34 项
- 覆盖 ICL、GIL、国际人道法、国际人权法、联合国条约与文件、机构访问和图书获取

最后更新：2026-11-09
