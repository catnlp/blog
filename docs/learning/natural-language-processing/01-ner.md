<h1 style="text-align:center">命名实体识别</h1>

## 任务

命名实体识别(named entity recognition，NER)是指识别文本中具有特定意义的实体。常见的实体类型有人名、地名、机构名、时间等。
如示例所示，NER任务需要识别实体在文本中的位置和类别。

> <font color='red'>周杰伦<sub>[人名]</sub></font>（<font color='red'>Jay Chou<sub>[人名]</sub></font>），
> <font color='blue'>1979年1月18日<sub>[时间]</sub></font>出生于<font color='green'>台湾省新北市<sub>[地名]</sub></font>

### 实体形式

**(1) 扁平实体**

扁平实体是指实体之间不会重叠，实体由连续字符串组成。

> 杭州市和嘉兴市 -> 杭州市、嘉兴市

**(2) 嵌套实体**

嵌套实体是指实体之间存在重叠。

> 浙江大学 -> 浙江、浙江大学

**(3) 非连续实体**

非连续实体是指实体可以由不连续字符串组成。

> 下个月1号、2号 -> 下个月1号、下个月2号

### 开源工具

| 名称     |语言| 类型  | 备注 |
|--------|---|-----|----|
| Stanza ||||
| HanLP  ||||
| LTP    ||||

### 数据集

| 名称            |语言|类型|备注|
|---------------|---|---|---|
| CoNLL-2003    ||||
| MSRA          ||||
| weibo         ||||
| OntoNotes 5.0 ||||

## 抽取式

### 位置+类别

**(1) Softmax**

**(2) CRF**

### 位置

**(1) Span**

**(2) MRC**

### 类别

**(1) Multi-head**

**(2) GlobalPointer**

**(3) Biaffine**


## 生成式

### Seq2Seq



## 参考

[1] [命名实体识别 NER 论文综述：那些年，我们一起追过的却仍未知道的花名 （一）](https://zhuanlan.zhihu.com/p/135453456)

[2] [信息抽取（五）实体命名识别之嵌套实体识别哪家强，我做了一个简单的对比实验](https://blog.csdn.net/weixin_45839693/article/details/116425297)

[3] [刷爆3路榜单，信息抽取冠军方案分享：嵌套NER+关系抽取+实体标准化](https://zhuanlan.zhihu.com/p/326302618)
