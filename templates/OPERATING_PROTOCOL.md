# <项目名> 协作运作协议

> 本文件是项目内嵌的协作协议正文，与项目同生命周期。
> 上游：https://github.com/<your-user>/cowork-protocol/blob/main/驱动计划.md
> 如有冲突，以本项目本文件为准（项目自治）。

## 角色

- **用户 + Claude = 两个老板**，平级
- **Codex = 执行器**，听派单

## 总循环

```
用户提需求 → Claude 整理+巡检 → Claude↔用户商量 → Claude 写任务到 GPT_HANDOFF.md §4 → Codex 干活+push [review-ready] → Claude 审 PASS/BLOCK → Claude 巡检 → 回到商量
```

## 三端一致

`origin/main = 服务器 current = 本地 HEAD`，每次 PASS/BLOCK/加任务前核对。

服务器 N/A 阶段降级为 `local == origin`。

## Claude 自主权

直接拍板：PASS / BLOCK、超范围小改动判断、handoff 格式纠正、任务范围微调、部署/push/测试决策。

必须问用户的 4 张红牌：
1. 产品方向
2. 真实写入首次
3. 设计分歧 3 轮未过
4. 三端无法自动对齐

## Codex 红线

- 不准 `git push --force` / `--no-verify`
- 不准跳过测试或部署脚本直接 scp
- 不准客户端推导 "成功/已完成"
- 一改动一独立 commit，`feat|fix|docs|chore(scope):` 前缀

## [review-ready] 证据包（5 块）

每次 push `[review-ready] Px.y` 后在 `docs/DEVELOPMENT_HANDOFF.md` 追加节：

**A. 三方同步**：`git log -1` + `git log HEAD..origin/main` + ssh server check
**B. 验证退出码**：build / test / typecheck / smoke 各自 exit 0 + 用例数
**C. 功能验证**：调真实 API / 关键日志
**D. 数据库证据**：涉及写库时 SELECT 输出
**E. 自查 6 条**：边界 / 幂等 / 测试 / 接口 / 前端 / 同步

每条 ✅/❌ + 一句证据。

## Review 循环

- Codex push [review-ready] → 停下等（除非夜班）
- Claude PASS / BLOCK Px.y round N
- 连续 3 轮未过 → 红牌 #3

## Claude 巡检面

每次 PASS 后扫：
- TODO / FIXME / XXX
- pending_backend / 占位 / 死按钮
- 接力文档承诺未兑现
- roadmap 缺口剩余
- 测试覆盖盲区
- 慢查询 / N+1
- 鉴权 / 注入 / SSRF
- 用户线上反馈

按 P 编号续写到 GPT_HANDOFF.md §4。**0 发现也明说**。

## 夜班模式

用户明示生效。不等 PASS，连续推。必停硬条件：真实写入边界 / build 不过 30 分钟修不好 / 三端 diverge / force push 诱惑 / 测试覆盖严重缺失。
