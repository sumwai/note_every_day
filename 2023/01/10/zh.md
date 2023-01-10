# 2023 年 1 月 10 日

## 目标

- [ ] 简单了解 [Github Actions](https://github.com/features/actions)
- [ ] 创建一个 Hello World Action

## 思考

## 总结

<details>
<summary>基础且最小的执行Shell的action配置</summary>

```yaml
name: Hello World
description: print "hello world"
runs:
  using: "composite"
  steps:
    - name: My first step
      shell: "sh"
      run: echo "Hello World"
```

</details>

### 参考文章
