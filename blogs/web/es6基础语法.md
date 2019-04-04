1. 
  ```
    // es5中定义常量的方法
      Object.defineProperty(window,"PI2",{
          value: 2,
          writable: false
      })
      // 常量定义完了不可以在赋值
      const haha = 'haha';
      // haha = "111";
  ```