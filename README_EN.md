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
  - [Build a SuperTest interface automation test project from 0 to 1](#build-a-supertest-interface-automation-test-project-from-0-to-1)
    - [Mocha version](#mocha-version)
      - [Create a new project folder](#create-a-new-project-folder)
      - [Project Initialization](#project-initialization)
      - [Install dependencies](#install-dependencies)
      - [Create new test folder and test cases](#create-new-test-folder-and-test-cases)
      - [Writing Test Cases](#writing-test-cases)
      - [Configuring mocha config files](#configuring-mocha-config-files)
      - [Updating test scripts for mocha](#updating-test-scripts-for-mocha)
      - [Running test cases](#running-test-cases)
      - [Test Report](#test-report)
        - [Terminal Test Report](#terminal-test-report)
        - [Integrated mochawesome test report](#integrated-mochawesome-test-report)
    - [Jest version](#jest-version)
      - [Create a new jest project folder](#create-a-new-jest-project-folder)
      - [Jest demo project initialization](#jest-demo-project-initialization)
      - [Jest demo install dependencies](#jest-demo-install-dependencies)
      - [Create new Jest demo project test folder and test cases](#create-new-jest-demo-project-test-folder-and-test-cases)
      - [Writing Jest demo Test Cases](#writing-jest-demo-test-cases)
      - [Configuring Jest config files](#configuring-jest-config-files)
      - [Adapting Jest Test Scripts](#adapting-jest-test-scripts)
      - [Runing test case](#runing-test-case)
      - [Jest test report](#jest-test-report)
        - [Jest terminal Test Report](#jest-terminal-test-report)
        - [Integrating jest-html-reporters test reports](#integrating-jest-html-reporters-test-reports)
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

## Build a SuperTest interface automation test project from 0 to 1

The following is a demo of building a SuperTest interface automation test project from 0 to 1, using either Jest or Mocha as the test framework.

### Mocha version

You can refer to the demo project at <https://github.com/Automation-Test-Starter/SuperTest-Mocha-demo>.

#### Create a new project folder

```bash
mkdir SuperTest-Mocha-demo
```

#### Project Initialization

```bash
// enter the project folder
cd SuperTest-Mocha-demo
// nodejs project initialization
npm init -y
```

#### Install dependencies

```bash
// install supertest library
npm install supertest --save-dev
// install mocha test framework
npm install mocha --save-dev
// install chai assertion library
npm install chai --save-dev
```

#### Create new test folder and test cases

```bash
// create test folder
mkdir Specs
// create test case file
cd Specs
touch test.spec.js
```

#### Writing Test Cases

> The test API can be found in the demoAPI.md file in the project.

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

#### Configuring mocha config files

- Create a new mocha configuration file

```bash
// create configuration file in the project root directory
touch .mocharc.js
```

- Updating configuration files

```javascript
// mocha config
module.exports = {
    timeout: 5000, // set the default timeout for test cases (milliseconds)
    spec: ['Specs/**/*.js'], // specify the location of the test file
};
```

#### Updating test scripts for mocha

Add test scripts to the package.json file

```json
"scripts": {
    "test": "mocha"
  },
```

#### Running test cases

```bash
// run test cases
npm run test
```

#### Test Report

##### Terminal Test Report

![RbdVs7](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/RbdVs7.png)

##### Integrated mochawesome test report

- Install mochawesome library

```bash
npm install --save-dev mochawesome
```

- Updating mocha configuration files

> You can refer to the demo project at<https://github.com/Automation-Test-Starter/SuperTest-Mocha-demo>

```javascript
// mocha config
module.exports = {
    timeout: 5000, // Set the default timeout for test cases (milliseconds)
    reporter: 'mochawesome', // Use mochawesome as the test report generator
    'reporter-option': [
        'reportDir=Report', // Report directory
        'reportFilename=[status]_[datetime]-[name]-report', //Report file name
        'html=true', // enable html report
        'json=false', // disable json report
        'overwrite=false', // disable report file overwrite
        'timestamp=longDate', // add timestamp to report file name

    ], // mochawesome report generator options
    spec: ['Specs/**/*.js'], // Specify the location of the test file
};
```

- Running test cases

```bash
// Run test cases
npm run test
```

- View test report

> Test report folder: Report, click to open the latest html report file with your browser

![BseOQ8](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/BseOQ8.png)

### Jest version

 You can refer to the demo project at<https://github.com/Automation-Test-Starter/SuperTest-Jest-demo>

#### Create a new jest project folder

```bash
mkdir SuperTest-Jest-demo
```

#### Jest demo project initialization

```bash
// enter the project folder
cd SuperTest-Mocha-demo
// nodejs project initialization
npm init -y
```

#### Jest demo install dependencies

```bash
// install supertest library
npm install supertest --save-dev
// install jest test framework
npm install jest --save-dev
```

#### Create new Jest demo project test folder and test cases

```bash
// create test folder
mkdir Specs
// enter test folder and create test case file
cd Specs
touch test.spec.js
```

#### Writing Jest demo Test Cases

> The test API can be found in the demoAPI.md file in the project.

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

#### Configuring Jest config files

- Creating a new configuration file

```bash
// Create a new configuration file in the project root directory
touch jest.config.js
```

- Updating configuration files

```javascript
// Desc: Jest configuration file
module.exports = {
    // Specify the location of the test file
    testMatch: ['**/Specs/*.spec.js'],
};
```

#### Adapting Jest Test Scripts

Add the test script to the package.json file

```json
"scripts": {
    "test": "jest"
  },
```

#### Runing test case

```bash
// run test case
npm run test
```

#### Jest test report

##### Jest terminal Test Report

![ItJf6N](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/ItJf6N.png)

##### Integrating jest-html-reporters test reports

- Install jest-html-reporters library

```bash
npm install --save-dev jest-html-reporters
```

- Updating jest configuration files

> You can refer to the demo project at<ttps://github.com/Automation-Test-Starter/SuperTest-Jest-demo>

```javascript
// Desc: Jest configuration file
module.exports = {
    // specify the location of the test file
    testMatch: ['**/Specs/*.spec.js'],
    // test report generator
    reporters: [
        'default',
        [
            'jest-html-reporters',
            {
                publicPath: './Report', // report directory
                filename: 'report.html', // report file name
                pageTitle: 'SuperTest and Jest API Test Report', // report title
                overwrite: true, // enable report file overwrite
                expand: true, // enable report file expansion
            },
        ],
    ],
};
```

- Running test cases

```bash
// run test case
npm run test
```

- View test report

> Test report folder: Report, click on the browser to open the latest html report file

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
