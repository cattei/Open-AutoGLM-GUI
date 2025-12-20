# 鸡哥手机助手 - Open-AutoGLM-GUI

基于Open-AutoGLM项目开发的手机自动化图形用户界面，支持安卓、鸿蒙和iOS设备的智能任务执行。

## 🌟 功能特性

### 核心功能
- 🖥️ 友好的图形界面，无需记忆命令行参数
- ⚙️ 可自定义base-url、model、apikey和任务命令
- 💾 支持保存和加载配置
- 📝 实时显示程序输出
- 🔒 API Key密码显示/隐藏功能
- ⏹️ 支持停止正在运行的程序

### 设备支持
- 📱 **安卓设备** - 通过ADB控制
- 🟢 **鸿蒙设备** - 通过HDC控制  
- 🍎 **iOS设备** - 通过WebDriverAgent控制

### 智能功能
- 🎯 任务润色器 - 自动润色复杂任务指令
- 🔄 多设备支持 - 自动检测和管理多个连接设备
- 📊 步数限制 - 可设置最大执行步数防止死循环
- 🔧 应用支持 - 支持主流手机应用的自动化操作

## 🚀 使用方法

### 安装依赖
```bash
pip install -r requirements.txt
```

### 启动方式

#### 方法1: Python脚本启动
```bash
python gui.py   
```

#### 方法2: 可执行文件启动
```bash
PhoneAgentGUI.exe  
```

## ⚙️ 参数说明

### 基础参数
- **Base URL**: 模型API的基础URL
  - 默认: `https://open.bigmodel.cn/api/paas/v4` (智谱AI)
- **Model**: 模型名称
  - 默认: `autoglm-phone-9b`
- **API Key**: 用于身份验证的API密钥
  - 智谱AI密钥格式: `xxxxxxxx.xxxxxxxxxx.xxxxxxxxxx`
- **最大步数**: 任务执行的最大步数，防止死循环
  - 默认: `200`

### 设备参数
- **设备类型**: 选择连接的设备类型
  - 安卓: 通过ADB控制
  - 鸿蒙: 通过HDC控制  
  - iOS: 通过WebDriverAgent控制
- **任务命令**: 要执行的具体任务，如"打开美团搜索附近的火锅店"

## 📋 使用步骤

### 1. 启动程序
运行上述任一命令启动GUI界面

### 2. 设备准备
根据您的设备类型进行准备：

#### 安卓设备
- ✅ 开启USB调试模式
- ✅ 连接电脑
- ✅ 安装ADB工具
- ✅ 安装ADB Keyboard应用（已内置在项目中）

#### 鸿蒙设备  
- ✅ 开启开发者模式
- ✅ 开启HDC调试
- ✅ 下载hdc.exe工具
- ✅ 连接电脑

#### iOS设备
- ✅ 开发者账号
- ✅ xcode导入WebDriverAgent

### 3. 配置参数
- 填写您的Base URL（默认已填写智谱AI的API地址）
- 填写模型名称（默认为autoglm-phone）
- 填写您的API Key（重要！请替换为真实密钥）
- 选择正确的设备类型
- 输入您要执行的任务命令
- 设置合适的最大步数

### 4. 运行任务
- 点击"运行"按钮开始执行
- 观察实时输出信息
- 如需中断，点击"停止"按钮

### 5. 配置管理
- 点击"保存配置"可将当前参数保存
- 下次启动时自动加载已保存配置

## ⚠️ 注意事项

### 安全相关
1. **API Key安全**: 请妥善保管您的API Key，不要分享给他人
2. **设备权限**: 确保给予应用必要的设备控制权限
3. **数据隐私**: 任务执行过程中可能涉及个人数据，请注意隐私保护

### 技术要求
1. **Python环境**: Python 3.7+
2. **网络连接**: 确保网络连接正常，能够访问API服务器
3. **设备兼容性**: 
   - 安卓: Android 5.0+
   - 鸿蒙: HarmonyOS 2.0+
   - iOS: iOS 12.0+ 

## 🔧 错误处理

### 常见错误及解决方案

