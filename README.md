# 前端开发手册（完善中）
## 一、编程规约
### （一）命名风格
1. 【强制】代码命名严禁使用拼音或英文拼音混合方式，更不允许直接使用中文命名，惯例词除外。 
2. 【强制】类名使用 UpperCamelCase 风格，遵守驼峰形式。
3. 【强制】方法名、参数名、成员变量、局部变量使用 lowerCamelCase 风格，遵守驼峰形式。
4. 【强制】常量命名统一使用全部大写，原本驼峰处（单词间隔处）使用下划线隔开，力求语义表达完整。
5. 【强制】React 组件文件、对应 less、sass 文件以及外层的文件夹，统一使用 UpperCamelCase 风格，遵守驼峰形式。
6. 【强制】如果当前组件是页面组件，最外层容器（div）中的 class 写成 ``组件名-container`` 格式，如当前页面组件为 ``Home``，则最外层样式为 ``home-container``。
7. 【强制】如果当前组件是非页面组件，最外层容器（div）中的 class 写成 ``组件名-component`` 格式，如当前页面组件为 ``NavigationBar``，则最外层样式为 ``navigation-bar-component``。
9. 【强制】全局样式统一添加某个固定前缀，如 `` global- ``，避免出现样式覆盖现象。
10. 【强制】杜绝不规范、不通用的缩写。
11. 【强制】英文命名确保英文拼写正确（可借助拼写检查插件）。
12. 【推荐】非类文件的功能文件夹名称，统一全部使用小写，避免 git 在未设定相关参数时同步过程中，由于不同系统，而导致目录大小写区分不准确的问题。
13. 【推荐】如果使用了设计模式，在文件名以及类名上体现出设计模式，如 RequestProxy，HumanFactory。
14. 【推荐】如果使用专门文件定义了枚举对象或者常量对象，在文件命名及对象命名上予以体现。假设下面文件专门用来定义 StatusCode，则可将文件命名为 StatusCodeConstants，
	``` JavaScript
	const StatusCodeConstants = {
	  SUCCESS: 200,
	  REDIRECT: 300,
	  NOT_FOUND: 404,
	  SERVER_ERROR: 500
	}
	
	export default StatusCodeConstants
	```
15. 【强制】class、className 命名禁止随性、缩写的命名（如 l-g、a-b），力求语义化基础上追求简洁（如 video-icon，video-tip）。
16. 【强制】除了 html5 中的推荐标签，禁止使用怪异标签（如模仿 ``<b>`` 标签，使用 ``<ib><bi>`` 来实现加粗、斜体样式的标签）。特殊需求使用 React 或 Vue 自带的自定义组件方式。


### （二）常量定义
1. 【强制】如果当前环境支持 let、const，则不允许使用 var 定义变量。
2. 【强制】禁止使用魔法值，统一使用有语义的常量来代替。
3. 【强制】如果有常量类型的枚举，事先定义枚举对象，并在对象中罗列出所有的枚举常量细类。
4. 【推荐】不要在一个常量文件里面维护所有的常量，不同类别常量进行区分，如 ErrorCodeConstants，StatusCodeConstants。
 

### （三）控制语句
1. 【强制】在一个 switch 语句中，每个 case 语句要么通过 break 和 return 语句来终止 case，要么添加详细注释来说明每个阶段将进行到哪个阶段为止；在 switch 语句中，最后必须添加一个 default 语句，哪怕什么都没有或者只有一个 return。
2. 【强制】在 if / else / for / while / do 等语句中，必须使用大括号。即使执行内容只有一行语句，禁止使用单行省略模式。当代码很多情况下，以下情形，很容易引起歧义：
	```javascript
	function () {
	  if (isTrue) return
	  console.log("hello world")
	}
	```
3. 【推荐】表达异常情况的分支时，少用 if-else 语句进行连续嵌套，而是建议直接在 if () 中做完特殊判断。
4. 【强制】禁止三个及以上三目运算符嵌套使用。
5. 【推荐】在 if 条件中，如果判断逻辑较为复杂，则先将结果赋值给一个有意义的布尔变量名，提高代码可读性。
6. 【推荐】在进行诸如循环或者遍历的情况下，理应考虑性能问题，诸如，实例化对象、定义中转变量等操作应放在循环、遍历外进行。
7. 【推荐】在会进行时间开销比较大（如 http 请求、复杂数据运算）的方法处，条件允许情况下，最好做好数据类型检查，避免因为数据不合规而导致出现的异常或性能浪费。


