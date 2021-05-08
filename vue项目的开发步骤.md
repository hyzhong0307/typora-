### vue项目的开发步骤

1. 划分目录结构
2. 引入css文件
   - normalize.css引入
   - common.css
   - normalize.css --> 引入到 common.css --> 引入到app.vue中
3. 别名配置

> 由于vuecli3中的webpack配置已经被隐藏，我们不好直接修改
>
> 于是我们需要在根目录上创建 vue.config.js

```javascript
// vue.config.js 名字不能出错
// 这个文件默认会内容和公共配置合并
module.exports = {
  configureWebpack: {
    resolve: {
      alias: {
        "assets": '@/assets',
        "common": '@/common',
        "components": '@/components',
        "network": '@/network',
        "views": '@/views',

      }
    }
  }
}
```

4. .editorconfig的配置

```
root = true

[*]
charset = utf-8
indent_style = space
indent_size = 2
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true

```

