##  AsyncStorage

与数据打交道，免不了对数据进行增加，删除，更改和查找。我们来看看如何用AsyncStorage实现这些。

增加数据：

```
save(key, value) {
  AsyncStorage.setItem(key,value).then(
    (errs)=>{
      if (!errs) {
        //xxx
      }else {
        //xxx
      }
    })  
}

```

在这里，我们使用了promise，这样会使代码看起来舒服很多。虽然看起来很多，实际上，只要知道

```
AsyncStorage.setItem(key,value)
```

就可以了，我们用`setItem`来将key和value存储起来，看到这里想必你已经知道了为什么AsyncStorage是key-value系统了。

由于有了key，所以我们可以用key进行查询：

```
get(key) {
   AsyncStorage.getItem(key)
            .then(  
                (result)=> {   
                    if (!result) {
                      //xxx
                    }
                    //返回结果
                }
            ).catch((error)=> {  
              //错误处理
        }
}   
```

数据我们存完了，但是如果数据没用了怎么办？删掉呗。和查询数据很像，删除也需要用到key：

```
del(key) {
   AsyncStorage.removeItem(key).
            then(
            ()=>{
              //删除成功
            }
          ).catch((error)=> {  
              //错误处理
        }
}
```

至于修改数据，其实写法和增加数据一样，当你需要修改一项数据的时候，直接传入key和一个新的值就可以了。