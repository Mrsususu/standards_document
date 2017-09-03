# Commit Message Style

## Commit message 的作用

格式化的Commit message，有几个好处。

1. 提供更多的历史信息，方便快速浏览。
2. 可以过滤某些commit（比如文档改动），便于快速查找信息。

## Commit message 的格式

每次提交，Commit message 都包括三个部分：Header，Body 和 Footer。

```
<type>(<scope>): <subject>
// 空一行
<body>
// 空一行
<footer>
```

### 提交信息类型前缀

- feat：新功能（feature）
- fix：修补bug
- docs：文档（documentation）
- style： 格式（不影响代码运行的变动）
- refactor：重构（即不是新增功能，也不是修改bug的代码变动）
- pref: 提升性能
- test：增加测试
- chore：构建过程或辅助工具的变动

**example**

```bash
feat(view): add Calendar Component
```
