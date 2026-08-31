# 演示后台 AI 助手续作 Prompt

复制给 Cursor。官网 V2 / 官网 AI **不要改**（继续 fixture）。本文件只做管理端演示租户 105。

执行前阅读：

- `docs/Demo方案/README.md`（实现进度）
- `docs/Demo方案/03-AI演示问题与期望回答.md`
- `xm-im-erp/docs/临时文件/演示后台-AI业务助手真实问答验证.md`
- `xm-im-erp/Test/demo-xinghai/`

## 已完成（不要回退）

- 造数：`script/seed-demo-xinghai.bat`，租户 105，`erpdemo` / `123456789`。不对租户 100 造数。含 `seed_sla_risk_tickets`（SLA 3 张）。
- 入口：顶栏「AI业务助手」、`/erp/home` 应收账龄「问 AI」自动发送。顶栏「演示数据」角标。
- 经营查询读真实表；60 问 API 已 60 PASS。回答不点名「租户 105」。
- 查询代码不写死锐创/林晓雨等专名（测试问句可以有）。
- 写闭环 7 条：超期跟进、催款、锐创报价、采购申请、调拨、赶工、工单进度。脚本 `write_loop_test.py`。批量跟进必须 `save()`，禁止 `create()`。

## 本轮剩余（按序）

1. 能补且不打乱 ¥682,400 / ¥1,268,600 的口径再补；不能补的继续如实说（保修无表、采购样本不足、锐创未到期应收未加等）。
2. 回归：`python Test/demo-xinghai/biz_assistant_test.py` 与 `write_loop_test.py`，必要时 `verify_demo.py`。改完后端必须 `script/start-backend.bat`。

## 禁止

- 改官网 AI fixture、改线索租户 4、对租户 100 seed。
- 确认跟进时调用会清掉原计划跟进的 API。
- 在生产查询代码里写死 Demo 专有名词。
