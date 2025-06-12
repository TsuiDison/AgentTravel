# 智能探索式多智能体协作配送系统

一个基于 Python 的智能配送系统仿真平台，支持无人机、汽车和机器狗三种智能体的**自主探索**与**协作配送**。系统具备未知环境探索、动态任务分配、实时地图构建和智能体协作等先进功能。

## 系统概述

本系统模拟真实世界的**未知环境配送场景**，智能体在**有限视野**下自主探索地图，通过**共享感知信息**构建全局地图知识库，并基于**动态更新的环境信息**进行智能任务分配。系统采用**分层决策架构**，结合上帝视角的全局优化与智能体的局部自主决策，提供了接近真实场景的配送解决方案。

### 🎯 核心设计理念

- **信息不对称**: 上帝视角掌握全局，智能体仅知局部
- **渐进式探索**: 从未知到已知的地图构建过程  
- **协作学习**: 智能体间实时共享探索发现
- **动态优化**: 基于新信息持续优化任务分配

## 🚀 核心创新功能

### 1. 🗺️ 智能探索系统
- **有限视野感知**: 每个智能体具有独立的感知半径，模拟真实视野限制
- **协作地图构建**: 智能体实时共享发现的地形信息，构建全局地图知识库
- **未知区域导航**: 支持在部分未知环境中的路径规划和探索决策
- **动态信息更新**: 地图信息随探索进度动态扩展和优化

### 2. 🎯 分层决策架构
- **上帝视角决策**: 
  - 全局最优的初始位置布局策略
  - 基于完整地图的距离权重计算
  - 战略层面的任务队列管理
- **智能体局部决策**:
  - 基于有限信息的自主探索
  - 动态路径调整和避障
  - 协作通信和信息共享

### 3. 🏪 中转站网络系统
- **任务队列管理**: 智能体已知的任务分发点和中转站网络
- **负载均衡**: 中转站之间的任务重新分配机制
- **补给站功能**: 智能体能量补充和维护点
- **信息汇聚点**: 地图信息的集中更新和同步

### 4. 🔄 动态任务分配
- **实时优化**: 基于不断扩展的地形信息优化任务分配
- **预测性调度**: 利用已探索信息预测最优配送路线
- **容错机制**: 处理探索过程中的意外发现和路径阻塞
- **自适应重分配**: 根据新发现的地形特征动态调整任务策略

## 系统架构

### 🧩 智能体信息分层架构

```
┌─────────────────────────────────────────────────────────────┐
│                    🌍 上帝视角决策层                          │
│  ┌─────────────────────────┬─────────────────────────────┐   │
│  │   全局地图信息         │    距离权重计算             │   │
│  │  - 完整地形数据        │  - 最优位置布局             │   │
│  │  - 所有障碍物位置      │  - 战略资源分配             │   │
│  │  - 道路网络拓扑        │  - 初始化策略制定           │   │
│  └─────────────────────────┴─────────────────────────────┘   │
│                            ↕️ 单向信息流                      │
└─────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────┐
│                 🏪 中转站网络层 (智能体已知)                  │
│  ┌─────────────────────────┬─────────────────────────────┐   │
│  │    任务分发中心        │      补给维护站             │   │
│  │  - 任务队列管理        │  - 能量补充点               │   │
│  │  - 优先级排序          │  - 维护服务点               │   │
│  │  - 负载均衡分配        │  - 信息同步节点             │   │
│  └─────────────────────────┴─────────────────────────────┘   │
│                            ↕️ 双向信息流                      │
└─────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────┐
│              🤖 智能体自主探索层 (有限视野)                   │
│  ┌─────────────────────────┬─────────────────────────────┐   │
│  │    感知探索模块        │    协作共享模块             │   │
│  │  - 视野半径感知        │  - 实时信息共享             │   │
│  │  - 地形识别分析        │  - 探索发现广播             │   │
│  │  - 障碍物检测          │  - 协作路径规划             │   │
│  │  - 未知区域探索        │  - 集群知识构建             │   │
│  └─────────────────────────┴─────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

### 🔄 动态任务分配流程

```
任务分配优化循环
├── 1️⃣ 初始化阶段
│   ├── 上帝视角: 计算全局最优布局
│   ├── 智能体: 接收初始位置(不知原因)
│   └── 中转站: 激活任务队列系统
│
├── 2️⃣ 探索发现阶段  
│   ├── 智能体自主感知(视野半径内)
│   ├── 实时共享地形发现
│   ├── 更新全局地图知识库
│   └── 识别新的中转站和障碍物
│
├── 3️⃣ 任务分配重优化
│   ├── 基于新地图信息重新评估
│   ├── 动态调整距离权重
│   ├── 重新分配未完成任务
│   └── 预测性路径规划
│
└── 4️⃣ 执行与反馈
    ├── 智能体执行优化后的任务
    ├── 持续探索未知区域
    ├── 实时反馈执行状态
    └── 循环迭代优化过程
