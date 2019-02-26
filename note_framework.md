# 框架


* 摘要
    * 随着Web2.0的普及，人们在互联网上透过不同的媒体来分享和传递他们的想法和情感。而在文本挖掘的研究领域中，情感分析的目标则是从自然语言的文本当中自动识别发言者的意图和情感。在商业价值上，营销公司可以透过对客户反馈的情感分析，判断客户对产品或者服务是否满足，或者根据当前市场上用户的喜好计划进一步的商业策略。

* 引言
    * 研究背景与意义
        
        ```
        随着Web2.0的普及，大量网民每天在互联网生产着不同媒体类型的数据，其中包含各种信息，如个人生活经历，购买行为，对产品服务的体验评价，对社会时事的看法等等。从人们的日常社交需求来看，这种借由互联网媒体的分享非常便捷，我们可以了解到亲朋好友的近况，也或者随时和不认识的网民交流对具体事件的想法。在商业上，借由对用户的网络行为进行分析，企业可以对应客户或者潜在客户有更深入的了解，对他们的需求和反馈及时作出反应将带来战略性的优势。在社会管理上，政府可以透过对网民在网络上的发言了解人民的想法和舆论的走向，进而作出相应的措施。正因为互联网的普及，才使得以上基于对特定人群的了解来进行决策的做法成为可能。随着数据资源变得丰富，相应的技术在近年有明显的发展，目前市面上已经有公司（如国内的腾讯和阿里巴巴，以及国外的微软和亚马逊等）提供基于大型社交媒体平台(如微博，讨论区等)上的数据进行意图分析相关的规泛化服务，然而相应的技术依然有进步空间，研究工作还在不同方向上摸索。
        
        情感在人们的思想表达和交流中起着重要作用\cite{Banerjee2015Detection}，比起了解该思想的细节内容，情感对应该思想的大体倾向。譬如在分析用户对新产品的评论时，从对正负性情感反馈的统计可以得知新产品是否能让大部分的客户满意，或者筛选出表示不满意的用户再进行深入分析。因此情感识别是意图分析中是非常重要的一环，而由于在互联网上，大部分情况下用户以文本表达想法，面向文本的意图识别成为了近年的最要研究课题之一。在人们面对面的交流，发言者的肢体语言，面部表情，声调变化等都有助于聆听者对所表达内容的了解，然而这些信息并不存在于文本当中，这也正是对文本进行情感识别本身的难点所在\cite{SemEval2019Task3}。



        ```

    * 国内外研究现状
        * 基于规则的模式识别
        * 非神经网络的机器学习方法
        * 深度学习方法
    * 研究内容和贡献
    * 本论文的内容安排

* 问题分析和框架设计
    * 问题分析
    * 框架设计
        * 
        * 
    * 本章小结
* 数据预处理

* 特征提取

* 



Liu, B., Web data mining: Exploring hyperlinks,2nd edition, New York: Springer,2011.



@inproceedings{Hakak2017Emotion,
  title={Emotion analysis: A survey},
  author={Hakak, Nida Manzoor and Mohd, Mohsin and Kirmani, Mahira and Mohd, Mudasir},
  booktitle={International Conference on Computer},
  year={2017},
}

@book{Banerjee2015Detection,
  title={Detection of Emotions in Text: A Survey},
  author={Banerjee, Shyamol and Dutta, Unmukh},
  booktitle={International Journal of Advanced Engineering and Global Technology},
  year={2015},
  volume='03',
  issue='12'
}

 
@InProceedings{SemEval2019Task3,
  author = {Chatterjee, Ankush and Narahari, Kedhar Nath and Joshi, Meghana and Agrawal, Puneet},
  title = {SemEval-2019 Task 3: EmoContext: Contextual Emotion Detection in Text},
  booktitle = {Proceedings of The 13th International Workshop on Semantic Evaluation (SemEval-2019)},
  address = { Minneapolis, Minnesota}, year = {2019}
}