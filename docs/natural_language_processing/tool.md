<h1 style="text-align:center">NLP工具</h1>

## NLTK

它包括词法分析、命名实体识别、标记化、词性标注、句法分析和语义推理。但是，由于 NLTK 在处理大数据时会占用大量资源，因此推荐用于简单项目。

## SpaCy

它具有一个简单的 API、预训练的词向量、11 种语言的 23 个统计模型、用于语法和 NER 的内置可视化工具。

## Textacy

Textacy用于执行高级自然语言处理任务，它的核心NLP功能基于spaCy，但它做了大量工作，使你可以轻松地引入许多类型的数据，而无需编写额外的程序代码。

## HanLP

https://github.com/hankcs/HanLP

trie添加词典

```
from hanlp.common.trie import Trie

import hanlp

tokenizer = hanlp.load('PKU_NAME_MERGED_SIX_MONTHS_CONVSEG')
text = 'NLP统计模型没有加规则，聪明人知道自己加。英文、数字、自定义词典统统都是规则。'
print(tokenizer(text))

trie = Trie()
trie.update({'自定义': 'custom', '词典': 'dict', '聪明人': 'smart'})
```

## THULAC

https://github.com/thunlp/THULAC-Python

```python
def __init__(self, user_dict = None, model_path = None, T2S = False, \
             seg_only = False, filt = False, max_length = 50000, deli='_', rm_space=False):
    '''初始化函数，传入用户设置的参数，并且根据参数初始化不同
    模型（调入不同的.dat文件，该文件存储了一个双数组trie树）'''
    ...
    self.__userDict = None
    ...
    if(self.__user_specified_dict_name):
        self.__userDict = Postprocesser(self.__user_specified_dict_name, "uw", True)
```

## jieba

https://github.com/fxsjy/jieba

```python
def __init__(self, dictionary=DEFAULT_DICT):
    self.lock = threading.RLock()
    if dictionary == DEFAULT_DICT:
        self.dictionary = dictionary
    else:
        self.dictionary = _get_abs_path(dictionary)
```

## fastNLP

https://github.com/fastnlp/fastNLP

深度模型

## LTP

https://github.com/HIT-SCIR/ltp

加载模型

```python
if path in model_map or is_remote_url(path) or os.path.isfile(path):
    ...
    path = cached_path(
        model_map.get(path, path),
        cache_dir=cache_dir,
        force_download=force_download,
        proxies=proxies,
        resume_download=resume_download,
        local_files_only=local_files_only,
        extract_compressed_file=True
    )
```

## SnowNLP

## LAC

https://github.com/baidu/lac

百度的自动机要看一下

分词

```
from LAC import LAC
lac = LAC()

# 装载干预词典
lac.load_customization('custom.txt')

# 干预后结果
custom_result = lac.run(u"春天的花开秋天的风以及冬天的落阳")
```

## YaYaNLP

https://github.com/Tony-Wang/YaYaNLP

有地名识别

## xmnlp

https://github.com/SeanLee97/xmnlp

## SmoothNLP

https://github.com/smoothnlp/SmoothNLP

金融实体