```

### 🎯 核心创新架构详解

#### 1. 分层信息架构 (Information Hierarchy)

**🌍 上帝视角决策层 (God-View Decision Layer)**
```python
class GodViewOptimizer:
    """上帝视角全局优化器 - 智能体不可见"""
    
    核心功能:
    - initial_position_optimization(): 基于完整地图计算最优初始布局
    - distance_weight_calculation(): 全局距离权重矩阵计算
    - strategic_resource_allocation(): 战略资源分配决策
    
    决策依据:
    - 完整地形数据: terrain_map[100][100]
    - 全局障碍物分布: obstacle_positions
    - 道路网络拓扑: road_network_graph
    - 最优覆盖距离: optimal_coverage_distance
    
    输出(智能体不知原因):
    - 初始位置分配: {agent_id: (x, y, z)}
    - 隐性距离权重: distance_weights_matrix
```

**🏪 中转站网络层 (Transfer Station Network) - 智能体已知**
```python
class TransferStationNetwork:
    """中转站网络系统 - 智能体完全可见"""
    
    已知信息:
    - 所有中转站位置: transfer_stations = [(x1,y1), (x2,y2), ...]
    - 任务队列状态: task_queues = {station_id: [tasks]}
    - 补给站位置: supply_stations = [(x,y), ...]
    - 站点间连接: station_connections = {id: [connected_ids]}
    
    智能体可访问功能:
    - query_task_queue(station_id): 查询任务队列
    - request_task_assignment(): 请求任务分配
    - report_completion(task_id): 报告任务完成
    - request_supply(supply_type): 请求补给
```

**🤖 智能体探索层 (Agent Exploration Layer)**
```python
class AgentExplorationSystem:
    """智能体自主探索系统 - 目标导向"""
    
    感知能力:
    - perception_radius: 视野半径(可配置: 5-15单位)
    - terrain_detection(): 地形类型识别
    - obstacle_detection(): 障碍物检测
    - unknown_area_mapping(): 未知区域映射
    
    目标导向探索:
    - target_oriented_planning(): 基于任务目标的探索路径规划
    - adaptive_route_selection(): 根据已知地形调整路线
    - exploration_priority_calc(): 计算未知区域探索优先级
    - goal_accessibility_check(): 检查目标可达性
    
    共享机制:
    - share_discovery(terrain_info): 广播地形发现
    - receive_shared_info(): 接收其他智能体发现
    - update_global_knowledge(): 更新全局知识库
    - collaborative_path_planning(): 协作路径规划
```

#### 2. 动态任务分配优化循环

**阶段1: 初始化布局**
```python
def initialize_system():
    """系统初始化 - 信息不对称设计"""
    
    # 上帝视角计算(智能体不可见)
    optimal_positions = god_view.calculate_optimal_layout(
        complete_map=full_terrain_data,
        coverage_strategy="minimum_total_distance"
    )
    
    # 智能体接收位置(不知原因)
    for agent_id, position in optimal_positions.items():
        agents[agent_id].set_initial_position(position)
        # 智能体只知道：我被要求在这个位置开始
        
    # 激活中转站网络(智能体可见)
    transfer_network.activate_all_stations()
    transfer_network.publish_station_locations()
```

**阶段2: 探索发现循环**
```python
def exploration_discovery_loop():
    """持续探索发现过程"""
    
    while system_active:
        for agent in active_agents:
            # 个体感知
            local_discoveries = agent.perceive_environment(
                radius=agent.perception_radius
            )
            
            # 实时共享
            if local_discoveries:
                shared_knowledge.broadcast_discovery(
                    agent_id=agent.id,
                    discoveries=local_discoveries
                )
                
            # 更新全局知识
            agent.update_known_map(shared_knowledge.get_updates())
            
        # 触发任务重分配评估
        if significant_discovery_detected():
            trigger_task_reallocation()
```

**阶段3: 动态任务重分配**
```python
def dynamic_task_reallocation():
    """基于新发现的动态任务重分配"""
    
    # 获取当前已知地图
    current_known_map = shared_knowledge.get_current_map()
    
    # 重新计算任务分配
    new_allocation = task_allocator.optimize_allocation(
        known_terrain=current_known_map,
        active_tasks=task_manager.get_pending_tasks(),
        agent_states=get_all_agent_states()
    )
    
    # 更新任务分配
    for agent_id, new_tasks in new_allocation.items():
        agents[agent_id].update_task_assignment(new_tasks)
        
    # 预测性路径规划
    for agent in agents:
        agent.replan_paths_with_new_info()
