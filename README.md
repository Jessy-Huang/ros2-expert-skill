# ROS 2 专家助手 Skill

**ClawHub 地址**: https://clawhub.ai/skills/ros2-expert

[![ClawHub](https://img.shields.io/badge/ClawHub-ros2--expert-blue)](https://clawhub.ai/skills/ros2-expert)

基于 ROS 2 Humble 版本的智能专家助手，提供工程开发、架构分析、学习教学、环境配置四大核心能力。

## 功能特性

### 🔧 工程开发辅助
- 需求分析与架构设计
- 基于 ROS 2 通信机制（话题、服务、动作）的方案设计
- 高质量代码生成（Python/C++）
- 排错引导与最佳实践建议

### 📊 工程分析解读
- 代码结构扫描与通信机制提取
- 节点间通信关系图解
- 架构优化建议

### 📚 学习教学科普
- 核心概念讲解（节点、话题、服务、动作、参数）
- 循序渐进的学习路径规划
- 官方文档引导

### ⚙️ 环境配置检验
- 一键安装工具使用指导
- 安装后环境检验
- 常见问题诊断与解决

## 知识来源

- **官方文档**: [ROS 2 Humble 文档](http://fishros.org/doc/ros2/humble/)
- **配置工具**: [小鱼一键安装工具](https://fishros.org.cn/forum/topic/20/)

## 安装使用

### 方式一：从 ClawHub 安装（推荐）

在 Openclaw 中直接搜索并安装：
- ClawHub 地址: https://clawhub.ai/skills/ros2-expert

### 方式二：从 GitHub 安装

在 Openclaw 中使用 GitHub 仓库地址安装：
```
git@github.com:Jessy-Huang/ros2-expert-skill.git
```

### 触发场景示例

| 模式 | 触发示例 |
|------|---------|
| 工程开发 | "如何实现一个发布者节点？"、"帮我设计一个导航系统架构" |
| 工程分析 | "分析一下这个节点的通信机制"、"解释这个工程的架构设计" |
| 学习教学 | "什么是 ROS 2 话题？"、"ROS 2 和 ROS 1 有什么区别？" |
| 环境配置 | "如何安装 ROS 2 Humble？"、"rosdep update 失败怎么办？" |

## 技能包内容

```
ros2-expert/
├── SKILL.md                              # 入口文档
├── references/
│   ├── ros2-core-concepts.md             # 核心概念详解
│   ├── installation-guide.md             # 安装配置指南
│   └── best-practices.md                 # 开发最佳实践
└── assets/
    ├── talker-listener-template.md       # 话题通信模板
    ├── service-client-template.md        # 服务通信模板
    └── action-client-server-template.md  # 动作通信模板
```

## 代码模板

提供 Python 和 C++ 双语言支持：

- **话题通信**: 发布者/订阅者模板
- **服务通信**: 服务端/客户端模板  
- **动作通信**: 动作服务端/客户端模板

所有模板均可直接复制使用，包含完整导入语句和 main 函数入口。

## 版本说明

- **ROS 2 发行版**: Humble Hawksbill
- **支持语言**: Python 3, C++ 17
- **目标平台**: Ubuntu 22.04 LTS

## 快速开始

### 环境安装

使用小鱼一键安装工具：

```bash
wget http://fishros.com/install -O fishros && . fishros
```

选择对应的 ROS 2 发行版进行安装。

### 验证安装

```bash
# 检查环境变量
printenv | grep ROS

# 运行示例节点
ros2 run demo_nodes_cpp talker
ros2 run demo_nodes_py listener
```

## 常见问题

### 安装相关

| 问题 | 解决方案 |
|------|---------|
| NO_PUBKEY 错误 | `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <KEY>` |
| APT 锁错误 | 关闭其他包管理器或删除锁文件 |
| 网络问题 | 使用一键工具换源 |

### 开发相关

| 问题 | 解决方案 |
|------|---------|
| 节点无法通信 | 检查话题名称、消息类型是否一致 |
| 服务调用超时 | 确认服务端已启动，使用 `ros2 service list` 检查 |
| 参数未生效 | 检查是否正确声明和获取参数 |

## 贡献

欢迎提交 Issue 和 Pull Request 来改进这个 Skill。

## 许可证

Apache-2.0 License

## 联系方式

- GitHub: [Jessy-Huang](https://github.com/Jessy-Huang)
- Email: hjc@15579663430@163.com
