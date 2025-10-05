# Perp DEX Trading Tools - Project Overview / 永续合约DEX交易工具 - 项目概览

## English Version

### 🚀 What is this repository?

This repository contains a **modular automated trading bot** designed specifically for perpetual futures trading on decentralized exchanges (DEXs). The bot implements a sophisticated trading strategy focused on generating high trading volume while maintaining controlled risk exposure.

### 🎯 Core Purpose

The primary goal of this trading bot is to:
- **Generate high trading volume** through automated order placement and execution
- **Minimize trading friction** with intelligent order management
- **Support multiple DEX exchanges** through a unified interface
- **Provide risk management** through configurable parameters and safety mechanisms

### 🏗️ Architecture Overview

The project follows a **modular architecture** with clear separation of concerns:

```
perp-dex-tools/
├── exchanges/           # Exchange-specific implementations
│   ├── base.py         # Abstract base class for all exchanges
│   ├── factory.py      # Factory pattern for exchange creation
│   ├── edgex.py        # EdgeX exchange client
│   ├── backpack.py     # Backpack exchange client
│   ├── paradex.py      # Paradex exchange client
│   ├── aster.py        # Aster exchange client
│   ├── lighter.py      # Lighter exchange client
│   └── grvt.py         # GRVT exchange client
├── helpers/            # Utility modules
│   ├── logger.py       # Comprehensive logging system
│   ├── telegram_bot.py # Telegram notifications
│   └── lark_bot.py     # Lark notifications
├── trading_bot.py      # Core trading logic and strategy
├── runbot.py           # Command-line interface and entry point
└── tests/              # Test suite
```

### 🔄 Trading Strategy

The bot implements a **systematic trading approach**:

1. **Order Placement**: Places limit orders near market price
2. **Order Monitoring**: Waits for order execution
3. **Profit Taking**: Automatically places closing orders at profit targets
4. **Position Management**: Monitors positions and active orders
5. **Risk Control**: Limits maximum concurrent orders
6. **Grid Management**: Controls spacing between closing orders
7. **Price Controls**: Implements stop-loss and pause mechanisms

### 🎛️ Key Features

#### Multi-Exchange Support
- **EdgeX**: High-performance derivatives exchange
- **Backpack**: Solana-based trading platform
- **Paradex**: StarkNet-based DEX
- **Aster**: Advanced trading platform
- **Lighter**: Zero-knowledge trading protocol
- **GRVT**: Institutional-grade derivatives

#### Advanced Risk Management
- **Maximum Order Limits**: Prevents over-exposure
- **Grid Step Control**: Ensures proper order spacing
- **Price Stop/Pause**: Automatic trading suspension at critical levels
- **Position Monitoring**: Real-time position tracking
- **Error Handling**: Comprehensive error recovery

#### Flexible Configuration
- **Command-line Interface**: Easy parameter adjustment
- **Environment Variables**: Secure API key management
- **Multiple Accounts**: Support for multiple trading accounts
- **Customizable Parameters**: Fine-tune trading behavior

### 🛠️ Technical Implementation

#### Core Components

**TradingBot Class** (`trading_bot.py`):
- Main trading logic and state management
- WebSocket-based real-time order monitoring
- Asynchronous order execution and management
- Comprehensive error handling and recovery

**Exchange Factory** (`exchanges/factory.py`):
- Dynamic exchange client creation
- Unified interface for all supported exchanges
- Lazy loading of exchange-specific modules

**Base Exchange Client** (`exchanges/base.py`):
- Abstract interface for all exchange implementations
- Standardized order result structures
- Retry mechanisms for network operations

#### Key Technical Features

- **Asynchronous Programming**: Full async/await support for high performance
- **WebSocket Integration**: Real-time market data and order updates
- **Error Recovery**: Automatic retry mechanisms with exponential backoff
- **Thread Safety**: Safe concurrent operations
- **Comprehensive Logging**: Detailed transaction and debug logging
- **Notification System**: Telegram and Lark integration for alerts