```

#### 3. 信息共享机制设计

**地图知识库架构**
```python
class SharedMapKnowledge:
    """共享地图知识库"""
    
    def __init__(self):
        # 三层地图表示
        self.terrain_knowledge = {}      # 地形信息: {(x,y): terrain_type}
        self.obstacle_knowledge = {}     # 障碍物: {(x,y): obstacle_info}
        self.exploration_status = {}     # 探索状态: {(x,y): discovery_time}
        
        # 智能体贡献追踪
        self.discovery_credits = {}      # {(x,y): discoverer_agent_id}
        self.confidence_levels = {}      # {(x,y): confidence_score}
        
    def add_discovery(self, agent_id, position, terrain_info):
        """添加新发现"""
        self.terrain_knowledge[position] = terrain_info
        self.discovery_credits[position] = agent_id
        self.exploration_status[position] = current_time()
        
        # 触发重分配评估
        if self.is_significant_discovery(terrain_info):
            self.trigger_reallocation_evaluation()
```

#### 4. 优化算法核心

**距离权重动态计算**
```python
class DynamicDistanceWeights:
    """动态距离权重计算"""
    
    def calculate_weights(self, known_map, unknown_areas):
        """计算考虑未知区域的距离权重"""
        
        weights = {}
        for position in known_map.keys():
            # 基础距离权重
            base_weight = self.euclidean_distance_weight(position)
            
            # 地形影响因子
            terrain_factor = self.terrain_difficulty_factor(
                known_map[position]
            )
            
            # 未知区域风险因子
            unknown_risk = self.unknown_area_risk_factor(
                position, unknown_areas
            )
            
            # 综合权重
            weights[position] = (
                base_weight * terrain_factor * unknown_risk
            )
            
        return weights
```

#### 2. 载具系统 (`Vehicle`)

#### 2. 载具物理层系统 (Vehicle Physical Layer)

**载具基类架构** (`vehicle_system.py` + `config.py`)
```python
class Vehicle:
    """载具物理行为基类 - 已完整实现"""
    核心功能:
    - move_towards(): 朝目标平滑移动
    - interpolate_path(): 路径点间插值
    - 动画状态管理: position, rotation, height实时同步
    - 物理参数控制: speed, heading, max_turn_rate
    - 路径轨迹记录: path_trace用于可视化
    
    配置参数(config.py):
    VEHICLE_CONFIG = {
        'drone': {'count': 3, 'speed': 15, 'weight_limit': 5, 'max_height': 20},
        'car': {'count': 2, 'speed': 5, 'weight_limit': 100, 'turning_radius': 2.0},
        'robot_dog': {'count': 2, 'speed': 7, 'weight_limit': 20, 'max_climb_height': 1.0}
    }
    
    具体载具实现:
    - Drone: 三维飞行控制、高度管理、风力影响模拟
    - Car: 道路约束行为、交通规则遵守、转向系统
    - RobotDog: 攀爬能力、电池管理、全地形适应
```

**基础智能体实现** (`agent.py`)
```python
class Agent:
    """智能体基类 - 简化版本"""
    - 状态管理: IDLE, MOVING_TO_PICKUP, PICKING_UP, MOVING_TO_DELIVERY, DELIVERING
    - 任务处理: can_handle_task(), assign_task(), move_towards_target()
    - 能力参数: max_weight(载重), max_speed(速度), energy_consumption(能耗)
    
    具体智能体类型:
    - RobotDog: 载重5kg, 速度3单位/步, 地形适应性0.9
    - UnmannedVehicle: 载重50kg, 速度5单位/步, 道路偏好
    - Drone: 载重2kg, 速度8单位/步, 飞行高度50
```

**具体载具实现** (已完成):
```python
Drone (无人机):
    - 三维飞行控制: (x, y, z)坐标系，支持悬停
    - 高度管理: min_height=5, max_height=20, vertical_speed=1.0
    - 风力影响模拟: wind_effect基于高度的动态影响
    - 特殊行为: takeoff(), land(), hover()
    - 成本函数: 考虑水平距离+高度变化+风力因子

Car (汽车):
    - 道路约束行为: 仅在道路网络行驶，turning_radius=2.0
    - 交通规则遵守: obey_traffic_rules, stopped_at_intersection
    - 转向指示系统: turn_signal状态管理
    - 巡航优化: 巡航速度为最大速度70%

