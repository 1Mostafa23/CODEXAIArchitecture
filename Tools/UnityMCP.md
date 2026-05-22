---
type: ConcreteFrame
---
# UnityMCP

description: Unity Editor bridge. Runs at localhost:8080 by default.
used_by: [[Coder]]
install: Unity Package Manager -> Add package from git URL -> `https://github.com/CoplayDev/unity-mcp.git?path=/MCPForUnity#main`
requirements: Unity 2021.3 LTS+; Python 3.10+; `uv`/`uvx` on PATH for local MCP client stdio/server tooling.
client_http_url: `http://localhost:8080/mcp`

## Key Tools
| Tool | Action |
|---|---|
| `create_script` | Write C# to `Assets/Scripts/` |
| `manage_scene` | Add / remove GameObjects |
| `manage_gameobject` | Add components, set field values |
| `read_console` | Read Unity console output |
| `run_tests` | Run Play Mode tests |
| `manage_build` | Build Android APK |