| 错误类型 | 可能原因 | 解决方案 |
|---------|----------|----------|
| **API Key无效** | 密钥错误或过期 | 检查API Key格式，重新获取密钥 |
| **网络连接失败** | 网络问题或API地址错误 | 检查网络连接，确认Base URL正确 |
| **设备未连接** | USB未连接或调试未开启 | 重新连接设备，开启调试模式 |
| **ADB工具未安装** | 缺少ADB环境变量 | 安装ADB工具并添加到PATH |
| **HDC工具未找到** | hdc.exe不在正确位置 | 下载hdc.exe并放置到程序目录 |

### 调试技巧
- 查看实时输出区域的详细错误信息
- 使用命令行工具验证设备连接：
  - 安卓: `adb devices`
  - 鸿蒙: `hdc list targets`

## 📁 配置文件

### GUI配置 (`gui_config.json`)
```json
{
  "base_url": "https://open.bigmodel.cn/api/paas/v4",
  "model": "autoglm-phone", 
  "apikey": "your-bigmodel-api-key",
  "task": "输入你想要执行的任务，例如：打开美团搜索附近的火锅店",
  "max_steps": "200",
  "device_type": "安卓"
}
```

### AI配置 (`ai_config.json`)
包含模型参数和推理设置的详细配置

## 💻 系统要求

### 基础环境
- **Python**: 3.7或更高版本
- **操作系统**: Windows 10+, macOS 10.14+, Ubuntu 18.04+
- **内存**: 至少4GB RAM
- **存储**: 至少2GB可用空间

### Python依赖
```bash
pip install -r requirements.txt
```

主要依赖包：
- `Pillow>=12.0.0` - 图像处理
- `openai>=2.9.0` - API调用
- `aiohttp>=3.8.0` - 异步HTTP
- `requests>=2.31.0` - HTTP请求（iOS支持）

## 📱 设备支持详解

### 安卓设备（ADB）
#### 系统要求
- Android 5.0 (API 21) 或更高版本
- 已开启USB调试模式

#### 安装步骤
1. **下载ADB工具**
   ```bash
   # 官方下载地址
   https://developer.android.com/studio/releases/platform-tools
   ```

2. **安装ADB Keyboard**
   - 使用项目内置的 `ADBKeyboard.apk`
   - 在手机上安装并设为默认输入法

3. **验证连接**
   ```bash
   adb devices
   ```

### 鸿蒙设备（HDC）
#### 系统要求
- HarmonyOS 2.0 或更高版本
- 已开启开发者模式和HDC调试

#### 安装步骤
1. **下载HDC工具**
   ```bash
   # 官方下载地址
   https://gitee.com/openharmony/docs
   # 或从HarmonyOS SDK获取
   ```

2. **配置hdc.exe**
   - 将hdc.exe放置在程序同一目录下
   - 或添加到系统PATH环境变量

3. **验证连接**
   ```bash
   hdc list targets
   ```

## 🚀 快速开始示例

### 示例1：美团搜索
1. 连接安卓设备并开启USB调试
2. 启动GUI程序
3. 输入智谱AI的API Key
4. 任务命令：`打开美团搜索附近的火锅店`
5. 点击"运行"

### 示例2：微信操作
1. 选择正确的设备类型
2. 任务命令：`打开微信给张三发消息：晚上一起吃饭`
3. 设置最大步数为50（简单任务）
4. 点击"运行"并观察执行过程

### 示例3：鸿蒙设备操作
1. 将设备类型切换为"鸿蒙"
2. 确保hdc.exe在正确位置
3. 任务命令：`打开相机拍照并保存`
4. 运行并检查输出

## 🆘 获取帮助

- **原始项目**: [Open-AutoGLM](https://github.com/zai-org/Open-AutoGLM)
- **微信公众号**: 菜芽创作小助手（更多工具和教程）
- **问题反馈**: 查看程序输出中的详细错误信息
- **社区支持**: 加入相关技术交流群

## 📄 许可证

本项目基于Open-AutoGLM开源协议，请遵守相关许可证要求。