### （四）注释规约
1. 【强制】文件、类、方法的注释使用 JSDoc 注释规范，如 `` /** 注释内容 */ ``，如果是方法，补充参数和返回值说明。
2. 【强制】方法内部注释，在被注释语句上方单起一行，并使用 `` // `` 注释。方法内部需要多行注释时，使用 `` /* */ `` 注释，并注意对齐。
3. 【强制】基础组件必须添加创建人、创建日期及是否允许他人未经同意更改的说明（预防基础组件更改后造成大面积 bug）。
3. 【强制】所有组件必须有功能说明，若存在复杂逻辑，则需重点说明。
3. 【推荐】使用 `` // `` 单行注释时，在双斜杠后方预留一个空格，再书写注释语句。如 
	``` javascript
	function hello(name) {
	  // 打印 hello
	  console.log("hello, " + name)
	}
	```
4. 【强制】枚举对象数据和常量数据必须要有注释，说明每个数据项含义。
5. 【强制】避免使用半吊子英文来注释，如果英文不能阐明含义就使用中文来进行说明（http、ajax 等专业名词则依旧保留原样）。
6. 【强制】代码如果修改，对应注释处也必须同步修改，避免出现注释和代码存在歧义的情况。
7. 【推荐】合理处理已有冗余注释（如：为了注释而加的注释，早已过时、与代码不符的注释）。
8. 【推荐】注释添加代码标记：如果有待办事项处，添加 TODO 并予以注释；如果是已有疑难 bug，却不能立即修复的，添加 FIXME 并予以注释。除此之外，应定期清理上述标记，完善代码。


### （五）代码风格
1. 【强制】js 基本代码风格，公司内部（至少同一项目）统一遵循一种规范格式，如 Google JavaScript Style Guide 或 JavaScript Standard Style。
2. 【推荐】尽可能使用 eslint 来做代码风格检测，尽量遵循某个业内既有规范风格。尤其不提倡过多自定义、率性而为的行为。
3. 【强制】类文件使用 ES6 风格来定义 class，并添加内部方法，禁止使用 function. prototype 来添加原型方法。
4. 【强制】React 组件中如果有使用 props，则在组件定义中添加 Component.propTypes，并对字段类型、是否必输、功能等相关属性进行说明。
5. 【推荐】当一个方法的入参数量达到 4 个或 4 个以上时，则应定义一个参数对象，并在对象中完成必须字段的填充。
6. 【推荐】数据存储
	1. 临时数据：直接在内存中处理，可定义一个全局对象、或使用类似 redux，mobx 的三方库；
	2. 持久数据：可以存储在服务器端，统一存储服务端；必须存储在客户端的，统一存储在 localStorage 中，同时匹配写好清除方法；
7. 【推荐】慎用 css 中的 `` !important `` 关键字，书写不当不仅会降低 stylesheet 的可读性，而且使其难以维护（尤其是多人协同开发时）；
8. 【推荐】书写 css、less、sass 过程中，宁可保留部分重复代码，也不要为了复用样式而随意更改样式树，致使 stylesheet 难以阅读和维护；
9. 【推荐】书写页面布局布局样式过程中，如果当前环境允许使用 flex，则尽量使用 flex 布局（流式布局，在浏览器 layout 的过程中计算量更少，也更能提高页面的性能）；


### （六）其他
1. 【推荐】链接资源引用，逻辑上可省略协议声明部分（`` http: 或 https: ``），但仍建议加上，如果后期有类似 electron 打包需求，此处会获取不到资源。
2. 【推荐】需要使用 require 或 import 引用非本 module 中的内容时，由上至下遵守以下顺序：
	1. node_modules 中，可以用包名直接引用的对象，如 `` import * as React from 'react' ``；
	2. node_modules 中，可以用包名直接引用的方法，如 `` import { merge } from 'lodash' ``；
	3. 项目中 export 出来，需要用相对地址来引入的对象，如 `` import HelloComponent from './HelloComponent.js' ``；
	4. 项目中 export 出来，需要用相对地址来引入的方法，如 ``  import splitString from '../stringUtil.js' ``；
	5. 需要引用的 css、less、sass 文件，如 `` import './Demo.less' ``；
