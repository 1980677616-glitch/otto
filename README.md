# 青少年网络使用心理对话分析智能体

一个用于“心理学对话分析 / 青少年戒网瘾”主题的专业智能体应用。项目采用纯静态页面，可部署到免费的 GitHub Pages；页面代码预置阿里云百炼 OpenAI 兼容调用方式，默认模型为 `qwen3.7-plus`。

## 功能

- 青少年网络过度使用对话分析
- 风险评分、情绪线索、睡眠影响、冲动控制与亲子冲突提取
- 动机性访谈风格回应
- 家庭沟通与干预方向建议
- 自伤、自杀、暴力、虐待等高危线索安全升级提醒
- Markdown 分析报告导出

## 模型接入

页面支持三种模式：

- `前端演示模式`：不调用外部接口，适合 GitHub Pages 公开展示。
- `百炼直连模式`：浏览器直接请求阿里云百炼兼容接口，API Key 只保存在当前浏览器会话中。公开演示不建议使用个人 Key。
- `后端代理模式`：推荐正式展示方式。前端请求你自己的代理服务，由代理服务在服务端安全调用百炼。

默认接口：

```text
https://dashscope.aliyuncs.com/compatible-mode/v1/chat/completions
```

如果你的百炼控制台要求使用业务空间专属域名，可在页面“模型”设置中改为：

```text
https://<WorkspaceId>.cn-beijing.maas.aliyuncs.com/compatible-mode/v1/chat/completions
```

默认模型：

```text
qwen3.7-plus
```

官方参考：

- 阿里云百炼 OpenAI 兼容接口：https://help.aliyun.com/zh/model-studio/compatibility-of-openai-with-dashscope
- 阿里云百炼模型列表：https://www.alibabacloud.com/help/zh/model-studio/models

## 本地预览

在项目根目录运行：

```powershell
python -m http.server 8080 -d docs
```

然后访问：

```text
http://localhost:8080
```

## GitHub Pages 部署

本机尚未登录 GitHub CLI。登录后可在本目录执行：

```powershell
gh auth login
git init
git branch -M main
git add .
git commit -m "Add Qwen teen internet overuse psychology agent"
gh repo create qwen-teen-net-addiction-agent --public --source=. --remote=origin --push
```

仓库创建后，GitHub Actions 会使用 `.github/workflows/pages.yml` 自动部署 `docs/` 目录。部署完成后，Pages 地址通常为：

```text
https://<你的GitHub用户名>.github.io/qwen-teen-net-addiction-agent/
```

如首次部署未启用 Pages，在仓库 Settings -> Pages 中选择 GitHub Actions 作为 Source，再重新运行工作流。

## 边界声明

本应用用于心理教育、学校心理辅导辅助和科研演示，不提供医学诊断，不替代心理咨询、精神科评估或急救服务。若对话中出现自伤、自杀、暴力、虐待或明显失控风险，应立即联系监护人、学校心理老师、当地急救或危机干预资源。
