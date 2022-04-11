# 模块化

模块化（modular）编程，是强调将计算机程序的功能分离成独立的、可相互改变的“模块”（module）的软件设计技术，它使得每个模块都包含着执行预期功能的一个唯一方面（aspect）所必需的所有东西。

## 过去组织代码的方式会出现的问题

1. 命名空间冲突
2. 控制依赖的加载顺序很繁琐
3. 大型的复杂项目很难管理代码的版本

## 模块化方案

> 在 ES6 之前，社区制定了一些模块加载方案，最主要的有 CommonJS 和 AMD 两种。前者用于服务器，后者用于浏览器。ES6 在语言标准的层面上，实现了模块功能，完全可以取代 CommonJS 和 AMD 规范，成为浏览器和服务器通用的模块解决方案。

### CommonJS（同步）

> `commonjs`是 Nodejs 中的模块规范，通过`require`以及`module.exports`进行导入和导出。

- 可运行在 Node 环境
- 通过 webpack 对模块解析，可以运行在浏览器
- 动态加载

```javascript
// add.js
exports.add = function (a, b) {
  return a + b;
};

// index.js
const { add } = require('./add.js');
add(1 + 2);
```

### ESModule

> `ESModule`是 TC39 对 ECMAScript 的模块化规范，属于语言层规范，因此在 Node 及浏览器中均支持。它使用`import`、`export`进行模块的导入导出。

- `import`是在静态编译时加载。
  1. 使得编译时就能确定模块的依赖关系，以及输入和输出的变量。可在编译器进行 Tree Shaking，减少 js 体积
  2. 使得静态分析成为可能。有了它，就能进一步拓宽 JavaScript 的语法，比如引入宏（macro）和类型检验（type system）这些只能靠静态分析实现的功能。

### ESModule 与 CommonJS 模块的差异

- CommonJS 同步，有缓存，一般用于服务器端，ESModule 动态引入，按需加载，没有缓存
- CommonJS 模块输出的是一个值的拷贝，ESModule 输出的是值的引用。
- CommonJS 模块是**运行时**加载，ESModule 是**编译时**输出接口。
- CommonJS 模块的 `require()`是**同步加载**模块，ESModule 的 `import` 命令是**异步加载**，有一个独立的模块依赖的解析阶段。

### AMD（异步）

[require.js](https://requirejs.org/)

### CMD（异步）

[sea.js](https://seajs.github.io/seajs/docs/)

### Module in css
