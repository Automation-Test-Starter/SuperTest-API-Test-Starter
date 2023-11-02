<div align="right"><strong>🇨🇳中文</a></strong>  | <strong><a href="./README_EN.md">🇬🇧English</strong></div>

# SuperTest 接口自动化测试快速启动项目

关于使用 SuperTest 进行 API 自动化测试的快速启动项目介绍文档。

- [SuperTest 接口自动化测试快速启动项目](#supertest-接口自动化测试快速启动项目)
  - [介绍](#介绍)
    - [SuperTest介绍](#supertest介绍)
    - [Jest 介绍](#jest-介绍)
    - [Mocha 介绍](#mocha-介绍)
  - [项目依赖](#项目依赖)
  - [项目文件结构](#项目文件结构)
  - [从 0 到 1 搭建 SuperTest 接口自动化测试项目](#从-0-到-1-搭建-supertest-接口自动化测试项目)
    - [Mocha 版本](#mocha-版本)
      - [新建项目文件夹](#新建项目文件夹)
      - [项目初始化](#项目初始化)
      - [安装依赖](#安装依赖)
      - [新建测试文件及测试用例](#新建测试文件及测试用例)
      - [编写测试用例](#编写测试用例)

## 介绍

本项目是一个使用 SuperTest 进行 API 自动化测试的快速启动项目教程，会使用 Jest 或 Mocha 作为测试框架进行demo演示。

下面会依次介绍 SuperTest、Jest 和 Mocha,让大家提前了解这些工具的基本使用。

### SuperTest介绍

"Supertest" 是一个用于测试 Node.js 应用程序的流行 JavaScript 库。它主要用于进行端到端（End-to-End）测试，也称为集成测试，以确保你的应用程序在不同组件之间正常运行。Supertest 通常与 Mocha、Jasmine 或 Jest 等测试框架一起使用，以编写和运行测试用例。

以下是 Supertest 的一些关键特点和用途：

- 发起 HTTP 请求：Supertest 允许你轻松地模拟 HTTP 请求，例如 GET、POST、PUT、DELETE 等，以测试你的应用程序的路由和端点。
- 链式语法：Supertest 提供了一种链式语法，使你能够在单个测试用例中构建和执行多个请求，这有助于模拟用户在应用程序中的不同操作。
- 断言和期望：你可以使用 Supertest 结合断言库（如 Chai）来检查响应的内容、状态码、头信息等，以确保应用程序的期望行为。
- 身份验证测试：Supertest 可以用于测试需要身份验证的端点，以确保用户登录和授权功能正常。
- 异步支持：Supertest 可以处理异步操作，例如等待响应返回后执行进一步的测试代码。
- 方便的集成：Supertest 可以轻松与不同的 Node.js 框架（如 Express、Koa、Hapi 等）一起使用，因此你可以测试各种类型的应用程序。

使用 Supertest 可以帮助你验证你的应用程序是否按预期工作，以及在应用程序发生更改时快速捕获潜在的问题。通常，你需要在项目中安装 Supertest 和测试框架，然后编写测试用例来模拟不同的请求和检查响应。这有助于提高代码质量和可维护性，确保你的应用程序在不断演化的过程中保持稳定性。

官方文档：<https://github.com/ladjs/supertest>

> 备注：Supertest不止可以用来做API测试，也可以用来做单元测试和集成测试

### Jest 介绍

Jest 是一个流行的 JavaScript 测试框架，用于编写和运行 JavaScript 应用程序的单元测试、集成测试和端到端测试。它的目标是提供简单、快速和易于使用的测试工具，适用于各种 JavaScript 应用程序，包括前端和后端应用程序。

以下是 Jest 的一些关键特点和用途：

- 内置断言库：Jest 包括一个强大的断言库，使你能够轻松地编写断言，以验证代码的行为是否符合预期。
- 自动模拟：Jest 自动创建模拟（mocks），帮助你模拟函数、模块和外部依赖，从而让测试更加简单和可控。
- 快速和并行：Jest 通过智能地选择要运行的测试以及并行执行测试，可以快速地运行大量测试用例，从而节省时间。
- 全面的测试套件：Jest 支持单元测试、集成测试和端到端测试，并可以测试 JavaScript、TypeScript、React、Vue、Node.js 等各种应用程序类型。
- 快照测试：Jest 具有快照测试功能，可用于检查 UI 组件的渲染是否与之前的快照匹配，从而捕获 UI 变化。
- 自动监视模式：Jest 具有一个监视模式，可在代码更改时自动重新运行相关测试，从而支持开发人员进行持续测试。
- 丰富的生态系统：Jest 有丰富的插件和扩展，可用于扩展其功能，如覆盖率报告、测试报告和其他工具的集成。
- 社区支持：Jest 是一个流行的测试框架，拥有庞大的社区，提供了大量的文档、教程和支持资源。

Jest通常与其他工具如Babel（用于转译 JavaScript）、Enzyme（用于 React 组件测试）、Supertest（用于 API 测试）等一起使用，以实现全面的测试覆盖和确保代码质量。无论你是在编写前端代码还是后端代码，Jest都是一个强大的测试工具，可以帮助你捕获潜在的问题，提高代码质量和可维护性。

官方文档：<https://jestjs.io/docs/zh-Hans/getting-started>

### Mocha 介绍

Mocha 是一个流行的 JavaScript 测试框架，用于编写和运行 JavaScript 应用程序的各种测试，包括单元测试、集成测试和端到端测试。Mocha 提供了灵活性和可扩展性，使开发人员能够轻松地定制测试套件以满足其项目的需求。

以下是 Mocha 的一些关键特点和用途：

- 多种测试风格：Mocha 支持多种测试风格，包括 BDD（行为驱动开发）和 TDD（测试驱动开发）。这使开发人员可以根据自己的偏好编写测试用例。
- 丰富的断言库：Mocha 本身并不包括断言库，但它可以与多种断言库（如 Chai、Should.js、Expect.js 等）结合使用，使你能够使用喜欢的断言风格来编写测试。
- 异步测试：Mocha 内置支持异步测试，允许你测试异步代码、Promise、回调函数等，确保代码在异步场景下的正确性。
- 并行测试：Mocha 可以并行运行测试套件中的测试用例，提高测试执行效率。
- 丰富的插件和扩展：Mocha 有丰富的插件生态系统，可以用于扩展其功能，如测试覆盖率报告、测试报告生成等。
- 易于集成：Mocha 可以与各种断言库、测试运行器（如 Karma 和 Jest）、浏览器（使用浏览器测试运行器）等一起使用，以适应不同的项目和测试需求。
- 命令行界面：Mocha 提供了一个易于使用的命令行界面，用于运行测试套件，生成报告以及其他测试相关操作。
- 持续集成支持：Mocha 可以轻松集成到持续集成（CI）工具中，如 Jenkins、Travis CI、CircleCI 等，以确保代码在每次提交后都能得到测试。

Mocha 的灵活性和可扩展性使其成为一个受欢迎的测试框架，适用于各种 JavaScript 项目，包括前端和后端应用程序。开发人员可以根据自己的需求和喜好选择测试工具、断言库和其他扩展，以满足项目的要求。无论你是在编写浏览器端代码还是服务器端代码，Mocha 都是一个强大的测试工具，可帮助你确保代码质量和可靠性。

官方文档：<https://mochajs.org/>

## 项目依赖

> 需提前安装好以下环境

- [x] nodejs, demo 版本为 v21.1.0

## 项目文件结构

以下是一个 SuperTest 接口自动化测试项目的文件结构，其中包含了测试配置文件、测试用例文件、测试工具文件和测试报告文件。可进行参考。

```Text
SuperTest-Jest-demo
├── README.md
├── package.json
├── package-lock.json
├── Config // 测试配置文件
│   └── config.js
├── Specs // 测试用例文件
│   └── test.spec.js
├── Utils // 测试工具文件
│   └── utils.js
├── Report // 测试报告文件
│   └── report.html
├── .gitignore
└── node_modules // 项目依赖
```

## 从 0 到 1 搭建 SuperTest 接口自动化测试项目

下面会从 0 到 1 搭建一个 SuperTest 接口自动化测试项目，会使用 Jest 或 Mocha 作为测试框架进行demo演示。

### Mocha 版本

可参考 demo 项目：<https://github.com/Automation-Test-Starter/SuperTest-Mocha-demo>

#### 新建项目文件夹

```bash
mkdir SuperTest-Mocha-demo
```

#### 项目初始化

```bash
// 进入项目文件夹下
cd SuperTest-Mocha-demo
// nodejs 项目初始化
npm init -y
```

#### 安装依赖

```bash
// 安装 supertest
npm install supertest --save-dev
// 安装 mocha测试框架
npm install mocha --save-dev
// 安装 chai断言库
npm install chai --save-dev
```

#### 新建测试文件及测试用例

```bash
// 新建测试文件夹
mkdir Specs
// 新建测试用例文件
cd Specs
touch test.spec.js
```

#### 编写测试用例

> 测试接口可参考项目中 demoAPI.md文件

```typescript
// 引入 supertest
const request = require('supertest');

