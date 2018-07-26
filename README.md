# selfProduct
````
# 记事本项目

  ## 分析

    1.数据结构

        页面中toDo列表的保存的数据
        [{name:'洗碗',complete:false}]
    2.根据数据渲染页面li
        判断是否选中
        checkbox进行双向绑定
    3.点击新增
        点击回车  获取输入的内容 增加到列表中 清空输入框 
        输入框为空 点击回车没效果
    4.点击删除对应的待办事项
        点击button 删除对应的那个事项
        绑定时 传入下表
    5.编辑待办事项
        获取到当前修改的值
        保存到 cacheEdit 中
        双击进入编辑状态 加上类名
    6.保存修改
        编辑状态下 点击回车即可
    7.点击esc取消修改
        编辑状态下 点击esc即可
        最开始的时候直接双向绑定 取消之后 无法还原的
        增加一个临时变量 用来保存 临时的操作 知道确认修改时 才保存 否则 直接取消
    8.重复编辑问题
        代码中并没问判断是否有其他的文本框进入编辑
        为了解决这个问题 每次进入编辑是 把所有的编辑状态全部设置为 false 再修改当前这一个即可
    9.失去焦点 保存 或者取消
        问文本框增加 @blur 事件 指向 取消 或者  保存 的逻辑  即可
    10.清空
        为清空按钮绑定点击事件
        清空data中的toDoList = [] 即可完成清空
    11.计数
        使用计算属性 计算未办的事项 返回个数即可
    12.筛选高亮逻辑
        增加一个标记当前状态的变量
        因为选项不止有2中 字符串来记录(数字1,2,3)
        三个a标签绑定点击事件
        点击修改标示变量的值
        三个a标签的类名 是需要进行判断
    13.显示筛选的值
        计算属性
        生成li标签是 不是 循环总数组
        计算属性中的数组
        逻辑
            根据标示状态 进行数组的筛选
            返回筛选之后的值

    14,15号逻辑 使用click 触发时 value并没有改变 使用change即可
    14.全选
        使用click 触发时 value还没有改变
        替换为 change事件
    15.判断是否全部选中
        click ul 使用冒泡的方式
        直接把事件绑定给  checkbox 使用 change事件即可
    16.数据常驻
        localStorage取值 
            有值 赋值
            没值 初始值[]
        
        浏览器关闭
            数据保存到 localStorage中
````

····
# webpack Webpack前端资源打包工具 
    1.安装  npm install webpack -g 
    2. 4.x 版本需执行 npm install  webpack-cli -g 	 
    3. 在当前根目录中创建src文件夹放置需打包的文件（webpack的入口文件夹）
        并创建一个名为index的js文件 文件内容： document.write("It works.");
    4.在根目录创建一个dist文件夹与src文件夹同级（dist文件夹作为webpack的出口 放打包后的文件 main.js）
    5.在根目录下创建一个index.html文件与src文件夹同级 内容
        <html>
                <head>
                        <meta charset="utf-8">
                </head>
                <body>
                        <script type="text/javascript" src="./dist/main.js" charset="utf-8"></script>
                </body>
        </html>

    6.在终端打开根目录文件夹 并运行打包命令 （webpack）
    7.在src文件夹下有多个js文件时 可以在index.js用require(‘文件名’)
        引入文件不用后缀
    8.Webpack默认只打包js文件 如需打包其他文件需自行下载组件
    9.下载css打包    npm install --save-dev style-loader css-loader
    10.写一个配置文件 webpack.config.js 
        const path = require('path');

    module.exports = {
        entry: './src/index.js',
        output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist')
        },
        module: {
        rules: [
        {
            test: /\.css$/,
        use: [
            'style-loader',
            'css-loader'
            ]
        }
        ]
    }
    };
    11.加载图片 npm install --save-dev file-loader
        {
            test: /\.(png|svg|jpg|gif)$/,
            use: [
            'file-loader'
            ]
        }

    12.
    webpack 根据正则表达式，来确定应该查找哪些文件，并将其提供给指定的 loader。在这种情况下，以 .css 结尾的全部文件，都将被提供给 style-loader 和 css-loader。
````