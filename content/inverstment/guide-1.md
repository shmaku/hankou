---
title: "我的流程图"
data: 2025-12-14
mermaid: true
---

```mermaid
flowchart TD
    st([开始]) --> op[处理框]
    op --> cond{判断框}
    cond -- 是 --> io[/输入输出/]
    io --> e([结束])
```
