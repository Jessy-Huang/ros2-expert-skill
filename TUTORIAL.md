# ROS 2 专家助手 Skill 使用教程

## 目录
- [简介](#简介)
- [功能特色](#功能特色)
- [环境准备](#环境准备)
- [安装方法](#安装方法)
- [快速上手](#快速上手)
- [使用场景示例](#使用场景示例)
- [项目实战引导](#项目实战引导)
- [常见问题](#常见问题)

---

## 简介

ROS 2 专家助手是一款专为机器人开发者打造的智能技能包，基于 ROS 2 Humble 版本，提供工程开发、架构分析、学习教学、环境配置、项目实战引导五大核心能力。无论你是 ROS 2 初学者还是资深开发者，都能通过这个 Skill 获得专业的指导和帮助。

**ClawHub 地址**: https://clawhub.ai/skills/ros2-expert

**GitHub 仓库**: https://github.com/Jessy-Huang/ros2-expert-skill

---

## 功能特色

### 🚀 四大核心能力

| 能力模块 | 功能描述 | 适用场景 |
|---------|---------|---------|
| **工程开发辅助** | 需求分析、架构设计、代码生成、排错引导 | 开发新的 ROS 2 节点或功能包 |
| **工程分析解读** | 代码结构扫描、通信机制提取、架构图解、优化建议 | 分析现有 ROS 2 工程 |
| **学习教学科普** | 概念讲解、交互式教学、学习路径规划 | 学习 ROS 2 基础知识 |
| **环境配置检验** | 一键安装指导、安装检验、问题诊断 | 安装配置 ROS 2 环境 |

### ✨ 特色亮点

#### 1. 双语言代码支持
- 提供 Python 和 C++ 双语言代码模板
- 所有代码可直接复制使用，包含完整导入和 main 函数

#### 2. 权威知识来源
- 基于 ROS 2 Humble 官方文档
- 集成小鱼一键安装工具最佳实践

#### 3. 智能模式切换
- 自动识别用户意图，切换对应工作模式
- 无需手动指定，开箱即用

#### 4. 完整代码模板
- 话题通信（发布者/订阅者）
- 服务通信（服务端/客户端）
- 动作通信（动作服务端/客户端）

#### 5. 项目实战引导
- 精选三个开源项目：SO-ARM100、reBot-DevArm、lerobot-ros
- 结构化代码解读与通信机制分析
- AI 增强型实战任务设计

---

## 环境准备

### 安装 Openclaw

Openclaw 是一个 AI Agent 运行平台，支持加载和运行 Skill。

**官网地址**: https://openclaw.ai/

#### 安装步骤

1. 访问 Openclaw 官网下载对应平台的客户端
2. 按照安装向导完成安装
3. 注册并登录 Openclaw 账号

> 💡 **提示**: Openclaw 支持多种操作系统，请根据你的系统选择合适的版本。

---

## 安装方法

### 方式一：从 ClawHub 安装（推荐）

1. 打开 Openclaw 客户端
2. 进入 Skill 管理页面
3. 搜索 `ros2-expert` 或访问 https://clawhub.ai/skills/ros2-expert
4. 点击 **安装** 按钮

![从 ClawHub 安装](https://via.placeholder.com/600x300?text=ClawHub+Install)

### 方式二：从 GitHub 安装

1. 打开 Openclaw 客户端
2. 进入 Skill 管理页面
3. 选择 **从 URL 安装**
4. 输入仓库地址：
   ```
   https://github.com/Jessy-Huang/ros2-expert-skill
   ```
5. 点击 **安装** 按钮

### 方式三：本地文件安装

1. 从 GitHub 下载 `ros2-expert.skill` 文件
2. 打开 Openclaw 客户端
3. 进入 Skill 管理页面
4. 选择 **从文件安装**
5. 选择下载的 `.skill` 文件

---

## 快速上手

### 第一步：启动 Skill

安装完成后，在 Openclaw 中创建新的对话，选择已安装的 `ros2-expert` Skill。

### 第二步：开始对话

Skill 会自动识别你的意图并切换到对应模式。以下是几个快速入门示例：

#### 示例 1：学习 ROS 2 基础概念

```
用户: 什么是 ROS 2 话题？

Skill: 话题（Topic）是 ROS 2 中节点间传递数据的通信通道...
[自动进入学习教学模式，提供概念讲解和文档链接]
```

#### 示例 2：开发一个发布者节点

```
用户: 帮我写一个 Python 发布者节点，发布字符串消息

Skill: 
[自动进入工程开发模式]
1. 需求分析：创建一个定时发布字符串的话题发布者
2. 架构设计：使用话题通信，消息类型 std_msgs/String
3. 代码生成：
```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from std_msgs.msg import String

class Talker(Node):
    def __init__(self):
        super().__init__('talker')
        self.publisher = self.create_publisher(String, 'chatter', 10)
        self.timer = self.create_timer(0.5, self.timer_callback)
        self.count = 0

    def timer_callback(self):
        msg = String()
        msg.data = f'Hello ROS 2: {self.count}'
        self.publisher.publish(msg)
        self.get_logger().info(f'发布: {msg.data}')
        self.count += 1

def main(args=None):
    rclpy.init(args=args)
    node = Talker()
    rclpy.spin(node)
    node.destroy_node()
    rclpy.shutdown()

if __name__ == '__main__':
    main()
```
```

#### 示例 3：安装 ROS 2 环境

```
用户: 如何安装 ROS 2 Humble？

Skill:
[自动进入环境配置模式]
使用小鱼一键安装工具：

1. 运行安装命令：
   wget http://fishros.com/install -O fishros && . fishros

2. 选择换源（首次安装推荐）
3. 选择安装 ROS 2 Humble
4. 等待安装完成

安装后检验：
- printenv | grep ROS
- ros2 --help
- ros2 run demo_nodes_cpp talker
```

---

## 使用场景示例

### 场景一：开发机器人导航节点

**用户输入**:
```
我需要开发一个机器人导航节点，订阅目标位置，发布速度指令
```

**Skill 响应**:
1. **需求分析**: 导航节点需要订阅目标位置话题，发布速度控制话题
2. **架构设计**: 
   - 订阅: `/goal_pose` (geometry_msgs/PoseStamped)
   - 发布: `/cmd_vel` (geometry_msgs/Twist)
   - 建议添加状态反馈服务
3. **生成完整代码框架**
4. **提供编译运行指导**

---

### 场景二：分析现有工程

**用户输入**:
```
这是我工程的节点代码，帮我分析通信机制
[上传代码文件]
```

**Skill 响应**:
1. **结构扫描**: 识别节点、话题、服务、参数
2. **通信关系图**:
   ```
   [Camera Node] --/image--> [Detector Node] --/detections--> [Tracker Node]
                    |--/camera_info--> [Detector Node]
   ```
3. **架构评估**: 分析优缺点
4. **优化建议**: 提出改进方案

---

### 场景三：学习 ROS 2 通信机制

**用户输入**:
```
话题、服务、动作有什么区别？什么时候用哪个？
```

**Skill 响应**:
1. **概念讲解**: 通俗解释三种通信机制
2. **对比表格**:

| 特性 | 话题 | 服务 | 动作 |
|------|------|------|------|
| 通信模式 | 发布-订阅 | 请求-响应 | 目标-反馈-结果 |
| 数据流 | 连续流 | 一次性 | 长时间任务 |
| 反馈 | ❌ | ❌ | ✅ |

3. **选择指南**: 
   - 传感器数据 → 话题
   - 参数查询 → 服务
   - 导航任务 → 动作

---

### 场景四：解决环境配置问题

**用户输入**:
```
rosdep update 一直失败，怎么解决？
```

**Skill 响应**:
1. **问题诊断**: 可能是网络问题或源配置问题
2. **解决方案**:
   ```bash
   # 方法一：使用小鱼工具配置 rosdep
   wget http://fishros.com/install -O fishros && . fishros
   # 选择 rosdep 配置选项
   
   # 方法二：手动更换源
   sudo apt-get update
   ```
3. **验证方法**: 提供验证命令

---

## 项目实战引导

### 功能介绍

项目实战引导是本 Skill 的特色功能，通过解析精选的开源项目，帮助你在真实工程中掌握 ROS2 核心机制，并引导你结合 AI 完成进阶任务。

### 推荐项目

| 项目名称 | 核心定位 | ROS2 相关亮点 | 适用场景 |
|---------|---------|-------------|---------|
| **SO-ARM100** | 标准开源机械臂硬件 | URDF 模型，Gazebo/Isaac Sim 仿真 | 理解机械臂 URDF 描述与仿真控制 |
| **reBot-DevArm** | 全开源机械臂 | ROS2 Humble 驱动、MoveIt2 | 完整软硬件方案，Sim2Real |
| **lerobot-ros** | LeRobot + ROS2 集成 | SLAM、Nav2、分布式架构 | AI 模型接入 ROS2 系统 |

### 使用示例

**用户输入**:
```
我想通过项目学习 ROS2，能推荐一些适合初学者的工程吗？
```

**Skill 响应**:
> "我为你找到了三个非常适合 ROS2 入门的工程型项目，分别覆盖了**纯机械臂仿真**、**完整机械臂软硬件**、**移动机器人 + AI 集成**三个方向。你可以根据兴趣选择一个，我会带你一步步读懂代码、理解原理，最后设计一个结合 AI 的编程任务。"

**用户选择项目后**，Skill 会：
1. 输出项目概览与 ROS2 组件清单
2. 展示代码结构树
3. 分析通信机制（节点、话题、服务、动作）
4. 精讲关键代码片段
5. 设计 AI 增强型实战任务
6. 推荐后续学习路径

### 实战任务示例

**任务：自然语言导航控制**（基于 lerobot-ros）

- **任务目标**：结合 LLM，让机器人理解自然语言导航指令
- **涉及知识**：Nav2、动作客户端、服务通信、坐标变换
- **AI 辅助**：Prompt 设计、Nav2 接口、错误处理
- **验收标准**：可理解 10+ 种自然语言指令，导航成功率 >80%

---

## 常见问题

### Q1: Skill 支持哪些 ROS 2 版本？

**A**: 本 Skill 基于 ROS 2 Humble 版本开发，代码示例和命令兼容 Humble。若使用其他发行版（如 Foxy、Iron、Jazzy），部分命令可能略有不同，Skill 会提示相关差异。

---

### Q2: 生成的代码可以直接运行吗？

**A**: 可以。所有代码模板都是完整的，包含必要的导入语句和 main 函数入口。只需：
1. 创建功能包
2. 将代码放入对应目录
3. 编译运行

Skill 会提供完整的创建、编译、运行命令。

---

### Q3: 如何获取 ROS 2 官方文档？

**A**: Skill 的知识来源包括：
- ROS 2 Humble 官方文档: http://fishros.org/doc/ros2/humble/
- 小鱼一键安装工具: https://fishros.org.cn/forum/topic/20/

Skill 会在回答中引用相关文档章节。

---

### Q4: Skill 能帮我调试代码吗？

**A**: 可以。将代码和错误信息发给 Skill，它会：
1. 分析错误原因
2. 提供修复方案
3. 给出最佳实践建议

---

### Q5: 支持哪些编程语言？

**A**: 支持 Python 和 C++ 双语言：
- **Python**: 使用 rclpy 库
- **C++**: 使用 rclcpp 库

Skill 会根据你的需求提供对应语言的代码。

---

## 技术支持

- **GitHub Issues**: https://github.com/Jessy-Huang/ros2-expert-skill/issues
- **ClawHub 页面**: https://clawhub.ai/skills/ros2-expert
- **邮箱**: hjc@15579663430@163.com

---

## 许可证

MIT License - 欢迎自由使用和贡献！

---

**开始你的 ROS 2 开发之旅吧！** 🤖
