---
title: npm配置与nodejs安装
date: 2021-12-04 22:28:49
tags:
- nodejs
- npm
categories: 
- web前端
- js
---

# nodejs

## 安装

windows下只能下载新版本重新安装



# npm （Node Packaged Modules）

## config

### npm从以下来源获取配置值，按优先级排序

##### 命令行标记

在命令行上放置`--foo bar`设置`foo`配置参数为`bar`。 一个 `--` 参数(argument)告诉cli解析器停止读取flags.一个 在命令行结尾的`--flag`参数(parameter)的值将会是`true`.

##### 环境变量

任何以`npm_config_`开始的环境变量都会作为配置参数解读。在环境里设置`npm_config_foo=bar`将会设置`foo`配置参数为`bar`。任何没有值的环境配置将会默认为`true`。配置值是不区分大小写的，所以`NPM_CONFIG_FOO=bar`的结果一样

### npm获取配置有6种方式，优先级由高到低

1. 命令行参数。 `--proxy http://server:port`即将proxy的值设为`http://server:port`。
2. 环境变量。 以`npm_config_`为前缀的环境变量将会被认为是npm的配置属性。如设置proxy可以加入这样的环境变量`npm_config_proxy=http://server:port`。
3. 用户配置文件。可以通过`npm config get userconfig`查看文件路径。如果是mac系统的话默认路径就是`$HOME/.npmrc`。
4. 全局配置文件。可以通过`npm config get globalconfig`查看文件路径。mac系统的默认路径是`/usr/local/etc/npmrc`。
5. 内置配置文件。安装npm的目录下的npmrc文件。
6. 默认配置。 npm本身有默认配置参数，如果以上5条都没设置，则npm会使用默认配置参数。

- npm修改全局包安装路径

```bash
npm config set prefix 'X:\yourpath\nodejs\npm_global'
npm config set cache 'X:\yourpath\nodejs\npm_cache'
```

- 针对npm配置的命令行操作

```bash
npm config set <key> <value> [--global]
npm config get <key>
npm config delete <key>
npm config list
npm config edit
npm get <key>
npm set <key> <value> [--global]
```

在设置配置属性时属性值默认是被存储于用户配置文件中，如果加上`--global`，则被存储在全局配置文件中。

如果要查看npm的所有配置属性（包括默认配置），可以使用`npm config ls -l`。

如果要查看npm的各种配置的含义，可以使用`npm help config`。

`npm config edit`会将默认配置复制到目标配置文件，并用系统默认编辑器打开，让用户编辑。`npm config edit`可以进行**用户配置**，也可以进行**全局配置**（加`-g`选项）。

> **项目配置**必须自己编辑`/path/to/my/project/.npmrc`文件

- 为npm设置代理

```bash
$ npm config set proxy http://username:password@server:port
$ npm config set https-proxy http://username:pawword@server:port
```

- 换源

```bash
npm config set registry https://registry.npm.taobao.org
npm config get registry
```

# use

### npm本地安装与全局安装有什么区别？

```bash
npm install grunt // 本地安装，则是将模块下载到当前命令行所在目录。
npm install -g grunt//全局安装，模块将被下载安装到【全局目录】中；
【npm install xxx –save】 安装并写入package.json的”dependencies”中
【npm install xxx –save-dev】安装并写入package.json的”devDependencies”中
```

### 删除依赖

```bash
【npm uninstall xxx】删除xxx依赖
【npm uninstall xxx -g】删除全局依赖xxx
```

### 使用npm init初始化项目

在node开发中使用npm init会生成一个pakeage.json文件，这个文件主要是用来记录这个项目的详细信息的，它会将我们在项目开发中所要用到的包，以及项目的详细信息等记录在这个项目中。方便在以后的版本迭代和项目移植的时候会更加的方便。也是防止在后期的项目维护中误删除了一个包导致的项目不能够正常运行。使用npm init初始化项目还有一个好处就是在进行项目传递的时候不需要将项目依赖包一起发送给对方，对方在接受到你的项目之后再执行npm install就可以将项目依赖全部下载到项目里。

```shell
PS F:\MyBlog> npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (myblog)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to F:\MyBlog\package.json:

{
  "name": "myblog",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes)
PS F:\MyBlog>
PS F:\MyBlog>
```

package name:                      你的项目名字叫啥
version:                          版本号
description:                       对项目的描述
entry point:                      项目的入口文件（一般你要用那个js文件作为node服务，就填写那个文件）
test command:                     项目启动的时候要用什么命令来执行脚本文件（默认为node app.js）
git repository:                    如果你要将项目上传到git中的话，那么就需要填写git的仓库地址（这里就不写地址了）
keywirds：                       项目关键字（我也不知道有啥用，所以我就不写了）
author:                         作者的名字（也就是你叫啥名字）
license:                        发行项目需要的证书（这里也就自己玩玩，就不写了）



# error

- Error: EINVAL: invalid argument, mkdir 'C:\Users\25433\'C:\Users\25433\AppData\Roaming\npm''



