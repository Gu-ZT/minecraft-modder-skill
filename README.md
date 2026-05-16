## 使用

### 添加 MCP 服务

#### IntelliJ IDEA MCP

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
> **重要：** 请将 `${IDEA_PATH}` 替换为你本地 IntelliJ IDEA 的安装路径，例如 `C:\\Program Files\\JetBrains\\IntelliJ IDEA 2024.1`。

#### mcp-webscraper

如果你使用的并非`Claude Code`官方的模型，可能无法使用`WebFetch`等工具，建议你配置以下MCP服务以获取更好的使用体验：

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
