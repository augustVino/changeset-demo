# monorepo 项目

基于 pnpm + changeset 管理的 monorepo 项目

## 项目结构

```
.
├── packages
│   ├── react-components  # react 组件库
│   └── utils            # 通用工具函数库
├── .changeset           # changeset 配置
├── package.json
└── pnpm-workspace.yaml
```

## 技术栈

- pnpm workspace - monorepo 管理
- changesets - 版本管理和发布
- typescript - 类型安全
- tsup - 构建工具

## 安装依赖

```bash
pnpm install
```

## 开发

```bash
# 构建所有包
pnpm build

# 运行测试
pnpm test
```

## 版本管理

### 添加 changeset

当你完成了某个功能或修复后，使用以下命令创建 changeset：

```bash
pnpm changeset
```

根据提示选择：
1. 选择要更新的包
2. 选择版本类型（major/minor/patch）
3. 输入变更描述

### 应用版本变更

```bash
pnpm version-packages
```

这会根据 changeset 文件更新包的版本号和 CHANGELOG。

### 发布

```bash
pnpm release
```

这会构建所有包并发布到 npm registry。

## 包说明

### @monorepo/react-components

react 组件库，包含常用的 UI 组件。

```typescript
import { Button } from '@monorepo/react-components';

function App() {
  return <Button variant="primary">点击我</Button>;
}
```

### @monorepo/utils

通用工具函数库，提供常用的工具函数。

```typescript
import { formatDate, unique, chunk } from '@monorepo/utils';

// 格式化日期
formatDate(new Date()); // "2024-01-01"

// 数组去重
unique([1, 2, 2, 3]); // [1, 2, 3]

// 数组分块
chunk([1, 2, 3, 4, 5], 2); // [[1, 2], [3, 4], [5]]
```

## 注意事项

- 提交标题限制在 70 个字符以内且必须小写
- 使用 pnpm 而不是 npm 或 yarn
- 每次发布前确保所有包都通过了构建和测试
