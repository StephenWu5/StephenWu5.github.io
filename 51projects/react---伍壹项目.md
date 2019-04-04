#### 后台管理系统

1. 一个bug : post方式的请求却get方式传参

```
var opt = {
    method: 'POST',
    url: type === 'add' ? '/api/dynamic/addDynamic' : '/api/dynamic/updateDynamic',
    params: values
}
```

改params为data则可