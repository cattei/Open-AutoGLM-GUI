### 问题分析
打包脚本 `build_exe.py` 尝试将不存在的 `demo_integration.py` 文件添加到打包数据中，导致 PyInstaller 打包失败。

### 解决方案
修改 `build_exe.py` 文件，移除对不存在的 `demo_integration.py` 文件的引用。

### 修复步骤
1. **修改 `create_spec_file()` 函数**：
   - 删除 spec_content 中第 33 行的 `('demo_integration.py', '.')` 引用

2. **修改 `build_exe()` 函数**：
   - 删除 cmd 列表中第 149 行的 `'--add-data', 'demo_integration.py;.'` 引用

### 修复后效果
- 打包脚本不再尝试打包不存在的文件
- PyInstaller 能够成功执行打包过程
- 生成可执行文件 `PhoneAgentGUI.exe`

### 技术说明
- 移除的文件 `demo_integration.py` 可能是一个遗留的引用，实际项目中并不存在
- 该文件的缺失不影响程序的核心功能
- 修改后打包脚本将只包含项目中实际存在的文件