### 📊 Trading Parameters

| Parameter | Description | Default | Purpose |
|-----------|-------------|---------|---------|
| `quantity` | Order size | 0.1 | Controls position size |
| `take-profit` | Profit target (%) | 0.02 | Sets profit margin |
| `max-orders` | Max concurrent orders | 40 | Risk management |
| `wait-time` | Order interval (seconds) | 450 | Prevents over-trading |
| `grid-step` | Order spacing (%) | -100 | Controls order density |
| `stop-price` | Emergency stop price | -1 | Risk control |
| `pause-price` | Trading pause price | -1 | Temporary suspension |

### 🚦 Usage Examples

#### Basic Trading
```bash
python runbot.py --exchange edgex --ticker ETH --quantity 0.1 --take-profit 0.02
```

#### Advanced Configuration
```bash
python runbot.py --exchange backpack --ticker BTC --quantity 0.05 --take-profit 0.02 --max-orders 30 --wait-time 600 --grid-step 0.5
```

#### Risk-Controlled Trading
```bash
python runbot.py --exchange aster --ticker ETH --quantity 0.1 --stop-price 5500 --pause-price 5400
```

### 🔒 Security & Risk Management

#### API Security
- Environment variable-based API key management
- Secure credential storage
- No hardcoded sensitive information

#### Trading Risk Controls
- Maximum order limits prevent over-exposure
- Price-based stop mechanisms
- Position monitoring and alerts
- Automatic error recovery

#### Operational Safety
- Graceful shutdown procedures
- Comprehensive error logging
- Real-time monitoring and alerts
- Manual intervention capabilities

### 📈 Performance Characteristics

- **High Throughput**: Asynchronous operations for maximum efficiency
- **Low Latency**: WebSocket-based real-time updates
- **Scalable**: Modular design supports easy addition of new exchanges
- **Reliable**: Comprehensive error handling and recovery mechanisms

---

## 中文版本

### 🚀 这是什么仓库？

这个仓库包含一个**模块化自动交易机器人**，专门为去中心化交易所（DEX）的永续期货交易而设计。该机器人实现了一个复杂的交易策略，专注于在保持可控风险敞口的同时产生高交易量。

### 🎯 核心目的

这个交易机器人的主要目标是：
- **产生高交易量**：通过自动化订单放置和执行
- **最小化交易摩擦**：通过智能订单管理
- **支持多个DEX交易所**：通过统一接口
- **提供风险管理**：通过可配置参数和安全机制

### 🏗️ 架构概览

项目采用**模块化架构**，具有清晰的关注点分离：

```
perp-dex-tools/
├── exchanges/           # 交易所特定实现
│   ├── base.py         # 所有交易所的抽象基类
│   ├── factory.py      # 交易所创建的工厂模式
│   ├── edgex.py        # EdgeX交易所客户端
│   ├── backpack.py     # Backpack交易所客户端
│   ├── paradex.py      # Paradex交易所客户端
│   ├── aster.py        # Aster交易所客户端
│   ├── lighter.py      # Lighter交易所客户端
│   └── grvt.py         # GRVT交易所客户端
├── helpers/            # 工具模块
│   ├── logger.py       # 综合日志系统
│   ├── telegram_bot.py # Telegram通知
│   └── lark_bot.py     # Lark通知
├── trading_bot.py      # 核心交易逻辑和策略
├── runbot.py           # 命令行界面和入口点
└── tests/              # 测试套件
```

### 🔄 交易策略

机器人实现了**系统性交易方法**：

1. **订单放置**：在市场价附近放置限价单
2. **订单监控**：等待订单执行
3. **获利了结**：在获利目标自动放置平仓单
4. **仓位管理**：监控仓位和活跃订单
5. **风险控制**：限制最大并发订单数
6. **网格管理**：控制平仓订单之间的间距
7. **价格控制**：实现止损和暂停机制

