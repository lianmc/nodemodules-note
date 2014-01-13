# [pkginfo](https://github.com/indexzero/node-pkginfo)

将`package.json`文件内容导出为模块属性。

## 安装
```
  npm install pkginfo
```

## 原理
在编写一个模块时，往往需要提供`foo.version`的方式让使用者获知模块当前版本号。

``` js
  exports.version = '0.1.0'
```

直接赋值的方法虽然简单，但是要在多个地方维护版本号，更通用的方法是从`package.json`文件中获取版本号。

```` js
  exports.version = JSON.parse(fs.readFileSync('/path/to/package.json', 'utf8')).version;
```


## 用法
在引入`pkginfo`时直接调用。

``` js
  var pkginfo = require('pkginfo')(module);
  
  console.dir(module.exports);
```

只用module做为参数，则将`package.json`文件所有内容都导出为调用模块的属性。

上面例子的输出为：

```
  { name: 'simple-app',
    description: 'A test fixture for pkginfo',
    version: '0.1.0',
    author: 'Charlie Robbins <charlie.robbins@gmail.com>',
    keywords: [ 'test', 'fixture' ],
    main: './index.js',
    scripts: { test: 'vows test/*-test.js --spec' },
    engines: { node: '>= 0.4.0' } }
```

### 导出指定属性
将指定属性名做为参数，将只导出指定属性:

``` js
  var pkginfo = require('pkginfo')(module, 'version', 'author');
  
  console.dir(module.exports);
```

上述例子输出为：

```
  { version: '0.1.0',
    author: 'Charlie Robbins <charlie.robbins@gmail.com>' }
```

#### 参考资源
[1]. https://github.com/indexzero/node-pkginfo/blob/master/README.md