RobotDog (机器狗):
    - 攀爬能力: can_climb=True, max_climb_height=1.0
    - 电池管理: battery_level(0-100)实时监控
    - 全地形适应: 可穿越大多数地形类型
    - 续航优化: 巡航速度为最大速度60%
```

**物理仿真特性**:
- **平滑插值移动**: 路径点间0.5单位精度插值
- **真实物理约束**: 转弯半径、爬升速度、载重限制
- **动画状态同步**: 位置、旋转、高度实时更新
- **轨迹记录**: path_trace支持路径可视化
- **个性化标识**: 每个载具唯一颜色和ID

### 现有模块详解

#### 1. 基础智能体系统 (`agent.py`)
```python
class Agent:
    """智能体基类 - 当前已实现版本"""
    - 状态枚举: IDLE, MOVING_TO_PICKUP, PICKING_UP, MOVING_TO_DELIVERY, DELIVERING, RETURNING
    - 核心属性: agent_id, agent_type, position, max_weight, max_speed, energy_consumption
    - 任务处理: can_handle_task(), assign_task(), move_towards_target()
    - 移动控制: calculate_distance(), move_towards_target(), update()
    
    已实现智能体类型:
    - RobotDog: 载重5kg, 速度3单位/步, 地形适应性0.9
    - UnmannedVehicle: 载重50kg, 速度5单位/步, 道路偏好
    - Drone: 载重2kg, 速度8单位/步, 飞行高度50
    
    工厂方法:
    - create_random_agents(): 在地图上随机创建智能体群体
```

#### 2. 多智能体协调系统 (`multi_agent_system.py`)
```python
class MultiAgentCoordinationSystem:
    """当前已实现的协调系统 - 注意：需要修复导入"""
    - 智能体群体管理: 7个智能体(3无人机+2汽车+2机器狗)
    - 拍卖机制任务分配: _auction_based_allocation()
    - 通信管理: communication_hub, _route_message()
    - 性能监控: performance_metrics, _evaluate_performance()
    - 任务生命周期管理: add_task(), _monitor_tasks()
    
    核心算法:
    - 竞标价值计算: 距离30% + 载重25% + 地形20% + 负载15% + 紧急度10%
    - 任务状态跟踪: active_tasks, completed_tasks
    - 系统知识更新: _update_system_knowledge()
    
    ⚠️ 导入问题: 当前导入agent_system.py，需要改为agent.py
```

#### 3. 载具物理系统 (`vehicle_system.py`)
```python
class Vehicle:
    """载具物理行为模拟 - 从config.py获取参数"""
    - 动画状态管理: position, rotation, height实时同步
    - 平滑移动控制: 路径插值和转向处理
    - 物理约束: 速度限制、转弯半径、爬升能力
    - 轨迹记录: 支持路径可视化和回放
    
    具体载具类型 (配置在config.py中):
    - Drone: 三维飞行，高度控制，风力影响
    - Car: 道路约束，交通规则，转向系统
    - RobotDog: 全地形适应，电池管理，攀爬能力
```

#### 4. 任务系统 (`delivery_task.py`)
支持的任务属性：
- 重量限制
- 体积限制
- 时间窗口
- 安全需求
- 紧急程度
- 成本限制
- 可扩展性
- 货物类型

#### 5. 可视化系统 (`visualization.py`)
- **交互式GUI**: 基于 Tkinter 的用户界面
- **实时动画**: 载具移动和任务执行的动态显示
- **参数控制**: 天气条件、任务参数的实时调整
- **反馈系统**: 实时显示系统状态和执行日志

## 安装要求

```bash
pip install numpy matplotlib tkinter threading queue math time copy random
```

### 依赖说明
- `numpy`: 数值计算和数组操作
- `matplotlib`: 图形绘制和动画
- `tkinter`: GUI界面
- 其他为 Python 标准库

## 使用方法

### 运行系统
```bash
python main.py
```

### 界面操作
1. **天气控制**: 在左侧面板选择天气条件
2. **任务创建**: 
   - 设置起点和终点坐标
   - 配置任务参数(重量、时间窗口等)
   - 点击"创建任务"按钮
3. **实时监控**: 在右侧反馈区域查看系统状态

### 任务参数说明
- **起点/终点**: 地图坐标 (0-100范围)
- **重量限制**: 货物重量 (kg)
- **时间窗口**: 完成时间限制 (时间单位)
- **紧急程度**: 1-5级 (数字越大越紧急)
- **安全需求**: 1-5级 (数字越大要求越高)
- **成本限制**: 最大允许成本
- **货物类型**: normal/fragile (普通/易碎品)

## 算法详解

### 载具选择算法
系统采用多因素评分机制：

```python
总分 = 紧急程度分数 × 0.4 + 安全分数 × 0.3 + 成本分数 × 0.3
```

评估因素：
- 载重能力匹配
- 时间窗口满足度
- 地形适应性
- 成本效益
- 安全性要求

### A*路径规划
- **启发函数**: 欧几里得距离
- **成本函数**: 考虑地形难度和天气影响
- **约束条件**: 载具特定的移动限制

## 扩展性

### 添加新载具类型
```python
class NewVehicle(Vehicle):
    def __init__(self, start_pos, goal_pos):
        super().__init__(start_pos, goal_pos)
        # 设置载具特定属性
        self.special_ability = True
