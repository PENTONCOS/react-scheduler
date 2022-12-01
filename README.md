## react-scheduler
### 测试代码

```js
// 模拟函数的执行
const sleep = delay => {
  for (let start = Date.now(); Date.now() - start <= delay;) {}
}

unstable_scheduleCallback(3, () => {console.log(1)})

unstable_scheduleCallback(3, () => {
  console.log(2)
  sleep(10)
}, {
  delay: 10
})

unstable_scheduleCallback(3, () => {console.log(3)}, {
  delay: 10
})

unstable_scheduleCallback(3, () => {
  console.log(4)
  sleep(10)
})

unstable_scheduleCallback(3, () => {console.log(5)})

// 执行结果  workLoop start -> 1 -> 4 -> workLoop start -> 5 -> 2 -> workLoop start -> 3
```