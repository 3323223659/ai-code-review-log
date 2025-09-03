# ai-code-review-log 代码评审日志仓库（Log Repo）

本仓库用于存放由 AI 代码评审 SDK 生成的“评审日志/记录”。日志由目标代码仓库的 GitHub Actions 在每次 Push/PR 触发后自动写入本仓库，便于统一留痕与回溯。

## 日志来源

- 在“被评审的目标仓库”中配置 GitHub Actions 工作流（参见主仓库 README 的完整示例）。
- 工作流下载已发布的 `openai-code-review-sdk-1.0.jar`，运行主类 `main` 方法，并将评审结果提交到本仓库。

## 使用与配置（简要）

- 在目标仓库 `Settings -> Security -> Actions -> Secrets and variables -> Actions` 配置以下 Secrets：
  - `CODE_REVIEW_LOG_URL`：指向本日志仓库的 Git 远程地址（需具备写入权限）
  - `CODE_TOKEN`：用于向本仓库提交的 Token（建议最小必要写权限）
  - 其余 项目信息 / ChatGLM / 微信 / 邮件相关 Secrets 按需配置
- 触发时机：通常在 `push` 或 `pull_request` 到指定分支时自动运行

## 如何查看

- 浏览本仓库的提交历史和变更内容，即可查看每次评审记录
- 若工作流将报告写入特定目录（如 `logs/`），可直接进入目录查看

## 完整说明与工作流示例

请前往主仓库查看完整使用文档（含工作流 YAML、Secrets 明细、故障排查等）：

- AI 代码评审 SDK 使用说明：`https://github.com/3323223659/ai-code-review`

---

安全提示：请为用于提交本仓库的 Token 设置“最小必要权限”，并避免在日志中包含敏感信息。
