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
> 
> bug6 配置webpack中externals来减少打包后vendor.js的体积 一直报错 $router 不能重复定义

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
>
> issue7 vue-cli报错 ` vue-cli · Failed to download repo vuejs-templates/webpack: getaddrinfo ENOTFOUND github.com github.com:443
` 这个报错是由于，使用vpn时修改了vue-cli下载模版的端口，导致其试图从127.0.0.1:41379下载。关掉VPN正常使用
>
> issue8 elementui 中表单方法 **`resetFields`** 对整个表单进行重置，将所有字段值重置为**初始值**并移除校验结果，**`clearValidate`**
清空校验结果。这两个方法是有区别的
>
> issue9 [elementui-cascader级联选择组件]：动态加载次级数据问题: **第一层级的数据中，cities即使没有也要存在且为空数组，这样才能触发`active-item-change`事件**，否则即使**当父级选项变化时触发的事件，仅在 change-on-select 为 false **也不能触发`active-item-change`
```javascript
  var Main = {
    data() {
      return {
        options2: [{
          label: '江苏',
          cities: []
        }, {
          label: '浙江',
          cities: []
        }],
        props: {
          value: 'label',
          children: 'cities'
        }
      };
    }
  };
```
>
> issue10 winscp 通过ftp连接远程服务器默认是被动模式，需要在高级->连接中把被动模式勾掉，不然就会一直报`Server sent passive reply with unroutable address 172.18.202.164, using host address instead.`这个错误
>
> issue11 elementui表单验证，如果规则是自定义的时候，不会出现红色星号，解决办法是在必填项的`el-item`标签上添加 **`required`**属性即可

