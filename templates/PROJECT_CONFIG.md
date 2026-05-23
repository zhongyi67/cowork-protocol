# <项目名> 项目配置

## 项目坐标
- REPO_PATH: ~/Desktop/<项目名>
- REPO_URL: git@github.com:<user>/<项目名>.git
- BRANCH: main

## 服务器
- SERVER: <user@ip / 或 N/A>
- RELEASES_DIR: <路径 / 或 N/A>
- CURRENT_SYMLINK: <路径 / 或 N/A>
- SERVICE_PROCESS_PATTERN: <匹配模式 / 或 N/A>
- HEALTH_VERSION_URL: <URL / 或 N/A>
- PUBLIC_SITE: <URL / 或 N/A>

## 命令
- BUILD_CMD: <构建命令 / 或"待 M0 P0.1 决定">
- TEST_CMD: <测试命令>
- TYPECHECK_CMD: <可选>
- SMOKE_CMD: <可选>
- DEPLOY_CMD: bash scripts/deploy-prod.sh （M1 实现）
- ROLLBACK_CMD: bash scripts/rollback.sh （M1 实现）

## 文档
- HANDOFF_DOC: docs/DEVELOPMENT_HANDOFF.md
- TASK_BOARD: docs/GPT_HANDOFF.md
- AUTHORITATIVE_ROADMAP: docs/PRODUCT_ROADMAP.md

## 巡检范围
- src/
- scripts/
- docs/

## 红牌通讯
Codex 在 commit message 加 `[RED-CARD #N]` 并在 handoff 节专门一节说明。
