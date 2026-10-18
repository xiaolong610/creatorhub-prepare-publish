# CreatorHub 发布准备 Skill

让 Codex 把本地图片、视频和随附文案填入 CreatorHub 的多平台发布页，保留页面，由你检查并提交。

**默认不点击“加入发布队列”。该按钮可能立即触发发布，并非保存草稿。**

这是一个操作流程型 Skill，不是自动发帖程序，也不包含 CreatorHub 服务本身。

## 能做什么

- 读取指定文件夹或 ZIP 中的素材和文案。
- 按自然编号排列图集，提取标题、正文和标签。
- 填写前默认移除标题、正文和话题中的所有星号 `*`，避免 Markdown 标记被带入；例如 `**重点**` 变为 `重点`。原始素材和文案文件不改动。
- 核对平台和账号，填写图片或视频发布表单。
- 按当前页面说明处理话题格式、标题限制和发布时间。
- 为不同平台保留独立页面，提供截图供检查。
- 默认停在提交之前，遇到结果不明确时不重复发布。

## 使用条件

- 能读取本地文件并操作浏览器的 Codex 环境。
- 当前实现使用 `mcp__cua_repl` 浏览器接口；不提供该接口的运行环境需要适配。
- 已运行并可访问的 CreatorHub，默认地址为 `http://127.0.0.1:8000/#publish`。
- 目标平台已登录；登录或平台验证需要用户处理。

已实际验证：Windows 上的抖音、小红书图集表单准备，停在提交前。其他平台及视频流程需以当前页面能力验证。CreatorHub 同名项目可能存在不同版本，请确认页面结构匹配。

## 安装

将本仓库复制到 Codex 的技能目录，目录结构如下：

```text
~/.codex/skills/creatorhub-prepare-publish/
├── SKILL.md
└── agents/
    └── openai.yaml
```

如果设置了 `CODEX_HOME`，使用该目录下的 `skills/`。安装后在新聊天中确认技能可见。

Windows PowerShell 示例（要求 Git 可用）：

```powershell
git clone https://github.com/xiaolong610/creatorhub-prepare-publish.git "$env:USERPROFILE\.codex\skills\creatorhub-prepare-publish"
```

目录已存在时先比较内容，不要直接覆盖自己的配置。

## 使用

```text
使用 $creatorhub-prepare-publish，把 D:\materials\example-post.zip
中的素材和文案填入 CreatorHub 的抖音及小红书指定账号。
图片按编号排序，每个平台保留独立发布页。
停在“加入发布队列”之前，由我检查并点击。
```

也可以说：“按上次流程，准备这个素材包，先别提交。”请提供素材位置、平台和目标账号。

推荐素材包：

```text
example-post.zip
├── 01.png
├── 02.png
├── 03.png
└── 文案.txt
```

`文案.txt` 示例：

```text
【标题】
今天的创作记录

【正文】
这里放准备发布的正文。

【标签】
#创作记录 #日常分享
```

## 使用边界

- 本技能只填写表单，不代表已经提交或发布成功。
- 当前标签页的文件选择不保证在刷新、关闭或重启后保留。
- 不包含账号凭证、Cookie、个人素材或本机专属路径。
- 不修改代理、登录和风控配置，不绕过平台验证。
- 请发布自己有权使用的素材，并遵守目标平台规则。

## 贡献

欢迎通过 Issue 或 Pull Request 提交页面兼容性问题及改进。报告时注明系统、目标平台和脱敏后的页面现象；不要上传账号凭证、Cookie 或私人素材。

## 许可

[MIT](LICENSE)。CreatorHub 及各平台的名称和服务属于各自权利人；本项目不代表其官方产品。
