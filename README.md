# Mockjs

Mockjs的使用

[Mockjs 官网](http://mockjs.com/examples.html#)

### 生成随机数据

方式一：
```
var newsJson = Mock.mock({
    'data|4-8': [
        {
            id: '@id',
            title: '@title',
            namespace: 'desctab',
            content: '@paragraph',
            isPublish: '@boolean',
            createTime: '@datetime',
            'fileList|1-10': [{
                name: '@integer(1,960)',
                uid: '-@name',
                url: 'http://xxxxx.xxx.clouddn.com/@name',
                status: 'done',
            }],
        },
    ],
});
```


方式二：
```
var newsJson2 = [];
for (let i = 0; i < 20; i++) {
    newsJson2.push({
        newsId: Mock.Random.natural(),
        title: Mock.Random.cparagraph(1, 3),
        date: Mock.Random.date('yyyy-MM-dd'),
        imageURL: Mock.Random.image('200x200', '#fff', '#333', 'Mock.js'),
        viewCount: Mock.Random.integer(10, 10000),
    })
};
```

### 配置接口

```
Mock.mock('/news', 'get', newsJson);
```


### 请求数据示例

```
$.ajax({
    type: "get",
    url: "/news",
    dataType: "json",
    success: function (response) {
        console.log(response.data);
    }
});
```