```

### 添加新地形类型
在 `Map` 类的 `terrain_types` 字典中添加新类型，并更新相关方法。

### 扩展任务属性
在 `DeliveryTask` 类的 `attributes` 字典中添加新属性。

## 性能特点

- **实时处理**: 支持动态任务添加和处理
- **并发执行**: 多线程任务分配和执行
- **平滑动画**: 60fps 动画更新频率
- **内存优化**: 路径插值减少内存占用

## 故障排除

### 常见问题
1. **载具无法移动**: 检查起点终点是否在有效范围内
2. **路径规划失败**: 确认目标位置可达
3. **动画卡顿**: 减少并发任务数量
4. **中文显示异常**: 确保系统支持中文字体

### 调试模式
系统提供详细的日志输出，可在反馈区域查看详细错误信息。

## 贡献指南

欢迎提交 Issue 和 Pull Request 来改进系统功能。

## 许可证

MIT License - 详见 LICENSE 文件

## 联系方式

如有问题或建议，请通过 GitHub Issues 联系。

## 📁 项目文件结构

```
e:\Sytemclass\Agent\
├── 🚀 系统启动
│   └── main.py                          # 系统主入口，简化版配送系统
│
├── ⚙️ 核心配置 (智能体已知)
│   ├── config.py                        # 系统配置：感知半径、载具参数、中转站坐标
│   └── transfer_station_network.py     # 中转站网络管理(基于config.py已知坐标)
│
├── 🌍 上帝视角决策层 (智能体不可见) 
│   ├── map_system.py                   # 地图环境系统(完整地形数据，上帝视角已实现)
│   ├── god_view_optimizer.py           # 全局最优布局计算(待实现)
│   └── distance_weight_calculator.py   # 隐性距离权重计算(待实现)
│
├── 🤖 智能体探索系统 (有限视野)
│   ├── agent.py                        # 基础智能体实现(机器狗、无人车、无人机)
│   ├── exploration_system.py           # 目标导向探索机制(待实现)
│   └── shared_map_knowledge.py        # 智能体共享地图知识库(待实现)
│
├── 🚗 载具物理层 
│   └── vehicle_system.py              # 载具物理行为模拟(已完整实现)
│
├── 📋 任务管理
│   ├── delivery_task.py               # 配送任务定义
│   ├── task_queue_manager.py          # 任务队列管理(待实现)
│   └── dynamic_task_allocator.py      # 动态任务分配器(待实现)
│
├── 🛣️ 路径规划
│   ├── path_planning.py               # A*路径规划算法
│   └── adaptive_path_planner.py       # 适应性路径规划(待实现)
│
├── 🔄 协调系统 (待实现)
│   ├── multi_agent_system.py          # 多智能体协调系统(需修复导入)
│   └── collaborative_system.py        # 协作配送系统(已删除)
│
├── 🎥 可视化系统
│   └── visualization.py               # 可视化界面系统
│
└── 📚 文档
    └── README.md                       # 项目文档(本文件)
