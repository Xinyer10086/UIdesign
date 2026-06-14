# 贡献指南

感谢你考虑为 AI UI Design Toolkit 做贡献！

## 如何贡献

### 报告问题

- 在 [Issues](https://github.com/Xinyer10086/UIdesign/issues) 提交
- 包含：使用的 Agent 类型、输入 prompt、实际输出 vs 期望输出

### 提交 Pull Request

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feat/your-feature`
3. 提交改动：`git commit -m "feat: 简洁描述"`
4. 推送到你的 Fork：`git push origin feat/your-feature`
5. 创建 Pull Request

### 开发规范

- SKILL.md 的 frontmatter description 应包含触发场景 + 负触发
- 参考文件使用英文路径和简洁模板
- 所有方法论文档使用简体中文
- 不要硬编码私有路径、API key 或个人资源
- 新增参考文件时更新 README.md 的文件结构树

### 提交信息格式

```
<type>: <简短描述>

- type: feat / fix / docs / refactor / test / chore
- 描述：中文或英文，不超过 50 字
```

## 本地验证

```bash
# 检查 SKILL.md frontmatter 格式
head -10 SKILL.md | grep "^name:\|^description:"

# 确认无中文路径引用
grep -r "UI效果图" --include="*.md" .
```
