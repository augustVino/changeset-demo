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

## **开发工作流**

`修改代码→发布预发布版本，并打tag→使用预发布版本进行测试→测试通过后，修改版本号为正式版→发布正式版`

### 使用 changesets 工作流

可手动选择本次需要更新版本的包，同时自动生成 changelog 文件。

1.进入预发布模式(beta 可修改为需要的 Npm dist tag)

`pnpm run changeset:beta`

2.在开发分支上修改代码后，生成 changeset 文件

`pnpm run changeset`

3.编译打包并修改版本号
`pnpm run version`

4.review 版本修改后进行代码提交 5.发布版本

`pnpm run publish`

6.发布新的预发布版本时重新执行第 2 步。直到测试完成后，退出预发布模式

`pnpm run changeset:exit`