```

### 🔧 实现状态说明

| 状态 | 文件名 | 功能描述 | 实现进度 |
|------|--------|----------|----------|
| ✅ **已实现** | `main.py` | 系统启动入口 | 完成 |
| ✅ **已实现** | `agent.py` | 基础智能体实现 | 完成 |
| ✅ **已实现** | `map_system.py` | 地图环境系统(上帝视角完整地形) | 完成 |
| ✅ **已实现** | `vehicle_system.py` | 载具物理模拟 | 完成 |
| ✅ **已实现** | `delivery_task.py` | 配送任务定义 | 完成 |
| ✅ **已实现** | `path_planning.py` | A*路径规划 | 完成 |
| ✅ **已实现** | `visualization.py` | 可视化界面 | 完成 |
| ✅ **已实现** | `config.py` | 系统配置(含中转站坐标) | 完成 |
| ✅ **已实现** | `transfer_station_network.py` | 中转站网络(智能体已知) | 完成 |
| ✅ **已实现** | `multi_agent_system.py` | 多智能体协调 | 完成(需修复导入) |
| ❌ **已删除** | `collaborative_system.py` | 协作配送系统 | 已移除 |
| ❌ **已删除** | `agent_system.py` | 高级智能体系统 | 已移除 |
| 🚧 **待实现** | `god_view_optimizer.py` | 上帝视角优化器 | 新功能 |
| 🚧 **待实现** | `exploration_system.py` | 目标导向探索机制 | 核心功能 |
| 🚧 **待实现** | `shared_map_knowledge.py` | 智能体共享地图知识库 | 核心功能 |
| 🚧 **待实现** | `task_queue_manager.py` | 任务队列管理 | 新功能 |
| 🚧 **待实现** | `dynamic_task_allocator.py` | 动态任务分配器 | 新功能 |
| 🚧 **待实现** | `distance_weight_calculator.py` | 隐性距离权重计算 | 新功能 |
| 🚧 **待实现** | `adaptive_path_planner.py` | 适应性路径规划 | 新功能 |

### 🔧 当前代码库架构说明

根据实际代码库分析，当前系统采用了**实用主义实现**策略：

#### ✅ 已完成的核心模块
1. **基础智能体系统** (`agent.py`): 
   - 三种智能体类型：机器狗、无人车、无人机
   - 基础状态管理和任务处理
   - 工厂方法支持批量创建智能体

2. **载具物理层** (`vehicle_system.py` + `config.py`):
   - 载具配置在`config.py`中集中管理
   - 完整的物理仿真和动画控制
   - 三种载具类型(Drone/Car/RobotDog)的详细实现

3. **地图环境系统** (`map_system.py`):
   - 地图尺寸：100x100单位，已知边界
   - 地形类型：未知，需要智能体探索发现
   - 支持动态地形查询和障碍物检测

4. **系统配置** (`config.py`):
   - 中转站网络坐标：已知且固定配置
   - 载具参数：速度、载重、物理限制
   - 感知半径：智能体视野范围配置

#### ❌ 发现的问题
1. **导入错误**: `multi_agent_system.py`试图导入不存在的`agent_system.py`
2. **架构简化**: 当前缺少探索和共享机制的具体实现

#### 🛠️ 核心信息架构特点

**已知信息 (智能体完全了解)**:
- **地图边界**: 100x100单位的探索范围
- **中转站位置**: 固定坐标，配置在`config.py`中，系统启动时直接可见
- **任务队列**: 中转站的任务分发状态，实时可查询
- **其他智能体位置**: 通过协作系统共享位置信息

**未知信息 (需要探索发现)**:
- **地形类型**: 每个位置的具体地形特征(平坦、陡峭、狭窄、丘陵、水域、道路)
- **障碍物分布**: 动态发现的阻塞区域和可通行路径
- **路径可达性**: 基于地形的实际通行能力和最优路线

**上帝视角独有信息 (智能体永远不知道)**:
- **完整地形数据**: 整个地图的详细地形分布
- **全局最优解**: 基于完整信息的最优位置布局策略
- **隐性距离权重**: 真实的地形难度系数和路径成本

#### 🚧 目标导向探索机制设计

**探索策略核心**:
```python
# 目标导向的探索规划
def plan_exploration_route(current_pos, target_pos, known_map):
    """
    基于任务目标和已知环境规划探索路径
    - 优先探索通往目标的路径上的未知区域
    - 考虑已知地形的可通行性
    - 选择探索价值最高的未知区域
    """
    
    # 1. 计算朝向目标的直线路径
    direct_path = calculate_direct_path(current_pos, target_pos)
    
    # 2. 识别路径上的未知区域
    unknown_areas = identify_unknown_areas(direct_path, known_map)
    
    # 3. 评估探索优先级
    exploration_priorities = calculate_exploration_value(
        unknown_areas, target_pos, current_pos
    )
    
    # 4. 生成探索路径
    return generate_exploration_route(exploration_priorities)
