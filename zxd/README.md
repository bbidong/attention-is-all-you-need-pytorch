# 相关资料
## 论文翻译 
https://zhuanlan.zhihu.com/p/36699992  
## 结构详解
- 容易理解 https://zhuanlan.zhihu.com/p/48508221
- 一些细节说的更具体 https://blog.csdn.net/han_xiaoyang/article/details/86560459
## encoder-decoder attention
假如input为 "我喜欢看电影“ ，output为 "I ...”

当要翻译第二个词的时候，querry为 “I“的向量，它要查询下一个词是什么；

key为"我喜欢看电影“的向量，也就是备选词；

q*k表示每个备选词k与q的相似度；

value为"我喜欢看电影“的向量。

# 环境
- ubuntu 18
- python 3.6
- torch 1.0.0
- torchvision 0.2.0

# Test流程
从src文件中读取要翻译的句子，从vocab文件中获得word和idx的对应关系，src的idx有2911个，target的idx有3149个

把src的句子拆解成单词, 每句加上's' '/s'前后标志词，再把单词转化为相应的idx

设batch=30, 这30个句子里最长的句子有31个单词，用collate_fn函数把其他不够31个单词的句子后面都补0，最后得到src_seq [30,31]和src_pos [30,31]
![](fig/test.jpg)
