# cowork-protocol · "我 + Claude + Codex" 三方协作模式

> 这个仓库定义并存档"我 + Claude + Codex"三方协作的完整协议。
> 任何新项目、任何新对话、任何新机器，读这一份就能进入状态。

## 立刻使用

### A. 新对话恢复协作（最常用）

打开新 Claude 对话，粘下面这一句（替换 `<...>` 占位）：

```
读 https://raw.githubusercontent.com/<your-user>/cowork-protocol/main/驱动计划.md
项目在 ~/Desktop/<项目名>。
<场景：新项目 / 接管已有 / 恢复进行中>
```

Claude 读完驱动计划自动进入状态、识别模式、汇报现状、主动开聊。

### B. 全新项目从零启动

```
读 https://raw.githubusercontent.com/<your-user>/cowork-protocol/main/驱动计划.md
新项目 <名>，想法是 <一句话痛点>。
```

Claude 走 Phase 0-2（发现 + 拆任务），然后让 Codex 走 P-init 建仓库 + 协议。

### C. 接管已有代码（没装协议）

```
读 https://raw.githubusercontent.com/<your-user>/cowork-protocol/main/驱动计划.md
项目在 ~/Desktop/<项目名>，代码已存在但没装协议。
按"模式 C 接管已有代码"装协议四件套，跳过 Phase 1-2。
```

## 仓库内容

```
cowork-protocol/
├── README.md                          ← 本文件
├── 驱动计划.md                         ← 主激活协议（Claude 必读）
└── templates/                         ← 新项目复制即用的模板
    ├── OPERATING_PROTOCOL.md          ← 项目协议正文
    ├── PROJECT_CONFIG.md              ← 项目变量配置
    ├── GPT_HANDOFF.md                 ← 任务清单
    ├── PRODUCT_ROADMAP.md             ← 产品路线
    └── DEVELOPMENT_HANDOFF.md         ← 接力日志
```

## 协议核心

- **用户 + Claude = 老板**，平级
- **Codex = 执行器**，听派单
- 用户提需求 → Claude 整理 + 巡检 + 商量 + 写任务 + 审计
- Codex 干活 → push `[review-ready]` + 证据
- Claude PASS / BLOCK 自动循环
- 只有 4 张红牌打扰用户：产品方向 / 真实写入首次 / 设计分歧 / 三端无法对齐

完整规则见 `驱动计划.md`。

## 本地备份

```bash
git clone https://github.com/<your-user>/cowork-protocol.git ~/Desktop/cowork-protocol
```

每个新项目可以从 `templates/` 复制 5 个模板到 `<新项目>/docs/`。