### 🎛️ 主要功能

#### 多交易所支持
- **EdgeX**：高性能衍生品交易所
- **Backpack**：基于Solana的交易平台
- **Paradex**：基于StarkNet的DEX
- **Aster**：高级交易平台
- **Lighter**：零知识交易协议
- **GRVT**：机构级衍生品

#### 高级风险管理
- **最大订单限制**：防止过度敞口
- **网格步长控制**：确保适当的订单间距
- **价格停止/暂停**：在关键水平自动暂停交易
- **仓位监控**：实时仓位跟踪
- **错误处理**：全面的错误恢复

#### 灵活配置
- **命令行界面**：易于参数调整
- **环境变量**：安全的API密钥管理
- **多账户**：支持多个交易账户
- **可定制参数**：微调交易行为

### 🛠️ 技术实现

#### 核心组件

**TradingBot类** (`trading_bot.py`)：
- 主要交易逻辑和状态管理
- 基于WebSocket的实时订单监控
- 异步订单执行和管理
- 全面的错误处理和恢复

**交易所工厂** (`exchanges/factory.py`)：
- 动态交易所客户端创建
- 所有支持交易所的统一接口
- 交易所特定模块的延迟加载

**基础交易所客户端** (`exchanges/base.py`)：
- 所有交易所实现的抽象接口
- 标准化订单结果结构
- 网络操作的重试机制

#### 关键技术特性

- **异步编程**：完全支持async/await以获得高性能
- **WebSocket集成**：实时市场数据和订单更新
- **错误恢复**：具有指数退避的自动重试机制
- **线程安全**：安全的并发操作
- **综合日志**：详细的交易和调试日志
- **通知系统**：Telegram和Lark集成用于警报

### 📊 交易参数

| 参数 | 描述 | 默认值 | 目的 |
|------|------|--------|------|
| `quantity` | 订单大小 | 0.1 | 控制仓位大小 |
| `take-profit` | 获利目标(%) | 0.02 | 设置利润边际 |
| `max-orders` | 最大并发订单 | 40 | 风险管理 |
| `wait-time` | 订单间隔(秒) | 450 | 防止过度交易 |
| `grid-step` | 订单间距(%) | -100 | 控制订单密度 |
| `stop-price` | 紧急停止价格 | -1 | 风险控制 |
| `pause-price` | 交易暂停价格 | -1 | 临时暂停 |

### 🚦 使用示例

#### 基础交易
```bash
python runbot.py --exchange edgex --ticker ETH --quantity 0.1 --take-profit 0.02
```

#### 高级配置
```bash
python runbot.py --exchange backpack --ticker BTC --quantity 0.05 --take-profit 0.02 --max-orders 30 --wait-time 600 --grid-step 0.5
```

#### 风险控制交易
```bash
python runbot.py --exchange aster --ticker ETH --quantity 0.1 --stop-price 5500 --pause-price 5400
```

### 🔒 安全与风险管理

#### API安全
- 基于环境变量的API密钥管理
- 安全凭证存储
- 无硬编码敏感信息

#### 交易风险控制
- 最大订单限制防止过度敞口
- 基于价格的停止机制
- 仓位监控和警报
- 自动错误恢复

#### 操作安全
- 优雅关闭程序
- 全面的错误日志
- 实时监控和警报
- 手动干预能力

### 📈 性能特征

- **高吞吐量**：异步操作以获得最大效率
- **低延迟**：基于WebSocket的实时更新
- **可扩展**：模块化设计支持轻松添加新交易所
- **可靠**：全面的错误处理和恢复机制

### ⚠️ 重要提醒

**风险警告**：加密货币交易涉及重大风险，可能导致重大财务损失。本软件仅供教育和研究目的。使用风险自负，切勿用您无法承受损失的资金进行交易。

**免责声明**：本软件仅供个人学习和研究使用，严禁用于任何商业用途。如需商业使用，请联系作者获取商业许可证。
