```mermaid
flowchart TD
    st([开始]) --> op[处理框]
    op --> cond{判断框}
    cond -- 是 --> io[/输入输出/]
    io --> e([结束])
    cond -- 否 --> sub1[[子流程]]
    sub1 --> op
```
