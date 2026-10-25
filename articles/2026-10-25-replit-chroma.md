# 你的 Chroma Cloud 要关了：Replit 收了向量库顶流，开源还在

![Chroma joins Replit](./assets/2026-10-25-replit-chroma/chroma-joins-replit-card.jpg)

你要是做过一点 RAG、agent 记忆，多半装过 **ChromaDB**——本地 `pip install`，几行代码把向量塞进去，再问回来。

今天这条新闻，不是「又一个向量库被收购」的通稿。按 [trychroma 这篇公告](https://www.trychroma.com/blog/chroma-joins-replit)：Chroma **已签署确定性协议**，加入 **Replit**。团队要去做 Replit 口中「self-driving company」的企业 **context / memory 层**。

开源还活着。托管 Cloud，开始倒计时。

---

## 先说人话：这跟你差在哪

分两拨人。

**还在本地 / 自托管跑 ChromaDB 的人**  
你今天的 `docker`、`pip`、自己的机房，不会因为这篇公告自动停。公告写得很直：开源月下载约 **600 万**，GitHub stars 接近 **3 万**；还把私有仓里更多代码推进了 **Apache 2.0** 仓库，Replit 也会继续往开源回贡献。你的痛点不是「库突然消失」，而是后面发版节奏、谁拍板、和企业版怎么分叉——这些公告没写死日历。

**把生产写在 Chroma Cloud 上的人**  
这才是真钩子。托管服务会在大约 **60 天**里收掉。不是「建议迁移」，是写死了两道闸——写先停，读再停。日历见下表。

普通人如果只是跟教程玩过一把本地 demo，可以当热闹看。真正在云端塞过客户数据、embedding、会话记忆的团队，今天就该开迁移工单。

---

## 公告里能核的硬货

动机写得很清楚：中段 2026 他们觉得下一跳在企业 context，做了 **Foundation**（自称在 BEAM memory 基准打到 SOTA），再叠上 Replit 的 agent 平台和规模化 GTM。Michele Catasta、Amjad Masad 早年投过 Chroma——熟人局合到一起，不是空降收购故事。

对开发者最要紧的，不是「self-driving company」这句口号，是下面这张时间表——数字来自官方 [Cloud wind-down](https://www.trychroma.com/cloud-wind-down) 页：

| 节点 | 日期 | 会发生什么 | 你至少要做完什么 |
| --- | --- | --- | --- |
| 写停 | **2026-11-22** | Cloud 变只读；不能再增删改 | 停掉/改道写入；开始导出并校验要留的数据 |
| 读停 | **2026-12-22** | 连读请求也不再服务 | 导出收尾；确认应用不再依赖 Cloud 端点；清掉/轮换凭证 |

中间那 30 天「还能读」不是安全垫——任何还在持续写入的业务，真正的硬截止是 **11 月 22 日**，不是 12 月 22 日。

开源侧再记三句：月下载 **6M**；stars 接近 **30k**；额外私有代码已 commit 进 Apache 2.0 仓，Replit 承诺继续贡献、并把它往企业 context 延伸。公告点名用过 ChromaDB 的客户包括 SpaceXAI、Mintlify、Krea、Paramount、Retool、Coreweave 等——那是产品叙事，不是 Cloud 付费用户数。

---

## 冷静一下：开源继续 ≠ Cloud 继续

**签了确定性协议，不等于交割细节都摊开。**  
价格、交割日、团队怎么并、产品何时嵌进 Replit Agent——公告没写。别把「signed definitive agreement」读成「一切已落地、新托管明天上线」。

**开源承诺是连续性故事，不是 SLA。**  
多塞私有代码、Replit 回贡献，听起来诚恳；发版节奏、兼容性承诺、谁说了算，公告没有排期表。自托管能跑，≠ 有人替你值夜班。

**没有写「Replit 托管版立刻接盘」。**  
wind-down 页只指向迁移到「另一个 Chroma 部署或其他数据库」，加一个 `support@trychroma.com`。Cloud 客户别赌「过两周会有官方 1:1 替身」。

**向量库赛道不会因为这一笔收购变成一家通吃。**  
公告里的 95% 下载占比是他们早期估算、且是过去时；Foundation 的 BEAM SOTA 是自家口径。别外推成「记忆层已被 Replit 独占」。

兴奋可以留给 Replit × context 的故事。生产侧，把 **11/22 写停** 记进日历。

---

## 想动手的话

1. 查清：你的写入是不是打在 Chroma Cloud 上——是的话，立刻排迁移。  
2. 按官方时间线：写入在 **11/22** 前改道；导出与读依赖在 **12/22** 前清干净。  
3. 自托管 / 开源用户：继续跟 [Chroma 公告](https://www.trychroma.com/blog/chroma-joins-replit) 和 Apache 2.0 仓的实际 commit，别只听口号。  
4. 选型 agent 记忆层：把「托管会不会突然收摊」写进风险评估——这次就是现成案例。
