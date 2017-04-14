---
layout: post
title: "python解析yaml配置文件"
description: "yaml比较适合做配置文件"
headline: ===============================================================================
category: python
tags: [python, config]
imagefeature: picture-26.jpg
comments: true
mathjax: false
---

# 1. 各个配置文件的对比
配置文件有很多种，ini, property, xml, json, yaml，调研了下
[常用配置文件格式简析](http://zengrong.net/post/2360.htm)

yaml堪称完美：

>为什么不是XML呢？因为：
>
> - YAML的可读性好。
> - YAML和脚本语言的交互性好。
> - YAML使用实现语言的数据类型。
> - YAML有一个一致的信息模型。
> - YAML易于实现。
>上面5条也就是XML不足的地方。同时，YAML也有XML的下列优点：
>
> - YAML可以基于流来处理；
> - YAML表达能力强，扩展性好。
> - 总之，YAML试图用一种比XML更敏捷的方式，来完成XML所完成的任务。

# 2. yaml文件介绍
- 官网： http://www.yaml.org/
- 名字由来：YAML: YAML Ain't Markup Language

# 3. 安装
`pip/pip3 install pyyaml`

# 4. 使用demo
ref: [python中yaml配置文件模块的使用](http://www.jianshu.com/p/f21b9306a68d)
config.yaml

```yaml
name: junxi
age: 18
spouse:
    name: Rui
    age: 18
children:
  - name: Chen You
    age: 3
  - name: Ruo Xi
    age: 2
```

parse.py


```python
#!/usr/bin/env python
# _*_ coding:utf-8 _*_

__author__ = 'junxi'

import sys
import yaml

f = open('config.yaml')
content = yaml.load(f)

print type(content)
print '修改前: ', content   # 可以看出整个Yaml配置文件是一个字典, 里面可以包含字典和列表
content['age'] = 17     # 根据Key修改对应的值
content['children'][1]['age'] = 1
print '修改后: ', content
```

```out
<type 'dict'>
修改前:
{
    'age': 18,
    'spouse': {
        'age': 18,
        'name': 'Rui'
    },
    'name': 'junxi',
    'children': [
        {
            'age': 3,
            'name': 'ChenYou'
        },
        {
            'age': 2,
            'name': 'RuoXi'
        }
    ]
}
修改后:
{
    'age': 17,
    'spouse': {
        'age': 18,
        'name': 'Rui'
    },
    'name': 'junxi',
    'children': [
        {
            'age': 3,
            'name': 'ChenYou'
        },
        {
            'age': 1,
            'name': 'RuoXi'
        }
    ]
}
```