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
> bug5 `[Vue warn]: Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value. Prop being mutated: "showDialog"` 使用elementui时，把弹窗放在子组件中，弹窗的状态由父组件传递进来，关闭时报这个警告。
> 原因是由于props属性接收到的参数是不能修改的，elementui在关闭弹窗时时获取控制弹窗的变量然后修改，就导致了这个问题。（弹窗的状态选择用vuex管理）

### ISSUE 列表

> issue1 `elementui 滚动条组件` [具体用法查看git issue](https://github.com/ElemeFE/element/issues/2238)
>
> issue2 elementUI 在el-row 或者 el-col 上使用@click失效 需要使用`.native`修饰符 `@click.native="events"`
>
> issue3 elementui dialog对话框 before-close 仅当用户通过点击关闭图标或遮罩关闭 Dialog 时起效
>
> issue4 elementui `v-model.number` 绑定值才是number类型，不写默认是字符串类型
>
> issue4 elementui checkbox多选框绑定指定value值，并显示执行描述`<el-checkbox :label="subject.id" name="type" :key="subject.id" v-for="subject in config.subjectList">{{subject.subjectName}}</el-checkbox>`
>
> issue5 `Warn : [vue-router] Duplicate named routes definition:` vue运行报这个警告，是router中存在name命名重复，修改下名字就可以了
>
> issue6 VUE 表单元素使用v-model绑定数据值，使用验证规则检测时，数据值不能嵌套多层，否则检测不到数据值得改变。例如`v-model="a.b.c"`修改`a.b.c`值得时候数据是非响应的
