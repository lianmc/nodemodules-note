# pkginfo

将package.json文件内容导出为模块属性。

## 安装
```
    npm install pkginfo
```

## 原理
在编写一个模块时，往往需要提供`foo.version`的方式让使用者获知模块当前版本号

``` js
    exports.version = '0.1.0'
```

直接赋值的方法虽然简单，但是要在多个地方维护版本号，更通用的方法是从package.json文件中获取版本号

```` js
exports.version = JSON.parse(fs.readFileSync('/path/to/package.json', 'utf8')).version;
```