3. 【推荐】DRY（Don’t Repeat Yourself）原则，避免出现重复的代码，重复代码后期极难维护，容易出现一个因为改动却需要到处都改的情况。
	1. React、Vue 中，如果多个页面中有重复 dom 结构的代码，抽出外部组件；
	2. less、sass 中，如果有多个同等样式，抽出公用样式方法；
	3. js 方法重复，对于需要多次使用的方法，根据分类，分入不同的 util 中；
4. 【推荐】React 开发中，对于暂存值（逻辑处理中的中间变量，且不会影响页面渲染结果）不要放在 state 中，更不要使用 this.setState 来更改 state 中的暂存值；
	


## 二、异常处理
1. 【强制】产品异常时，异常信息必须能做到友好展示。
2. 【强制】不用 try - catch 来做条件条件、流程控制，try-catch 相比于正常的流程控制更耗费性能，也效率更低。
3. 【强制】避免使用大区块的 try-catch，分清稳定代码和非稳定代码（动态情况下产生，如接口返回类型不符等）。
4. 【强制】不能白白吃掉异常，catch 住异常之后一定要处理，哪怕是 console.err，如果什么都不处理，不如直接向上抛出异常。
5. 【强制】记得 try-catch-finally 才是完整的组合，如果有资源对象或者流对象，一定要在 finally 中处理。如果 finaly 中不处理，很容易因为异常导致代码中断执行，从而使资源不能得到及时释放。
6. 【强制】线上（生产）环境下，只允许 console 宣传日志或临时为了 debug 而打印的信息，其他内容一律不准 console 出来。


## 三、数据打点
1. 【强制】每个页面的进入都需要进行打点，方便获取产品的 pv、uv。如 window.onload、React 中的 componentDidMount、vue 的 mounted 中进行打点。
2. 【推荐】条件允许情况下，用户所有的交互式操作，都需要进行打点（方便得到用户的漏斗模型、计算用户的流失率等）。
3. 【强制】打点内容力求简明、清晰，并且与以往打点内容互不冲突。


## 四、工程架构
1. 【强制】每个项目都需要提供个性化配置文件，并在版本管理中 ignore 掉，以便能适应每个人的开发习惯，也避免版本同步时配置文件的互相覆盖（如 webpack 在有 webpack.default.js 基础上，搭配 webpack.local.js 文件）。
2. 【强制】核心、私密数据不上传至 github 或者 svn 等版本管理工具，统一使用单独文件配置（如小程序中的 AppId、AppSecret）。
3. 【强制】项目目录架构，允许使用不同的目录格式，但是整体架构力求清晰，以下模式仅供参考（有 dir 则代表当前是目录）
	```
	-- (dir)config【打包配置存放】
	  -- webpack.dev.config
	  -- webpack.prod.config
	  -- 等其他配置文件
	-- (dir)dist/build
	-- (dir)mock
	-- (dir)node_modules
	-- (dir)src【核心代码】
	  -- (dir)api【api 集中管理】
	  -- (dir)asset/static【静态资源存放（更推荐 cdn）】
	  -- (dir)components【全局通用基础组件存放】
	  -- (dir)config【环境配置参数，也可后端获取，前端有此配置能做很多黑科技。】
	  -- (dir)external【三方文件处理，当前目录的 index.js 处理完所有逻辑】
	  -- (dir)modules/pages/routes【此处按功能类别抽出页面级组件】
	    -- (dir)components
	    -- (dir)module
	    -- router.js【路由文件】
	  -- (dir)store【redux、mobx】
	  -- (dir)style
	    -- common.less / global.less
	    -- (dir)mixin 样式方法
	  -- (dir)util
	  -- index.js / app.js
	  -- index.html
	-- (dir)typings
	-- package.json
	-- 等其他项目及配置文件（.editorconfig、eslintrc、.gitignore、typings.json 等等）
	```























