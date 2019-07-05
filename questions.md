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



#### code2vec: Learning Distributed Representations of Code



#### Maybe Deep Neural Networks are the Best Choice for Modeling Source Code

1.这篇文章最核心的是将原本以token为单位的网络修改为以subword units为单位的网络，以此来解决OOV的问题。我认为，这里之所以将token分割为subword units的效果比原来更好了，是因为代码中的identifier一般是多个英文的组合，比如getValue, setTime。通过subword units使得getValue和setTime被分割为get和Value，set和Time，避免了OOV的现象。在该论文中使用字节对编码的方法获得subword units，但是我觉得其实并没有必要。因为我们完全可以使用英文分词算法对数据集进行分割，来得到subword units。从这一角度来看，使用字节对编码似乎是不必要的（且是费时的），老师有什么看法？

#### How To Create Natural Language Semantic Search For Arbitrary Objects With Deep Learning

1.在该文的part 1中，为了去除代码中的注释，使用了python的包，先将代码转化为AST，再将AST转化为code，为什么要使用这种相当复杂且耗时的方法，而不是用最brute-force的方法来实现？

#### Deep API Learning



#### Deep Code Search



#### Aroma: Code Recommendation via Structural Code Search



#### When Deep Learning Met Code Search