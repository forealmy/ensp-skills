# eNSP Skill 开发日志

## 概述
这是一个为 AI Agent 创建 eNSP 网络拓扑文件的 Skill。

## 已完成功能

### 1. 格式分析
通过分析 eNSP 官方示例文件，掌握了 .topo 格式：
- 文件位置：`E:\files\eNSP\examples\`
- 分析了 10+ 个不同拓扑示例

### 2. 核心文件
- `SKILL.md` - Agent 技能说明
- `references/topo-reference.md` - 格式参考文档

### 3. 支持的设备类型
| 设备 | Model | 说明 |
|------|-------|------|
| 路由器 | AR1220 | 2GE + 8Ethernet |
| 路由器 | AR2220 | 2GE + Serial |
| 交换机 | S5700 | 24GE |
| PC | PC | 1GE |
| 笔记本 | Laptop | 1GE |
| 组播服务器 | MCS | 1Ethernet |
| 云 | Cloud | Ethernet 接口 |
| 无线 AC | AC6005 | 8GE |
| 无线 AP | AP6050 | 2GE |
| 无线终端 | STA | 无线 |

### 4. 支持的线缆类型
- `Copper` - 以太网线
- `Serial` - 串口线
- `Auto` - 自动检测

### 5. 支持的图形元素
- `shapes` - 区域框（type 0/1/2）
- `txttips` - 文本标注

## 待完成功能

### 设备支持
- [ ] Server（服务器）
- [ ] 防火墙（USG）
- [ ] 更多的 AP 型号
- [ ] 更多的路由器型号（AR201、AR3260 等）

### 功能增强
- [ ] 自动布局算法优化
- [ ] 支持更多 shapes 类型（圆形等）
- [ ] 设备配置模板

## 已知问题
- 暂无

## 示例文件
位于 `examples/` 目录，包含官方示例：
- 1-1RIPv1&v2.topo
- 2-1Single-Area OSPF.topo
- Multi-Area OSPF.topo

## 使用方式
1. 用户描述网络拓扑需求
2. AI 根据 SKILL.md 生成 .topo 文件
3. 用户用 eNSP 打开文件
