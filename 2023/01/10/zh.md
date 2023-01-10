# 2023 年 1 月 10 日

## 日常

- [x] 简单了解 [Github Actions](https://github.com/features/actions)
- [x] 创建一个 Hello World Action
- [x] 维护项目
  - [x] 新增 Feature
  - [x] 发现旧 BUG
  
## 思考

<details>
<summary>Github Actions 能做什么？</summary>

</details>

<details>
<summary>是否可以在Github的虚拟机上运行我的程序？</summary>

</details>

<details>
<summary>Web程序请求时, 新建的变量要保证其删除</summary>

今天维护项目时, 发现了旧项目的BUG, 开发时没有注意该情况, 当运行时间久了之后, 发现程序占用内存很高

相关代码大致如下

```go
package main

func main() {
  http.HandleFunc("/", root)
  http.ListenAndServe(":8080")
}

func root(w http.ResponseWriter, r *http.Request) {
  NewModel().Where(...).Update(...)
}

type ModelStruct struct {
	err error
	*gorm.DB
}

func NewModel(model ...interface{}) *ModelStruct {
	if len(model) == 1 {
		return &ModelStruct{
			DB: db.Model(model[0]),
		}
	}
	return &ModelStruct{
		DB: db,
	}
}

```

主要问题：在响应请求时, 我使用了`NewModel`方法创建新的Model, 它在内存中创建了新的区域存放新的struct并返回指针, 而响应完毕后, 我并没有将Model的内容清除, 并且Go也不会清除那些没有使用的struct, 就导致了内存一直增长

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


## 评价

我仍然没有控制好今天的时间安排, 本打算在 21:30 时处理每日的翻译工作, 今天看来是完不成了。

对于今天的日常, 我给自己的评价是 5分 / 100分, 我会尽可能的将学习时间安排好, 至于翻译工作, 或许可以统一在某一天, 我先尝试慢慢让自己适应, 边适应边安排。
