<div align="right"><strong><a href="./README.md">🇨🇳中文</a></strong>  | <strong>🇬🇧English</strong></div>

# SuperTest API Automation Testing QuickStart Project

An introductory QuickStart project document on API automation testing with SuperTest.

- [SuperTest API Automation Testing QuickStart Project](#supertest-api-automation-testing-quickstart-project)
  - [Introduction](#introduction)
    - [Introduction of SuperTest](#introduction-of-supertest)
    - [Introduction of Jest](#introduction-of-jest)
    - [Introduction of Mocha](#introduction-of-mocha)
    - [Introduction of CHAI](#introduction-of-chai)
  - [Project dependencies](#project-dependencies)
  - [Project Structure](#project-structure)
  - [从 0 到 1 搭建 SuperTest 接口自动化测试项目](#从-0-到-1-搭建-supertest-接口自动化测试项目)
    - [Mocha 版本](#mocha-版本)
      - [新建项目文件夹](#新建项目文件夹)
      - [项目初始化](#项目初始化)
      - [安装依赖](#安装依赖)
      - [新建测试文件及测试用例](#新建测试文件及测试用例)
      - [编写测试用例](#编写测试用例)
      - [配置 mocha 配置文件](#配置-mocha-配置文件)
      - [调整测试脚本](#调整测试脚本)
      - [运行测试用例](#运行测试用例)
      - [测试报告](#测试报告)
        - [命令行测试报告](#命令行测试报告)
        - [集成 mochawesome 测试报告](#集成-mochawesome-测试报告)
    - [Jest 版本](#jest-版本)
      - [新建 Jest demo 项目文件夹](#新建-jest-demo-项目文件夹)
      - [Jest demo 项目初始化](#jest-demo-项目初始化)
      - [Jest demo 安装依赖](#jest-demo-安装依赖)
      - [新建 Jest demo 项目的测试文件及测试用例](#新建-jest-demo-项目的测试文件及测试用例)
      - [编写 Jest demo 测试用例](#编写-jest-demo-测试用例)
      - [配置 Jest 配置文件](#配置-jest-配置文件)
      - [调整 Jest 测试脚本](#调整-jest-测试脚本)
      - [运行 Jest 测试用例](#运行-jest-测试用例)
      - [Jest 测试报告](#jest-测试报告)
        - [Jest 命令行测试报告](#jest-命令行测试报告)
        - [集成 jest-html-reporters 测试报告](#集成-jest-html-reporters-测试报告)
  - [进阶用法](#进阶用法)
    - [持续集成](#持续集成)
      - [接入 github action](#接入-github-action)
        - [Mocha 版本接入 github action](#mocha-版本接入-github-action)
        - [Jest 版本接入 github action](#jest-版本接入-github-action)

## Introduction

This project is a quick start tutorial for API automation testing using SuperTest, and will use Jest or Mocha as the testing framework for demo demonstration.

We will introduce SuperTest, Jest and Mocha in turn, so that you can understand the basic usage of these tools in advance.

### Introduction of SuperTest

"Supertest" is a popular JavaScript library for testing Node.js applications. It is primarily used for end-to-end testing, also known as integration testing, to make sure that your application works properly across different components.Supertest is typically used in conjunction with testing frameworks such as Mocha, Jasmine or Jest to write and run test cases.

Here are some of the key features and uses of Supertest:

- Initiating HTTP requests: Supertest allows you to easily simulate HTTP requests such as GET, POST, PUT, DELETE, etc. to test your application's routing and endpoints.
- Chained Syntax: Supertest provides a chained syntax that allows you to build and execute multiple requests in a single test case, which helps simulate different user actions in your application.
- Assertions and Expectations: You can use Supertest in conjunction with assertion libraries such as Chai to examine the content of the response, status codes, headers, etc. to ensure the expected behavior of your application.
- Authentication Testing: Supertest can be used to test endpoints that require authentication to ensure that user login and authorization functions properly.
- Asynchronous support: Supertest can handle asynchronous operations, such as waiting for a response to return before executing further test code.
- Easy Integration: Supertest can be easily used with different Node.js frameworks (e.g. Express, Koa, Hapi, etc.), so you can test all types of applications.

Using Supertest can help you verify that your application is working as expected, as well as quickly catch potential problems when changes are made to your application. Typically, you need to install Supertest and the testing framework in your project, and then write test cases to simulate different requests and check responses. This helps improve code quality and maintainability and ensures that your application remains stable as it evolves.

Official documentation: <https://github.com/ladjs/supertest>

> Note: Supertest can be used not only for API testing, but also for unit and integration testing.

code examples:

```javascript
// import supertest
const request = require('supertest');

request({URL}) // request(url) or request(app)
.get() or .put() or.post() // http methods
.set() // http options
.send() // http body
.expect() // http assertions
.end() // end the request
```

### Introduction of Jest

Jest is a popular JavaScript testing framework for writing and running unit, integration and end-to-end tests for JavaScript applications. Its goal is to provide simple, fast and easy-to-use testing tools for a wide variety of JavaScript applications, both front-end and back-end.

Here are some of the key features and uses of Jest:

- Built-in Assertion Library: Jest includes a powerful assertion library that makes it easy to write assertions to verify that code behaves as expected.
- Automated mocks: Jest automatically creates mocks that help you simulate functions, modules, and external dependencies, making testing easier and more manageable.
- Fast and Parallel: Jest saves time by intelligently selecting which tests to run and executing them in parallel, allowing you to run a large number of test cases quickly.
- Comprehensive Test Suite: Jest supports unit, integration and end-to-end testing and can test a wide range of application types such as JavaScript, TypeScript, React, Vue, Node.js and more.
- Snapshot testing: Jest has a snapshot testing feature that can be used to capture UI changes by checking if the rendering of a UI component matches a previous snapshot.
- Automatic Watch Mode: Jest has a watch mode that automatically re-runs tests as code changes are made, supporting developers in continuous testing.
- Rich Ecosystem: Jest has a rich set of plug-ins and extensions that can be used to extend its functionality, such as coverage reporting, test reporting, and integration with other tools.
- Community Support: Jest is a popular testing framework with a large community that provides extensive documentation, tutorials and support resources.

Jest is often used in conjunction with other tools such as Babel (for transcoding JavaScript), Enzyme (for React component testing), Supertest (for API testing), etc. to achieve comprehensive test coverage and ensure code quality. Whether you're writing front-end or back-end code, Jest is a powerful testing tool that can help you catch potential problems and improve code quality and maintainability.

Official Documentation: <https://jestjs.io/docs/zh-Hans/getting-started>

Code examples:

```javascript
// import jest
const jest = require('jest');

describe(): // test scenarios

it(): // detailed test case, it() is in the describe()

before(): // this action is before all test cases

after(): // this action is after all test cases
```

### Introduction of Mocha

Mocha is a popular JavaScript testing framework for writing and running a variety of tests for JavaScript applications, including unit tests, integration tests, and end-to-end tests.Mocha provides flexibility and extensibility, allowing developers to easily customize the test suite to meet the needs of their projects.

Here are some of the key features and uses of Mocha:

- Multiple Test Styles: Mocha supports multiple test styles including BDD (Behavior Driven Development) and TDD (Test Driven Development). This allows developers to write test cases according to their preferences.
- Rich Assertion Library: Mocha does not include an assertion library by itself, but it can be used in conjunction with a variety of assertion libraries (e.g., Chai, Should.js, Expect.js, etc.), allowing you to write tests using your favorite assertion style.
- Asynchronous Testing: Mocha has built-in support for asynchronous testing, allowing you to test asynchronous code, Promises, callback functions, etc. to ensure that your code is correct in asynchronous scenarios.
- Parallel Testing: Mocha allows you to run test cases in your test suite in parallel, improving the efficiency of test execution.
- Rich Plug-ins and Extensions: Mocha has a rich ecosystem of plug-ins that can be used to extend its functionality, such as test coverage reporting, test report generation, and so on.
- Easy to Integrate: Mocha can be used with various assertion libraries, test runners (such as Karma and Jest), browsers (using the browser test runner), etc. to suit different project and testing needs.
- Command Line Interface: Mocha provides an easy-to-use command line interface for running test suites, generating reports, and other test-related operations.
- Continuous Integration Support: Mocha can be easily integrated into Continuous Integration (CI) tools such as Jenkins, Travis CI, CircleCI, etc. to ensure that code is tested after every commit.

Mocha's flexibility and extensibility make it a popular testing framework for a variety of JavaScript projects, including front-end and back-end applications. Developers can choose the testing tools, assertion libraries, and other extensions to meet the requirements of their projects based on their needs and preferences. Whether you are writing browser-side code or server-side code, Mocha is a powerful testing tool to help you ensure code quality and reliability.

Official documentation: <https://mochajs.org/>

Code examples:

```javascript
// import mocha
const mocha = require('mocha');

describe(): // test scenarios

it(): // detailed test case, it() is in the describe()

before(): // this action is before all test cases

after(): // this action is after all test cases
```

### Introduction of CHAI

Chai is a JavaScript assertion library for assertion and expectation validation when writing and running test cases. It is a popular testing tool that is often used in conjunction with testing frameworks (e.g. Mocha, Jest, etc.) to help developers write and execute various types of tests, including unit tests and integration tests.

Here are some of the key features and uses of Chai:

- Readable Assertion Syntax: Chai provides an easy to read and write assertion syntax that makes test cases easier to understand. It supports natural language assertion styles such as expect(foo).to.be.a('string') or expect(bar).to.equal(42).
- Multiple Assertion Styles: Chai provides a number of different assertion styles to suit different developer preferences. The main styles include BDD (Behavior-Driven Development) style, TDD (Test-Driven Development) style and assert style.
- Plugin extensions: Chai can be extended with plugins to support more assertion types and features. This allows Chai to fulfill a variety of testing needs, including asynchronous testing, HTTP request testing, and more.
- Easy Integration: Chai can be easily integrated with various testing frameworks such as Mocha, Jest, Jasmine etc. This makes it a powerful tool for writing test cases.
- Chained Assertions Support: Chai allows you to chain calls to multiple assertions to make complex testing and validation easier.

Official documentation: <https://www.chaijs.com/>

Code examples:

```javascript
// import chai
const chai = require('chai');
const expect = chai.expect;

// demo assertions
.expect(<actual result>).to.{assert}(<expected result>) // Asserts that the target is strictly equal to value.

.expect(‘hello').to.equal('hello'); // Asserts that the target is strictly equal to value.

.expect({ foo: 'bar' }).to.not.equal({ foo: 'bar' }); // Asserts that the target is not strictly equal to value.

.expect('foobar').to.contain('foo'); // Asserts that the target contains the given substring.

.expect(foo).to.exist; // Asserts that the target is neither null nor undefined.

.expect(5).to.be.at.most(5); // Asserts that the target is less than or equal to value.
```

## Project dependencies

> The following environments need to be installed in advance

- [x] nodejs, demo version v21.1.0

## Project Structure

The following is the file structure of a SuperTest Interface Automation Test project, which contains test configuration files, test case files, test tool files, and test report files. It can be used for reference.

```Text
SuperTest-Jest-demo
├── README.md
├── package.json
├── package-lock.json
├── Config // Test configuration 
│   └── config.js
├── Specs // Test case 
│   └── test.spec.js
├── Utils // Test tool 
│   └── utils.js
├── Report // Test report 
│   └── report.html
├── .gitignore
└── node_modules // Project dependencies
    ├── ...
    └── ...
```

## 从 0 到 1 搭建 SuperTest 接口自动化测试项目

下面会从 0 到 1 搭建一个 SuperTest 接口自动化测试项目，会使用 Jest 或 Mocha 作为测试框架进行 demo 演示。

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

> 测试接口可参考项目中 demoAPI.md 文件

```javascript
// Test: test.spec.js
const request = require('supertest'); // import supertest
const chai = require('chai'); // import chai
const expect = require('chai').expect; // import expect

// Test Suite
describe('Verify that the Get and POST API returns correctly', function(){
        // Test case 1
        it('Verify that the GET API returns correctly', function(done){
            request('https://jsonplaceholder.typicode.com') // Test endpoint
                .get('/posts/1') // API endpoint
                .expect(200) // expected response status code
                .expect(function (res) {
                    expect(res.body.id).to.equal(1  )
                    expect(res.body.userId).to.equal(1)
                    expect(res.body.title).to.equal("sunt aut facere repellat provident occaecati excepturi optio reprehenderit")
                    expect(res.body.body).to.equal("quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto")
                }) // expected response body
                .end(done) // end the test case

        });
        // Test case 2
        it('Verify that the POST API returns correctly', function(done){
            request('https://jsonplaceholder.typicode.com') // Test endpoint
                .post('/posts') // API endpoint
                .send({
                    "title": "foo",
                    "body": "bar",
                    "userId": 1
                }) // request body
                .expect(201) // expected response status code
                .expect(function (res) {
                    expect(res.body.id).to.equal(101  )
                    expect(res.body.userId).to.equal(1)
                    expect(res.body.title).to.equal("foo")
                    expect(res.body.body).to.equal("bar")
                }) // expected response body
                .end(done) // end the test case
        });
});
```

#### 配置 mocha 配置文件

- 新建配置文件

```bash
// 项目根目录下新建配置文件
touch .mocharc.js
```

- 更新配置文件

```javascript
// mocha config
module.exports = {
    timeout: 5000, // 设置测试用例的默认超时时间（毫秒）
    spec: ['Specs/**/*.js'], // 指定测试文件的位置
};
```

#### 调整测试脚本

在 package.json 文件中添加测试脚本

```json
"scripts": {
    "test": "mocha"
  },
```

#### 运行测试用例

```bash
// 运行测试用例
npm run test
```

#### 测试报告

##### 命令行测试报告

![RbdVs7](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/RbdVs7.png)

##### 集成 mochawesome 测试报告

- 安装 mochawesome

```bash
npm install --save-dev mochawesome
```

- 更新 mocha 配置文件

> 可参考 demo 项目：<https://github.com/Automation-Test-Starter/SuperTest-Mocha-demo>

```javascript
// mocha config
module.exports = {
    timeout: 5000, // 设置测试用例的默认超时时间（毫秒）
    reporter: 'mochawesome', // 使用 mochawesome 报告生成器
    'reporter-option': [
        'reportDir=Report', // 报告生成路径
        'reportFilename=[status]_[datetime]-[name]-report', //报告名称
        'html=true', // 生成 html 格式报告
        'json=false', // 不生成 json 格式报告
        'overwrite=false', // 不覆盖已经存在的报告
        'timestamp=longDate', // 给报告添加时间戳

    ], // 传递给报告生成器的参数
    spec: ['Specs/**/*.js'], // 指定测试文件的位置
};
```

- 运行测试用例

```bash
// 运行测试用例
npm run test
```

- 查看测试报告

> 测试报告文件夹：Report，点击使用浏览器打开最新 html 报告文件

![BseOQ8](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/BseOQ8.png)

### Jest 版本

可参考 demo 项目：<https://github.com/Automation-Test-Starter/SuperTest-Jest-demo>

#### 新建 Jest demo 项目文件夹

```bash
mkdir SuperTest-Jest-demo
```

#### Jest demo 项目初始化

```bash
// 进入项目文件夹下
cd SuperTest-Mocha-demo
// nodejs 项目初始化
npm init -y
```

#### Jest demo 安装依赖

```bash
// 安装 supertest
npm install supertest --save-dev
// 安装 Jest测试框架
npm install jest --save-dev
```

#### 新建 Jest demo 项目的测试文件及测试用例

```bash
// 新建测试文件夹
mkdir Specs
// 新建测试用例文件
cd Specs
touch test.spec.js
```

#### 编写 Jest demo 测试用例

> 测试接口可参考项目中 demoAPI.md 文件

```javascript
const request = require('supertest');

// Test Suite
describe('Verify that the Get and POST API returns correctly', () => {
    // Test case 1
    it('Verify that the GET API returns correctly', async () => {
        const res = await request('https://jsonplaceholder.typicode.com') // Test endpoint
            .get('/posts/1') // API endpoint
            .send() // request body
            .expect(200); // use supertest's expect to verify that the status code is 200
        // user jest's expect to verify the response body
        expect(res.status).toBe(200); // Verify that the status code is 200
        expect(res.body.id).toEqual(1); // Verify that the id is 1
        expect(res.body.userId).toEqual(1); // Verify that the userId is 1
        expect(res.body.title).toEqual("sunt aut facere repellat provident occaecati excepturi optio reprehenderit");
        expect(res.body.body).toEqual("quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto");
    });

    // Test case 2
    it('Verify that the POST API returns correctly', async() =>{
        const res = await request('https://jsonplaceholder.typicode.com') // Test endpoint
            .post('/posts') // API endpoint
            .send({
                "title": "foo",
                "body": "bar",
                "userId": 1
            }) // request body
            .expect(201); // use supertest's expect to verify that the status code is 201
        // user jest's expect to verify the response body
        expect(res.statusCode).toBe(201);
        expect(res.body.id).toEqual(101);
        expect(res.body.userId).toEqual(1);
        expect(res.body.title).toEqual("foo");
        expect(res.body.body).toEqual("bar");
    });
}); 
```

#### 配置 Jest 配置文件

- 新建配置文件

```bash
// 项目根目录下新建配置文件
touch jest.config.js
```

- 更新配置文件

```javascript
// Desc: Jest configuration file
module.exports = {
    // 测试文件的匹配规则
    testMatch: ['**/Specs/*.spec.js'],
};
```

#### 调整 Jest 测试脚本

在 package.json 文件中添加测试脚本

```json
"scripts": {
    "test": "jest"
  },
```

#### 运行 Jest 测试用例

```bash
// 运行测试用例
npm run test
```

#### Jest 测试报告

##### Jest 命令行测试报告

![ItJf6N](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/ItJf6N.png)

##### 集成 jest-html-reporters 测试报告

- 安装 jest-html-reporters

```bash
npm install --save-dev jest-html-reporters
```

- 更新 Jest 配置文件

> 可参考 demo 项目：<https://github.com/Automation-Test-Starter/SuperTest-Jest-demo>

```javascript
// Desc: Jest configuration file
module.exports = {
    // 测试文件的匹配规则
    testMatch: ['**/Specs/*.spec.js'],
    // 测试报告生成器
    reporters: [
        'default',
        [
            'jest-html-reporters',
            {
                publicPath: './Report', // 报告生成路径
                filename: 'report.html', // 报告名称
                pageTitle: 'SuperTest and Jest API Test Report', // 报告标题
                overwrite: true, // 报告文件是否覆盖
                expand: true, // 展开所有测试套件
            },
        ],
    ],
};
```

- 运行 Jest 测试用例

```bash
// 运行测试用例
npm run test
```

- 查看测试报告

> 测试报告文件夹：Report，点击使用浏览器打开最新 html 报告文件

![12ZreT](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/12ZreT.png)

## 进阶用法

### 持续集成

#### 接入 github action

以 github action 为例，其他 CI 工具类似

##### Mocha 版本接入 github action

可参考 demo：<https://github.com/Automation-Test-Starter/SuperTest-Mocha-demo>

创建.github/workflows 目录：在你的 GitHub 仓库中，创建一个名为 .github/workflows 的目录。这将是存放 GitHub Actions 工作流程文件的地方。

创建工作流程文件：在.github/workflows 目录中创建一个 YAML 格式的工作流程文件，例如 mocha.yml。

编辑 mocha.yml 文件：将以下内容复制到文件中
  
```yaml
name: RUN SuperTest API Test CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  RUN-SuperTest-API-Test:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [ 18.x]
        # See supported Node.js release schedule at https://nodejs.org/en/about/releases/

    steps:
    - uses: actions/checkout@v3
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
        
    - name: Installation of related packages
      run: npm ci
      
    - name: RUN SuperTest API Testing
      run: npm test
      
    - name: Archive SuperTest mochawesome test report
      uses: actions/upload-artifact@v3
      with:
        name: SuperTest-mochawesome-test-report
        path: Report

    - name: Upload SuperTest mochawesome report to GitHub
      uses: actions/upload-artifact@v3
      with:
        name: SuperTest-mochawesome-test-report
        path: Report
```

- 提交代码：将 mocha.yml 文件添加到仓库中并提交。
- 查看测试报告：在 GitHub 中，导航到你的仓库。单击上方的 Actions 选项卡，然后单击左侧的 RUN SuperTest API Test CI 工作流。你应该会看到工作流正在运行，等待执行完成，就可以查看结果。

![dgfyaS](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/dgfyaS.png)

##### Jest 版本接入 github action

可参考 demo：<https://github.com/Automation-Test-Starter/SuperTest-Jest-demo>

创建.github/workflows 目录：在你的 GitHub 仓库中，创建一个名为 .github/workflows 的目录。这将是存放 GitHub Actions 工作流程文件的地方。

创建工作流程文件：在.github/workflows 目录中创建一个 YAML 格式的工作流程文件，例如 jest.yml。

编辑 jest.yml 文件：将以下内容复制到文件中
  
```yaml
name: RUN SuperTest API Test CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  RUN-SuperTest-API-Test:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [ 18.x]
        # See supported Node.js release schedule at https://nodejs.org/en/about/releases/

    steps:
      - uses: actions/checkout@v3
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'

      - name: Installation of related packages
        run: npm ci

      - name: RUN SuperTest API Testing
        run: npm test

      - name: Archive SuperTest test report
        uses: actions/upload-artifact@v3
        with:
          name: SuperTest-test-report
          path: Report

      - name: Upload SuperTest  report to GitHub
        uses: actions/upload-artifact@v3
        with:
          name: SuperTest-test-report
          path: Report
```

- 提交代码：将 jest.yml 文件添加到仓库中并提交。
- 查看测试报告：在 GitHub 中，导航到你的仓库。单击上方的 Actions 选项卡，然后单击左侧的 RUN-SuperTest-API-Test 工作流。你应该会看到工作流正在运行，等待执行完成，就可以查看结果。

![fqXy8o](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/fqXy8o.png)
