# mpMasonry

> 小程序瀑布流组件

## 基本使用

##### 1、将components目录下中masonry文件夹复制到自己项目中。

##### 2、添加业务组件，并在业务组件中添加property，用于承载数据

    // property名必须为item
    properties: {
        item: { 
            type: Object
        }
    }

##### 3、引入masonry组件和所需的业务组件
    
    // index.json
    "usingComponents": {
        "masonry": "../../components/masonry/masonry",
        "img-box": "../../components/img-box/img-box"
    }

##### 4、在wxml加入masonry节点

    <!-- index.wxml -->
    <masonry generic:masonry-item="img-box" id="masonry" interval-width="20rpx"></masonry>

`generic:masonry-item`用于指定业务组件，`interval-width`为左右两列空隙宽度。

##### 5、调用函数，渲染瀑布流

    _doStartMasonry(items) {
        // 通过ID，获取组件实例
        this.masonryListComponent = this.selectComponent('#masonry');
        // 调用组件的start函数，渲染瀑布流
        this.masonryListComponent.start(items).then(() => {
            console.log('render completed')
        })
    }

> 为保证页面显示效果，建议一次渲染不超过100个元素。

## 函数列表

<table>
    <thead>
        <tr>
            <th>函数名</th>
            <th>函数功能</th>
            <th>参数说明</th>
            <th>返回值</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>append</td>
            <td>批量添加元素</td>
            <td>{Array} items - 新增的元素数组</td>
            <td>Promise</td>
        </tr>
        <tr>
            <td>delete</td>
            <td>批量删除瀑布流中的元素</td>
            <td>{Number} start - 开始下标<br>{Number} end  - 结束下标</td>
            <td>无</td>
        </tr>
        <tr>
            <td>deleteItem</td>
            <td>删除瀑布流中的某个元素</td>
            <td>{Number} index - 数组下标</td>
            <td>无</td>
        </tr>
        <tr>
            <td>start</td>
            <td>启动组件，开始渲染瀑布流</td>
            <td>{Array} items - 参与渲染的元素数组</td>
            <td>Promise</td>
        </tr>
        <tr>
            <td>stop</td>
            <td>停止渲染瀑布流，清空数据</td>
            <td>无</td>
            <td>无</td>
        </tr>
        <tr>
            <td>updateItem</td>
            <td>更新渲染数组中的某个元素</td>
            <td> {Object} newItem  - 修改后的元素<br>{Number} index - 需要更新的数组下标</td>
            <td>无</td>
        </tr>
    </tbody>
</table>

## 实践案例

![京东种草](https://api.kapeter.com/storage/TGDntXf3r0cUQ3KrmgMPYS1S9xN9noChbau4F0as.jpeg)