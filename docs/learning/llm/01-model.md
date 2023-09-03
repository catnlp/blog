<h1 style="text-align:center">模型</h1>

## llama

### 数据量

- 数据量：1.4T
- 公开数据集：爬虫、Github、维基百科、book、arxiv、stack

### 架构

- transform
- 预归一化：transformers子层输入归一化，RMSNorm
- 激活函数：SwiGLU替换ReLU，提高性能
- 位置嵌入：旋转嵌入替换绝对位置嵌入

### 训练

- 设备：2048个A100
- 时间：21天

## baichuan

### 数据量

### 架构

同llama

### 训练