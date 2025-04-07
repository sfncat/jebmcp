A quick-and-dirty MCP server&Plugin for JEB Pro.
Tested on Cline.

1.安装uv,不用uv可以改json里的命令
2.git clone 代码
3.打开jeb,F2选择MCP.py
4.在vscode的cline中 Configure MCP Servers
MCP的json修改
5.修改mcp的目录
      "args": [
        "--directory",
        "/home/kali/workspace/github/jebmcp/jeb-mcp/src/jeb_mcp",
        "run",
        "server.py"
      ],

6.在cline中连接jeb server,正常应该可连上.Done
7.告诉ai apk的绝对路径,要分析的类,函数名和要求


Reference: https://github.com/mrexodia/ida-pro-mcp

![jebmcp](https://github.com/user-attachments/assets/28ea1c0e-76a7-4ed2-84b6-17645f671156)
