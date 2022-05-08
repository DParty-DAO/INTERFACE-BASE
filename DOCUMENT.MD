# Beta Document 1.0

## 起步
本工程使用nextjs构建，以下是需要阅览的资料
* https://nextjs.org/ 构建工具
* https://mui.com/zh/ 主要的UI 
* https://airbnb.io/visx 图表
* https://lingui.js.org/ 国际化插件
* https://typescript.bootcss.com/ TS教程
* https://www.cypress.io/ 测试工具

## 目录结构
+ ├─cypress   #测试工具 https://www.cypress.io/ 
+ ├─pages #页面 
    + ├─_app.page  #入口页面 
    + └─_document.page  #输出页面 
+ ├─public  #静态文件输出目录 
+ ├─scripts  #构建脚本 
+ └─src 
    + ├─components  #组件 
    + ├─helpers  #帮助类 
    + ├─hooks  #自定义hooks 
    + ├─layouts  #布局页面 
    + ├─libs  #sdk 
    + ├─locales  #国际化文件 
    + ├─modules  #模块 
    + ├─providers  
    + ├─static-build 
    + ├─ui-config  #UI配置文件，比如菜单 
    + └─utils  #工具类 
+ │  .babelrc 
+ │  .env.example # nextjs，匹配.evn.*的所有文件 
+ │  .eslintignore 
+ │  .eslintrc.js 
+ │  .gitattributes 
+ │  .linguirc 
+ │  .nvmrc 
+ │  .prettierrc 
+ │  codegen.yml 
+ │  crowdin.yml 
+ │  custom.d.ts 
+ │  cypress.json  #测试工具配置文件 
+ │  index.d.ts 
+ │  next-env.d.ts 
+ │  next.config.js #nextjs配置文件 
+ │  svgo.config.js 
+ │  tsconfig.json 
## 第一个示例

### 自动路由，pageExtensions自定义页面后缀(默认会读取page目录下所有路径下的文件)
``` javascript
// eslint-disable-next-line
const pageExtensions = ['page.tsx'];
module.exports = withBundleAnalyzer({
  pageExtensions,
});
```

### 约定的入口页面和输出页面
* pages/_app.page.tsx #设置公共的Provider，通用组件
* pages/_document.page.tsx #输出页面的设置，例如：head,额外的引用

### 页面组装
以index.page.tsx为例，getLayout属性指定布局页面，getLayout会在_app.page.tsx最终使用
``` javascript
import { MainLayout } from '../src/layouts/MainLayout';
export default function Home() {
  return (
    <>
        indexPage
    </>
  );
}
Home.getLayout = function getLayout(page: React.ReactElement) {
  return <MainLayout>{page}</MainLayout>;
};
```
> 以上即可完成一个最简单页面的组成，访问localhost:3000/index访问，端口默认3000