```

**探索优先级计算**:
```python
def calculate_target_oriented_priorities(unknown_areas, target_pos, current_pos):
    """计算目标导向的探索优先级"""
    
    priorities = {}
    
    for unknown_pos in unknown_areas:
        # 1. 距离目标的远近（越近优先级越高）
        distance_to_target = calculate_distance(unknown_pos, target_pos)
        target_priority = 1.0 / (distance_to_target + 1)
        
        # 2. 是否在直线路径上（路径上的优先级更高）
        on_path_bonus = 2.0 if is_on_direct_path(
            current_pos, target_pos, unknown_pos
        ) else 1.0
        
        # 3. 周围已知信息的密度（信息密度低的区域优先探索）
        info_density = get_surrounding_known_density(unknown_pos, known_terrain)
        density_factor = 1.0 / (info_density + 0.1)
        
        # 4. 战略价值（靠近中转站的区域优先级更高）
        strategic_value = calculate_strategic_importance(
            unknown_pos, transfer_stations
        )
        
        # 综合优先级计算
        priorities[unknown_pos] = (
            target_priority * 0.4 +      # 目标导向权重40%
            on_path_bonus * 0.3 +        # 路径权重30%
            density_factor * 0.2 +       # 信息密度权重20%
            strategic_value * 0.1        # 战略价值权重10%
        )
    
    return priorities
```

#### 🏪 中转站网络配置

**配置位置** (`config.py`):
```python
# 中转站网络配置 - 智能体已知
TRANSFER_STATIONS = {
    'main_hub': (50, 50),      # 主要中转站
    'north_station': (25, 75), # 北部站点
    'south_station': (75, 25), # 南部站点
    'east_station': (85, 50),  # 东部站点
    'west_station': (15, 50)   # 西部站点
}

# 补给站配置
SUPPLY_STATIONS = {
    'supply_1': (30, 30),
    'supply_2': (70, 70)
}
```

#### 🎯 配置参数扩展说明

根据当前代码库分析，建议扩展`config.py`以支持探索式系统：

```python
# 智能体感知配置
PERCEPTION_CONFIG = {
    'default_radius': 10,           # 默认感知半径
    'drone_radius': 15,             # 无人机感知半径(飞行高度优势)
    'car_radius': 8,                # 汽车感知半径(道路限制)
    'robot_dog_radius': 12,         # 机器狗感知半径(全地形适应)
    'sharing_frequency': 0.1        # 100ms感知共享频率
}

# 中转站网络配置 - 智能体已知
TRANSFER_STATIONS = {
    'main_hub': (50, 50),           # 主要中转站(地图中心)
    'north_station': (25, 75),      # 北部站点
    'south_station': (75, 25),      # 南部站点  
    'east_station': (85, 50),       # 东部站点
    'west_station': (15, 50)        # 西部站点
}

# 补给站配置 - 智能体已知
SUPPLY_STATIONS = {
    'supply_northeast': (75, 75),   # 东北补给站
    'supply_southwest': (25, 25),   # 西南补给站
    'supply_center': (50, 50)       # 中心补给站(与主中转站重合)
}

# 探索优先级权重配置
EXPLORATION_WEIGHTS = {
    'target_oriented': 0.4,         # 目标导向权重40%
    'path_bonus': 0.3,              # 路径权重30%
    'info_density': 0.2,            # 信息密度权重20%
    'strategic_value': 0.1          # 战略价值权重10%
}

# 地形难度配置(用于路径规划权重)
TERRAIN_DIFFICULTY = {
    'normal': 1.0,                  # 普通地形
    'steep': 2.5,                   # 陡峭地形
    'narrow': 1.8,                  # 狭窄地形
    'hilly': 1.5,                   # 丘陵地形
    'water': 999.0,                 # 水域(对非飞行器不可通行)
    'road': 0.8                     # 道路(汽车优势)
}
```

#### 🚧 待实现的探索式功能

**核心待实现模块**:

1. **目标导向探索系统** (`exploration_system.py`):
```python
class TargetOrientedExplorationSystem:
    """目标导向探索系统"""
    
    def __init__(self, agents, shared_knowledge, transfer_stations):
        self.agents = agents
        self.shared_knowledge = shared_knowledge  
        self.transfer_stations = transfer_stations  # 已知的中转站位置
        
    def plan_exploration_to_target(self, agent, target_pos):
        """规划朝向目标的探索路径"""
        current_pos = agent.position
        known_terrain = agent.local_map_knowledge
        
        # 1. 分析目标方向的未知区域
        target_direction = calculate_direction(current_pos, target_pos)
        unknown_areas_on_path = identify_unknown_on_path(
            current_pos, target_pos, known_terrain
        )
        
        # 2. 优先级计算：距离目标越近的未知区域优先级越高
        exploration_priorities = self.calculate_target_oriented_priorities(
            unknown_areas_on_path, target_pos, current_pos
        )
        
        # 3. 生成探索路径
        return self.generate_efficient_exploration_route(
            current_pos, target_pos, exploration_priorities
        )
