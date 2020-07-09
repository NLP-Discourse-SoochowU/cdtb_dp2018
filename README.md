## Toolkit for CDT-Styled Chinese Discourse Parsing

<b>-- Reference</b>
   This project contains basic parsing, evaluation and visualization tools for "Connective Driven Discourse Treebank".
   Please read the following paper for more technical details

   [Cheng Sun and Fang Kong, A Transition-based Framework for Chinese Discourse Structure Parsing.](http://jcip.cipsc.org.cn/EN/abstract/abstract2681.shtml)


<b>-- Project</b>
```
cdtparser
   |- berkeleyparser: 第三方句法解析器 berkeley parser
   |- data: 训练语料和模型等
   |- dataset: 数据集读取工具
   |    |- cdtb.py: CDTB 语料读取，序列化存储工具类
   |- labeler: 篇章关系分类器
   |- segmenter: 篇章单元分割器
   |- structure: 与篇章有关的数据结构
   |    |- tree.py 篇章树数据结构
   |- treebuilder: 篇章结构构建模型
   |- util: 工具函数和类
   |- api.py 接口函数
   |- evaluate.py: 评测脚本
   |- parse.py: 篇章解析脚本
   |- interface.py: 公共接口
   |- schemas.py: 解析策略流水线工厂方法
   |- requirements.txt: python 依赖项
   |- ...
```


<b>-- Installation</b>
* Java 需要在系统PATH环境变量中
* requirements.txt 依赖需要安装好


<b>-- Usage</b>
* 命令行使用

假设用户当前目录如下：
```
pwd
 |- cdtparser: 本工具文件夹
 |- raw: 待解析篇章文本
 |    |- 1.csv
 |    |- 2.csv
 |- parse: 解析后保存位置
```
输入文件格式
```
篇章编号\t需要解析的起始偏移量\t需要解析的终止偏移量\t篇章文本\n
```
篇章解析命令：
```
$ python3 -m cdtparser.parse [--schema 解析策略  --encoding 编码  --jobs 进程数] -source raw -save parse
```

* API

参阅 `api.py` 中的方法说明

e.g.
```python
import cdtparser
# 解析篇章
discourse = cdtparser.raw2discourse("123", "我爱北京天安门，天安门上太阳升。")
# 可视化
discourse.tree().draw()
```

<b>-- License</b>
```
   Copyright (c) 2019, Soochow University NLP research group. All rights reserved.
   Redistribution and use in source and binary forms, with or without modification, are permitted provided that
   the following conditions are met:
   1. Redistributions of source code must retain the above copyright notice, this list of conditions and the
      following disclaimer.
   2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the
      following disclaimer in the documentation and/or other materials provided with the distribution.
```