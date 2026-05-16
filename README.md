# Minecraft Modder — Claude Code Skill

NeoForge 模组开发的 Claude Code Skill，提供项目初始化、物品/方块注册、数据生成、事件处理、Mixin 等模组开发辅助。

## 安装

将本仓库克隆到你的 Claude Code skills 目录：

```bash
git clone https://github.com/Gu-ZT/minecraft-modder-skill.git ~/.claude/skills/minecraft-modder
```

或作为项目级 skill 放入 `.claude/skills/` 目录。

## 触发条件

当你向 Claude Code 提出以下类型的问题时会自动激活此 skill：

- 创建 NeoForge 模组项目
- 添加物品、方块、实体、合成表
- 处理模组事件
- 配置数据生成
- 调试模组崩溃

## 特性

- 默认基于 **NeoForge 26.1.2 + Minecraft 26.1.2**
- 优先使用 **Datagen** 生成语言文件、模型、配方、战利品表等
- 推荐使用 [AnvilLib](https://lib.anvilcraft.dev/) 模组开发辅助库（16 个可选模块）
- 项目骨架基于 [NeoForge 模板仓库](https://github.com/Gu-ZT/neoforge-template-mod)

## 推荐 MCP 服务

以下 MCP 服务可改善使用体验，按需配置到 `claude_desktop_config.json` 或项目 `.mcp.json`。

### WebScraper（网页抓取）

> [!TIP]
> 如果你使用的不是 Claude Code 官方模型，`WebFetch` 工具可能不可用。配置此服务以启用网页抓取能力。

```json
{
  "mcpServers": {
    "webscraper": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-webscraper"
      ]
    }
  }
}
```

> [!IMPORTANT]
> **重要：** 安装后，需运行 `npx playwright install chromium` 来手动安装浏览器依赖。

### JetBrains IDEA（IDE 集成）

```json
{
  "mcpServers": {
    "Jetbrains IDEA": {
      "type": "stdio",
      "env": {
        "IJ_MCP_SERVER_PORT": "64342"
      },
      "command": "${IDEA_PATH}\\jbr\\bin\\java",
      "args": [
        "-classpath",
        "${IDEA_PATH}\\plugins\\mcpserver\\lib\\mcpserver-frontend.jar;${IDEA_PATH}\\lib\\util-8.jar;${IDEA_PATH}\\lib\\intellij.libraries.kotlinx.coroutines.core.jar;${IDEA_PATH}\\lib\\intellij.libraries.ktor.client.cio.jar;${IDEA_PATH}\\lib\\intellij.libraries.ktor.client.jar;${IDEA_PATH}\\lib\\intellij.libraries.ktor.network.tls.jar;${IDEA_PATH}\\lib\\intellij.libraries.ktor.io.jar;${IDEA_PATH}\\lib\\intellij.libraries.ktor.utils.jar;${IDEA_PATH}\\lib\\intellij.libraries.kotlinx.io.jar;${IDEA_PATH}\\lib\\intellij.libraries.kotlinx.serialization.core.jar;${IDEA_PATH}\\lib\\intellij.libraries.kotlinx.serialization.json.jar",
        "com.intellij.mcpserver.stdio.McpStdioRunnerKt"
      ]
    }
  }
}
```

> [!IMPORTANT]
> **重要：** `${IDEA_PATH}` 替换为本地 IntelliJ IDEA 安装路径，例如 `C:\\Program Files\\JetBrains\\IntelliJ IDEA 2024.1`。

## 许可证

* MIT
