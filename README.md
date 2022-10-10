# GraphSAGE
消息传递GNN模型GraphSAGE
GNN数据集
三类数据集：Cora, Citeseer, PubMed
|Items|	Cora	|Citeseer|	PubMed|
|  ----  | ----  |----|----|
|#Nodes|	2708|	3327|	19717|
|#Edges	|5429|	4732|44338|
|#Features|	1433|	3703|	500|
|#Classes|	7	|6	|3|

引用：P. Sen, G. M. Namata, M. Bilgic, L. Getoor, B. Gallagher, and T. Eliassi-Rad. Collective classification in network data. AI Magazine, 29(3):93–106, 2008. 

## 一 Cora 数据集

### 1.1数据下载地址：https://linqs-data.soe.ucsc.edu/public/lbc/cora.tgz

### 1.2 Cora数据集由机器学习论文组成，论文被分为以下七类：

1.	Case Based
2.	Genetic Algorithms
3.	Neural Networks
4.	Probabilistic Methods
5.	Reinforcement Learning
6.	Rule Learning
7.	Theory
论文的选择方式是，在最终的语料库中，每一篇论文都引用或被至少一篇其他论文引用。整个语料库共有2708篇论文。
在词干提取和删除停止词之后，我们只剩下1433个大小独特的单词。删除所有文档频率小于10的单词。
### 1.3数据集包含两个文件：
①	cora.conten内容格式说明如下：
每行的第一个条目（paper_id）是每篇论文的唯一编号ID，后续（word_attributes）包含1433个二进制码，表示词汇表中的每个单词在论文中是否存在（由1表示）或不存在（由0表示），最后一个条目（class_label）表示论文的类标签。
②	cora.cites内容格式说明如下：
包含了语料库中论文的引用关系。每行数据包含了两篇论文的编码ID，第一个条目（ID of cited paper）表示被引用论文的编号，第二个条目（ID of citing paper）表示引用论文的编号，链接的方向是从右向左。

## 二 Citeseer 数据集

### 2.1 数据集下载地址：http://www.cs.umd.edu/~sen/lbc-proj/data/citeseer.tgz

### 2.2 Citeseer数据集是从CiteSeer数字论文图书馆中选取的一部分论文，被分为以下六类：
1.	Agents
2.	AI
3.	DB
4.	IR
5.	ML
6.	HCI
论文的选择方式是，在最终的语料库中，每一篇论文都引用或被至少一篇其他论文引用。整个语料库共有3327篇论文。

关于Citeseer数据集的问题。应该是有15个孤立节点，导致了程序出现问题以及训练精度都不好。
有2种思路来解决这个问题：①直接删除3312之后的节点；②补全法：Citeseer的测试数据集中有一些孤立的点没有在test.index中（15个），可把这些点当作特征全为0的节点加入到测试集tx中，并且对应的标签加入到ty中。
在词干提取和删除停止词之后，只剩下3703个单词。删除所有文档频率小于10的单词。
### 2.3 数据集包含两个文件：
① citeseer.conten内容格式说明如下：
每行的第一个条目（paper_id）是每篇论文的唯一编号ID，后续（word_attributes）包含3703个二进制码，表示词汇表中的每个单词在论文中是否存在（由1表示）或不存在（由0表示），最后一个条目（class_label）表示论文的类标签。
② citeseer.cites 内容格式说明如下：
包含了语料库中论文的引用关系，每行数据包含了两篇论文的编码ID，第一个条目（ID of cited paper）表示被引用论文的编号，第二个条目（ID of citing paper）表示引用论文的编号。
 

## 三 PubMed数据集

### 3.1 数据集下载地址：https://linqs-data.soe.ucsc.edu/public/Pubmed-Diabetes.tgz

### 3.2 PubMed数据集包括来自Pubmed数据库的19717篇关于糖尿病的科学出版物，分为三类：
1.	Diabetes Mellitus, Experimental
2.	Diabetes Mellitus Type 1
3.	Diabetes Mellitus Type 2
引文网络由44338个链接组成。数据集中的每个出版物都由一个由500个唯一单词组成的字典中的TF/IDF加权词向量来描述。
TF-IDF（term frequency–inverse document frequency）是一种用于信息检索与数据挖掘的常用加权技术。TF是词频(Term Frequency)，IDF是逆文本频率指数(Inverse Document Frequency)。
TF-IDF是一种统计方法，用以评估一字词对于一个文件集或一个语料库中的其中一份文件的重要程度。字词的重要性随着它在文件中出现的次数成正比增加，但同时会随着它在语料库中出现的频率成反比下降。
3.3 数据集包含三个文件
①Pubmed-Diabetes.NODE.paper.tab内容格式说明如下：
+ + 每行数据的第一个条目（paper_id）是每篇论文的唯一编号ID，第二个条目是“label=***”,"***"表示该论文的所属类别，后续包含500个浮点数TF_IDF值，形式是"word=***"，"word"表示词汇，"***"表示词汇的TF_IDF值。
②Pubmed-Diabetes.GRAPH.pubmed.tab
无用文件，不用关注
③Pubmed-Diabetes.DIRECTED.cites.tab
<********> + | 每行数据的第一个条目暂时还没搞明白代表什么意思，第二个条目的数据和表示被引用论文的ID，第三个条目的数据表示引用论文的ID。

