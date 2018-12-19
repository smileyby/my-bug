解决办法
=======

### BUG 列表

> bug1 [vue v-model 循环绑定数据 问题](https://segmentfault.com/q/1010000017216594)
>
> bug2 elementui form表单中 select 会显数据时，显示结果不正确，首先要检查是否是option上绑定的value值类型和返回数据的value类型是否一致
>
>bug3 `[Vue warn]: Templates should only be responsible for mapping the state to the UI` 出现这个警告的原因可能是你新建VUE实例的代码放在了被绑定的组件当中
>
> bug4 `TypeError: Cannot destructure property `compile` of 'undefined' or 'null'.` npm run dev 过程中报错，最后发现原来是webpack和webpack-dev-server 版本的原因。
> [webpack git issue](https://github.com/webpack/webpack-dev-server/issues/1334)
> 如果webpack-dev-server是3.X，webpack必须是4.X；如果webpack-dev-server是2.X，webpack必须是3.X
> 发生这个错误的原因是，在初始化安装npm包的时候，提示`found 1 high severity vulnerability run npm audit fix to fix them, or npm audit for details` ，发现了一个高危漏洞，然后按照npm的提示执行之后，webpack-dev-server版本就变成3.x，然后就抛出了这个error
>

### ISSUE 列表

> issue1 `elementui 滚动条组件` [具体用法查看git issue](https://github.com/ElemeFE/element/issues/2238)
>
> issue3 elementUI 在el-row 或者 el-col 上使用@click失效 需要使用`.native`修饰符 `@click.native="events"`
