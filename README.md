#自然语言处理--基于BPE的子词压缩

对于英文语料来讲，特别是在预训练模型兴起之前，一种常见的分词方式是通过空格对英文语句直接进行分词。然而这种分词方式可能也会带来一些问题。
英文单词由于时态、单复数、大小写等因素，可能具有多个单词变体，比如单词go具有这样的变体： going, gone, goes，单纯基于空格从语料中收集单词，可能会导致词表过大，进而导致模型学习过程中，需要设置较大的词向量矩阵，增加模型参数。
由于词表难以穷尽所有单词，以及网络中会出现一些新的词，导致某些词无法出现在词表中，即出现集外词（OOV）。
BPE（Byte-Pair Encoding）是缓解这些问题的一种算法，其不再按照完整的单词进行分词，而是将单词划分成了子词（sub-word）的粒度。例如单词showed可以被划分为show和ed， 如此做法，可以有效缩减单词个数，同时通过拆解子词也能够缓解OOV问题。图1展示了一种BPE算法效果的示例，一方面通过右侧的子词组合可以表示左侧任意一个单词，另一方面通过子词的表示大大减小了原本词表的大小。
