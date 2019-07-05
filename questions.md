# Questions

- ML in PL/SE
  - A Survey of Machine Learning for Big Code and Naturalness
  - code2vec: Learning Distributed Representations of Code
    - <https://code2vec.org/>
  - Maybe Deep Neural Networks are the Best Choice for Modeling Source Code

- Code Search Related
  - How To Create Natural Language Semantic Search For Arbitrary Objects With Deep Learning
    - <https://github.com/hamelsmu/code_search>
  - Deep API Learning
    - <https://github.com/guxd/deepAPI>
  - Deep Code Search
    - <https://github.com/guxd/deep-code-search>
  - Aroma: Code Recommendation via Structural Code Search
  - When Deep Learning Met Code Search

#### A Survey of Machine Learning for Big Code and Naturalness

1.

> As a consequence, programming languages are designed top-down by a few designers for many users. Natural languages, in contrast, emerge, bottom up, “through social dynamics”

如何理解编程语言是自顶向下的，而自然语言是自底向上的？

#### code2vec: Learning Distributed Representations of Code

1.x=7和x=5这样的赋值语句，它们在语义上应该是相等的。按照文中的path-context,它们两个的值应该是：

```
(x, Name↑AssignOperator↓IntegerExpr, 7)

(x, Name↑AssignOperator↓IntegerExpr, 5)
```

但是x为5或者7对语义是无影响的，它本身都是对变量进行赋值，那么为什么不是直接将中间的path作为网络的输入而是将终结符和path一起输入给网络呢？

#### Maybe Deep Neural Networks are the Best Choice for Modeling Source Code

1.这篇文章最核心的是将原本以token为单位的网络修改为以subword units为单位的网络，以此来解决OOV的问题。我认为，这里之所以将token分割为subword units的效果比原来更好了，是因为代码中的identifier一般是多个英文的组合，比如getValue, setTime。通过subword units使得getValue和setTime被分割为get和Value，set和Time，避免了OOV的现象。在该论文中使用字节对编码的方法获得subword units，但是我觉得其实并没有必要。因为我们完全可以使用英文分词算法对数据集进行分割，来得到subword units。从这一角度来看，使用字节对编码似乎是不必要的（且是费时的），老师有什么看法？

#### How To Create Natural Language Semantic Search For Arbitrary Objects With Deep Learning

1.在该文的part 1中，为了去除代码中的注释，使用了python的包，先将代码转化为AST，再将AST转化为code，为什么要使用这种相当复杂且耗时的方法，而不是用最brute-force的方法来实现？

#### Deep API Learning

1.DeepAPI针对的是java这种强类型的语言进行训练的，而对于python，js这些弱类型的语言，从原理上讲，DeepAPI并不适用，是否有某种解决方案来解决弱类型语言的问题？

2.该文章的训练数据是代码+注释的第一句，我认为取注释的第一句太粗糙了，因为注释的第一句可能并不是代码的语义概括，能否对注释进行某种“缩写”操作，来对数据进行预处理呢？

#### Deep Code Search

1.CoNN中考虑方法名、API调用序列和token集合三部分，这里没有使用token的序列，会产生一定的信息的丢失，为什么丢失的信息并没有对结果产生影响？

#### Aroma: Code Recommendation via Structural Code Search

1.Aroma会将输入的代码映射到向量空间，然后寻找语义库中的相似代码，我觉得这个设计很容易导致检索误差。比如说在语义库中有一段代码是进行a/b的操作（记为代码A），那么在这之前应该有检测b是否为0的代码B，在库中可能有的数据只有代码A，有的数据是代码BA（尽管BA是推荐的写法，但是也不能保证数据中所有代码都是BA），那么当用户输入A时而忘记写代码B时，此时代码的向量空间中距离最近的应该是类似A的代码而不是类似BA的代码，那么怎么能做到提示用户忘记写B了呢？

#### When Deep Learning Met Code Search

1.在UNIF方法中，对于code input使用了attention矩阵ac处理embedding，但是不对query input使用attention矩阵处理，我认为这是因为code input本身的冗余量太多了，要使用attention处理embedding去掉冗余信息，而query input的冗余量相对可以忽略。那么，在NCS方法中为什么对code input使用TFIDF处理，而不对query input进行TFIDF处理呢？

2.文中介绍的模型全部使用了cos距离作为相似度的测量标准，相比于其它的相似度表示方法（如欧式距离），cos距离的优势在哪里呢？