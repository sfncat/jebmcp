A quick-and-dirty MCP server&Plugin for JEB Pro.
Tested on Cline.

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

![jebmcp](https://github.com/user-attachments/assets/28ea1c0e-76a7-4ed2-84b6-17645f671156)
