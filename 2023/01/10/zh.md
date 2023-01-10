# 2023 年 1 月 10 日

## 目标

- [ ] 简单了解 [Github Actions](https://github.com/features/actions)
- [ ] 创建一个 Hello World Action

## 思考

<details>
<summary>Github Actions 能做什么？</summary>

</details>

<details>
<summary>是否可以在Github的虚拟机上运行我的程序？</summary>

</details>

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

- [了解 GitHub Actions](https://docs.github.com/zh/actions/learn-github-actions/understanding-github-actions)
- [关于自定义操作](https://docs.github.com/zh/actions/creating-actions/about-custom-actions)
- [GitHub Actions 的元数据语法](https://docs.github.com/zh/actions/creating-actions/metadata-syntax-for-github-actions)
