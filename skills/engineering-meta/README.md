# engineering-meta

工程化元技能。在成熟领域系统中保护概念拓扑、上下文完整性和执行门禁。

## 干什么

- **Domain Contract Gate**：防止术语漂移、概念污染、层级混淆
- **Context Pack Gate**：确保每次执行前加载最小无损上下文
- **Entry Router**：分类当前项目状态，路由到正确的执行路径
- **Learning Loop**：每次执行结束记录 agent_mistake / concept_drift / next_rule

## 在 content-engine 中的作用

author-fit-engine 生成稿子时，engineering-meta 作为前置合约检查：
- 五维材料是否被当成文章模板？
- 三层拟合是否被跳过？
- 三维检验是否变成最后喷漆？
- Agent 是否在用户验收前进入执行？

不通过合约，不进入生成。