```

2. **智能体共享地图知识库** (`shared_map_knowledge.py`):
```python
class SharedMapKnowledge:
    """智能体间共享的地图知识库"""
    
    def __init__(self):
        # 地图知识三层结构
        self.terrain_knowledge = {}      # {(x,y): terrain_type}
        self.obstacle_knowledge = {}     # {(x,y): obstacle_info}
        self.exploration_status = {}     # {(x,y): discovery_time}
        
        # 智能体贡献追踪
        self.discovery_credits = {}      # {(x,y): discoverer_agent_id}
        self.confidence_levels = {}      # {(x,y): confidence_score}
        
    def broadcast_discovery(self, agent_id, discoveries):
        """实时广播新发现的地形信息"""
        for position, terrain_info in discoveries.items():
            self.terrain_knowledge[position] = terrain_info
            self.discovery_credits[position] = agent_id
            self.exploration_status[position] = current_time()
            
        # 通知所有智能体更新本地知识
        self.notify_all_agents_update(discoveries)
```

3. **中转站网络管理** (`transfer_station_network.py`):
```python
class TransferStationNetwork:
    """中转站网络管理 - 基于config.py的已知坐标"""
    
    def __init__(self):
        # 从config.py加载已知的中转站位置
        from config import TRANSFER_STATIONS, SUPPLY_STATIONS
        self.transfer_stations = TRANSFER_STATIONS
        self.supply_stations = SUPPLY_STATIONS
        
        # 任务队列管理
        self.task_queues = {station_id: [] for station_id in TRANSFER_STATIONS}
        self.station_status = {station_id: "active" for station_id in TRANSFER_STATIONS}
        
    def get_nearest_station(self, position):
        """获取最近的中转站"""
        min_distance = float('inf')
        nearest_station = None
        
        for station_id, station_pos in self.transfer_stations.items():
            distance = calculate_distance(position, station_pos)
            if distance < min_distance:
                min_distance = distance
                nearest_station = station_id
                
        return nearest_station, self.transfer_stations[nearest_station]
```

#### 🎯 目标导向探索的核心设计

**智能体感知与共享流程**:
```python
def agent_perception_and_sharing_loop():
    """智能体感知与共享主循环"""
    
    while system_active:
        for agent in active_agents:
            # 1. 基于任务目标的感知
            if agent.current_task:
                target_pos = agent.current_task.goal_pos
                
                # 感知朝向目标方向的区域
                local_discoveries = agent.perceive_towards_target(
                    target_pos, perception_radius=agent.perception_radius
                )
            else:
                # 空闲时进行周围环境的常规感知
                local_discoveries = agent.perceive_environment(
                    radius=agent.perception_radius
                )
            
            # 2. 实时共享新发现
            if local_discoveries:
                shared_knowledge.broadcast_discovery(
                    agent.agent_id, local_discoveries
                )
                
            # 3. 接收其他智能体的发现并更新本地知识
            updates = shared_knowledge.get_updates_for_agent(agent.agent_id)
            agent.update_local_map_knowledge(updates)
            
            # 4. 基于新信息重新规划路径
            if agent.current_task and updates:
                agent.replan_route_with_new_info(updates)
        
        time.sleep(0.1)  # 100ms感知周期
```

### 🚧 实现优先级路线图

#### Phase 1: 目标导向探索系统 (Priority: 🔥 极高)
**文件**: `exploration_system.py`
- **核心功能**: 智能体基于任务目标进行探索路径规划
- **实现要点**: 朝向目标方向的未知区域优先探索
- **依赖**: 当前智能体位置、目标位置、已知地形信息

#### Phase 2: 共享地图知识库 (Priority: 🔥 极高)  
**文件**: `shared_map_knowledge.py`
- **核心功能**: 智能体间实时共享地形发现
- **实现要点**: 地形信息广播、本地知识更新、信息去重
- **依赖**: 智能体感知系统、通信机制

#### Phase 3: 中转站网络完善 (Priority: 🔥 高)
**文件**: `transfer_station_network.py` (已存在，需完善)
- **核心功能**: 基于config.py的已知中转站坐标管理
- **实现要点**: 任务队列管理、最近站点查询、补给服务
- **依赖**: config.py中的TRANSFER_STATIONS配置

#### Phase 4: 动态任务分配器 (Priority: 🔥 中)
**文件**: `dynamic_task_allocator.py`
- **核心功能**: 基于新地形信息重新分配任务
- **实现要点**: 任务重评估、路径重规划、负载均衡
- **依赖**: 共享地图知识库、探索系统

这种设计确保了智能体的探索始终**以任务目标为导向**，同时利用**已知的中转站网络**和**共享的地形知识**进行最优路径规划。