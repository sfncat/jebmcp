[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/flankerhqd-jebmcp-badge.png)](https://mseep.ai/app/flankerhqd-jebmcp)

A quick-and-dirty MCP server&Plugin for JEB Pro.
Tested on Cline & Cursor & RooCode.

1. 安装uv
2. git clone 代码 
3. cd jebmcp
4. 安装依赖 uv --directory jebmcp/jeb-mcp/src/jeb_mcp run server.py
5. 打开jeb,F2选择MCP.py
6. 在vscode的cline中 Configure MCP Servers
7. MCP的json修改 mcp的目录
      "args": [
        "--directory",
        "/home/kali/workspace/github/jebmcp/jeb-mcp/src/jeb_mcp",
        "run",
        "server.py"
      ],

8. 在cline中连接jeb server,正常应该可连上.Done
9. 告诉ai apk的绝对路径,要分析的类,函数名和要求

其它：
修改jeb
1. jvmopt.txt
2. jeb-engines.cfg 关闭加载apk的提示框

Reference: https://github.com/mrexodia/ida-pro-mcp

# Installation

## Requirements
```
Python >= 3.11
uv: https://docs.astral.sh/uv/getting-started/installation/
```
## Usage
- COPY the src/jeb_mcp/MCP.py to $JEB_INSTALLATION_DIR/scripts. Make sure the jython file is also present
- Choose and Start the script in JEB GUI (`File->Scripts->Scripts selector...`), check for desired output:
```bash
[MCP] Plugin loaded
[MCP] Plugin running
[MCP] Server started at http://127.0.0.1:16161
```
- Add this MCP server's config in cline/cursor/etc, as in the sample

# 安装
要求：
```
安装 python3.11及以上版本
安装 uv https://docs.astral.sh/uv/getting-started/installation/
```

# RooCode 使用方法：

1. 使用 vscode 打开该工具，此时目录结构如下：

```bash
.
├── README.md
├── jeb-mcp
│   ├── pyproject.toml
│   ├── src
│   │   └── jeb_mcp
│   │       ├── MCP.py
│   │       ├── server.py
│   │       └── server_generated.py
│   └── uv.lock
└── sample_cline_mcp_settings.json
```

2. 点击左侧活动栏 rooCode 图标，然后继续点击 RooCode 对话框右上角 `...`，最后点击编辑项目 MCP 按钮，
   会在当前目录下产生一个 `.roo` 目录，其中包含 `mcp.json` 文件。

![](assets/2025-08-26-10-03-53.png)

3. 修改 `mcp.json` 文件为下列内容：

```json
{
  "mcpServers": {
    "jeb": {
      "command": "uv",
      "args": ["--directory", "jeb-mcp/src/jeb_mcp", "run", "server.py"],
      "timeout": 1800,
      "disabled": false,
      "autoApprove": [
        "ping",
        "check_connection",
        "get_manifest",
        "get_all_exported_activities",
        "get_exported_activities_count",
        "get_an_exported_activity_by_index",
        "get_class_decompiled_code",
        "get_method_decompiled_code",
        "get_method_overrides",
        "get_method_callers",
        "get_superclass",
        "get_interfaces",
        "get_class_methods",
        "get_class_fields",
        "rename_class_name",
        "rename_method_name",
        "rename_field_name"
      ],
      "alwaysAllow": [
        "check_connection",
        "get_class_decompiled_code",
        "get_class_fields",
        "ping",
        "get_manifest",
        "get_all_exported_activities",
        "get_exported_activities_count",
        "get_an_exported_activity_by_index",
        "get_method_decompiled_code",
        "get_method_callers",
        "get_method_overrides",
        "get_superclass",
        "get_interfaces",
        "get_class_methods",
        "rename_class_name",
        "rename_method_name",
        "rename_class_field"
      ]
    }
  }
}
```

此时可以发现 mcp 服务器列表中已经存在 jeb mcp 服务器了。

4. 打开 jeb 菜单栏 `File->Scripts->Scripts selector...` 选中当前目录下 `jeb-mcp/src/jeb_mcp/MCP.py` 文件，
   运行脚本，此时可以在 jeb 的 logger 窗口中看到如下输出：

```bash
[MCP] Plugin loaded
[MCP] Plugin running
[MCP] Server started at http://127.0.0.1:16161
```

5. 在 RooCode 对话框中输入下列相应的任务即可，如：
```bash
1. 连接MCP JEB
2. 分析D:\xxx.apk 应用的 Lnet/xxx/MainActivity; 类的功能
3. 根据功能重命名所有方法名小于3个字符的名称
4. 如果调用了其他类的方法，分析相应的类功能，并重命名方法名小于3个字符的名称
5. 输出分析过程
```


# Demo
## DEMO for using JEB-MCP to analyze vulnerabilities in APK
![jebmcp](https://github.com/user-attachments/assets/28ea1c0e-76a7-4ed2-84b6-17645f671156)
