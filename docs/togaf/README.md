# Single-SPA TOGAF 企业架构图

本目录包含了基于 TOGAF (The Open Group Architecture Framework) 框架为 single-spa 项目创建的企业架构图。所有架构图使用 PlantUML 格式编写，可以通过 PlantUML 工具或支持 PlantUML 的编辑器查看和渲染。

## 架构图文件说明

### 1. 业务架构图 (business-architecture.puml)

描述 single-spa 项目的业务层面架构，包括：

- **业务目标层**：提供微前端框架解决方案的核心目标和价值主张
- **业务流程层**：应用注册、路由管理、生命周期管理等核心业务流程
- **业务能力层**：应用注册、路由导航、生命周期管理、多框架支持等业务能力
- **利益相关者层**：前端开发者、企业架构师、最终用户、开源社区等
- **业务服务层**：应用注册服务、路由协调服务、状态管理服务等

### 2. 应用架构图 (application-architecture.puml)

描述 single-spa 的应用组件架构，包括：

- **应用接口层**：公开的 API 接口（registerApplication、start、navigateToUrl 等）
- **核心应用层**：应用管理器、启动管理器、导航事件管理、路由协调器等核心模块
- **生命周期管理层**：加载、引导、挂载、卸载、更新等生命周期处理模块
- **应用状态管理层**：应用状态定义、状态转换逻辑、超时管理、错误处理
- **功能扩展层**：Parcel 管理器、开发工具、性能分析器、jQuery 支持等
- **工具支撑层**：运行时环境检测、对象分配工具、查找工具等工具函数

### 3. 数据架构图 (data-architecture.puml)

描述 single-spa 的数据模型和状态流转，包括：

- **应用状态模型**：完整的状态转换图（NOT_LOADED → MOUNTED → UNMOUNTING 等）
- **应用数据对象**：应用对象的结构定义和属性
- **应用变更数据**：应用变更列表的数据结构
- **事件数据结构**：导航事件、PopState 事件、HashChange 事件等
- **生命周期属性数据**：传递给生命周期函数的属性对象
- **Parcel 数据对象**：Parcel 对象的结构定义
- **错误数据结构**：应用错误的数据结构
- **数据存储位置**：应用注册表、当前 URL、错误处理器列表等存储位置

### 4. 技术架构图 (technology-architecture.puml)

描述 single-spa 的技术栈和构建架构，包括：

- **运行时环境层**：浏览器环境和 Node.js 环境
- **编程语言层**：JavaScript ES2015+、ES Modules、CommonJS、TypeScript 类型定义
- **核心框架层**：Single-SPA 核心模块和配置模块
- **构建工具层**：Rollup、Babel 及相关插件
- **开发工具层**：Jest 测试框架、ESLint、Prettier、TSD 等代码质量工具
- **包管理工具层**：PNPM 包管理器
- **构建输出层**：开发版本、生产版本、类型定义文件的输出
- **浏览器兼容性**：支持的浏览器版本列表

### 5. 总体架构概览图 (overview.puml)

展示四层架构的整体关系和跨层交互：

- **业务架构层**：业务目标、流程、能力、服务和利益相关者
- **应用架构层**：应用接口、核心模块、生命周期管理、状态管理、功能扩展、工具支撑
- **数据架构层**：状态模型、数据对象、事件数据、数据存储、数据流转
- **技术架构层**：运行时环境、编程语言、核心框架、构建工具、开发工具、浏览器兼容性

包含跨层关系说明和架构原则标注。

## 如何使用

### 在线查看

1. 访问 [PlantUML Online Server](http://www.plantuml.com/plantuml/uml/)
2. 打开对应的 `.puml` 文件，复制内容到在线编辑器
3. 点击渲染按钮查看图表

### 本地查看

#### 方法 1：使用 VS Code 插件

1. 在 VS Code 中安装 "PlantUML" 插件
2. 打开 `.puml` 文件
3. 使用 `Alt + D` 或右键选择 "Preview Current Diagram" 预览图表

#### 方法 2：使用命令行工具

1. 安装 PlantUML：

```bash
# macOS
brew install plantuml

# 或使用 Java 和 JAR 包
# 下载 plantuml.jar 并运行
java -jar plantuml.jar *.puml
```

2. 生成图片：

```bash
cd docs/togaf
plantuml *.puml
```

#### 方法 3：使用 Docker

```bash
docker run -d -p 8080:8080 plantuml/plantuml-server:jetty
# 然后访问 http://localhost:8080
```

### 导出为其他格式

PlantUML 支持导出多种格式：

```bash
# PNG 格式
plantuml -tpng *.puml

# SVG 格式
plantuml -tsvg *.puml

# PDF 格式
plantuml -tpdf *.puml
```

## 架构图关系说明

### 架构层次关系

```
业务架构层 (What & Why)
    ↓ 实现
应用架构层 (How - Application)
    ↓ 使用
数据架构层 (What - Data)
    ↓ 运行在
技术架构层 (How - Technology)
```

### 跨层交互

- **业务 → 应用**：业务需求通过应用接口和核心模块实现
- **应用 → 数据**：应用模块操作和管理数据对象及状态
- **数据 → 技术**：数据模型在技术栈上实现和存储
- **应用 → 技术**：应用组件依赖技术栈和运行时环境

## TOGAF 架构原则

所有架构图遵循 TOGAF 标准原则：

1. **业务驱动**：业务需求驱动技术决策
2. **模块化**：组件高内聚、低耦合
3. **标准化**：使用标准技术和接口
4. **可扩展性**：支持功能扩展和演进
5. **可维护性**：清晰的架构便于维护和理解

## 参考资料

- [TOGAF 官方文档](https://www.opengroup.org/togaf)
- [PlantUML 官方文档](https://plantuml.com/)
- [Single-SPA 官方文档](https://single-spa.js.org/)
- [Single-SPA GitHub 仓库](https://github.com/single-spa/single-spa)

## 维护说明

这些架构图基于 single-spa 项目当前代码结构生成。如果项目架构发生变化，请及时更新相应的架构图文件，以保持架构文档与代码的一致性。

### 更新建议

- 当添加新的核心模块时，更新应用架构图
- 当状态模型发生变化时，更新数据架构图
- 当技术栈发生变化时，更新技术架构图
- 当业务需求变化时，更新业务架构图

## 文件列表

```
docs/togaf/
├── README.md                      # 本说明文档
├── business-architecture.puml     # 业务架构图
├── application-architecture.puml  # 应用架构图
├── data-architecture.puml         # 数据架构图
├── technology-architecture.puml   # 技术架构图
└── overview.puml                  # 总体架构概览图
```

