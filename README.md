# 农业采摘机器人路径规划系统

基于深度学习与路径优化算法的智能采摘机器人解决方案，支持果实成熟度检测、采摘路径规划、障碍物避障等功能。

## 项目结构

```
├── harvesting_robot_planner.py    # 采摘路径规划核心算法
├── fruit_maturity_detector.py     # 果实成熟度检测 (HSV颜色分析)
├── smart_sowing_planner.py        # 智能播种规划
├── smart_irrigation_planner.py    # 智能灌溉规划
├── real_data_interface.py         # GPS/传感器数据接口
├── test_end_to_end.py             # 端到端测试
└── harvesting-robot_README.md      # 详细文档
```

## 核心功能

### 1. 采摘路径规划
```python
from harvesting_robot_planner import HarvestingRobotPlanner, FruitTarget

planner = HarvestingRobotPlanner()
targets = [
    FruitTarget(x=1.2, y=0.5, z=1.8, radius=0.04, maturity=0.85),
]
path = planner.plan_path(targets)
```

### 2. 果实成熟度检测
```python
from fruit_maturity_detector import FruitMaturityDetector

detector = FruitMaturityDetector()
maturity = detector.detect(image_path)
```

### 3. 智能播种规划
```python
from smart_sowing_planner import SmartSowingPlanner

planner = SmartSowingPlanner()
plan = planner.optimize(field_size=(100, 50), crop="tomato")
```

### 4. GPS轨迹避障
```python
from real_data_interface import GPSInterface

gps = GPSInterface()
trajectory = gps.load_trace("gps_trace.json")
```

## 技术栈

- **Python 3.8+**
- **OpenCV** - 图像处理与成熟度检测
- **NumPy** - 数值计算
- **Matplotlib** - 可视化

## 快速开始

```bash
# 安装依赖
pip install opencv-python numpy matplotlib

# 运行端到端测试
python test_end_to_end.py

# 运行采摘路径规划
python harvesting_robot_planner.py
```

## 主要特性

- 🎯 **路径规划**: 最近邻 + 贪心优化算法
- 👁️ **成熟度检测**: HSV 颜色空间分析
- 🛡️ **障碍避障**: GPS轨迹预测 + 碰撞检测
- 🌱 **播种优化**: 密度计算 + 作物参数库
- 💧 **灌溉规划**: 按需分配 + 节水优化

## 应用场景

- 大棚果蔬采摘自动化
- 果园机器人采摘
- 智能农业管理系统

## License

MIT
