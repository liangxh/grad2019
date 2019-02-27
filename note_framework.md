# 框架


* 摘要
    * 随着Web2.0的普及，人们在互联网上透过不同的媒体来分享和传递他们的想法和情感。而在文本挖掘的研究领域中，情感分析的目标则是从自然语言的文本当中自动识别发言者的意图和情感。在商业价值上，营销公司可以透过对客户反馈的情感分析，判断客户对产品或者服务是否满足，或者根据当前市场上用户的喜好计划进一步的商业策略。

* 引言
    * 研究背景与意义

```
随着Web2.0的普及，大量网民每天在互联网生产着不同媒体类型的数据，其中包含各种信息，如个人生活经历，购买行为，对产品服务的体验评价，对社会时事的看法等等。从人们的日常社交需求来看，这种借由互联网媒体的分享非常便捷，我们可以了解到亲朋好友的近况，也或者随时和不认识的网民交流对具体事件的想法。在商业上，借由对用户的网络行为进行分析，企业可以对应客户或者潜在客户有更深入的了解，对他们的需求和反馈及时作出反应将带来战略性的优势。在社会管理上，政府可以透过对网民在网络上的发言了解人民的想法和舆论的走向，进而作出相应的措施。正因为互联网的普及，才使得以上基于对特定人群的了解来进行决策的做法成为可能。随着数据资源变得丰富，相应的技术在近年有明显的发展，目前市面上已经有公司（如国内的腾讯和阿里巴巴，以及国外的微软和亚马逊等）提供基于大型社交媒体平台(如微博，讨论区等)上的数据进行意图分析相关的规泛化服务，然而相应的技术依然有进步空间，研究工作还在不同方向上摸索。

情感在人们的思想表达和交流中起着重要作用\cite{Banerjee2015Detection}，比起了解该思想的细节内容，情感对应该思想的大体倾向。譬如在分析用户对新产品的评论时，从对正负性情感反馈的统计可以得知新产品是否能让大部分的客户满意，或者筛选出表示不满意的用户再进行深入分析。因此情感识别是意图分析中是非常重要的一环，而由于在互联网上，大部分情况下用户以文本表达想法，面向文本的意图识别成为了近年的最要研究课题之一。在人们面对面的交流，发言者的肢体语言，面部表情，声调变化等都有助于聆听者对所表达内容的了解，然而这些信息并不存在于文本当中，这也正是对文本进行情感识别本身的难点所在\cite{SemEval2019Task3}。

情感计算的基础是对情感作出描述，现有的描述方式可以分成两个大类: 范畴观和维度观。范畴观即把不同情感对应到一组离散的情感标签上Alm等人\cite{Alm2005Emotions}，其中具代表性的有Plutchik的情感模型\cite{Plutchik1980Emo}和Ekan的情感理论\cite{Ekman1992An}和。Plutchik的情感模型包含十种情感：愤怒、恐惧、悲伤、厌恶、期待、信任、高兴、惊讶；这些情感都各自对应具有重要生存意义的行为，各种复杂的情感都是由这此基本情感构成，另外这十种情感可以分成五组对立的情感对。Ekan在十年后提出的情感理论和Plutchik的相似，但相对地少了期待和信任，是一个六类情感模型。

以维度观描述情感就是把情感映射到多维空间的点上，而目前维度观情感模型以二维和三维空间的为主。二维情感模型中较有代表性的是Russell提出的环状模型（Circumplex Model）\cite{Russell1980Cir} ，其中纵坐标对应情感的激活度（Arousal），横坐标对应情感向性（Valence），而不同的情感则分布在一个环状的区域内。Bradley等人\cite{Bradley1992Rem}提出的向量模型（Vector Model）对横轴和纵轴的定义相似，但其理论认假设高激活度的情感应该有較明顯的正向或负向，相对地低激活度的情感则偏向中性，故情感分布在一个回力标形状的区域。Watson和Tellegen \cite{Watson1985Tow} 提出的 PANA（positive activiation-negative activation）模型和前两者在理论基础上则有明显的不同，他们认为情感的正面作面和负面作用是两个独立的成分，所以在模型中纵轴和横轴分别表示情感正面作用和负面作用的强弱，其效果相当于把Russell等人提出的环状模型的向量空间旋转45度\cite{Rubin2009A}。

基于三维空間的情感模型中具有代表性的有Plutchik\cite{Plutchik1980Emo}提出的倒置椎体三维模型，Plutchik认为情绪之間包含强度，相似性和两极性三种维度，椎体的頂部和底部分別对应强的情绪和弱的情绪，相似的情感对应椎本中相近的位置，对立的的情绪则会对应到椎体中对立的位置上。另外还有Mehrabian \cite{Mehrabian1996Pleasure}提出的PAD模型，其三维空間的三个坐标軸分別对应情感愉悦度（Pleasure）、激活度（Arousal）以及优势度（Dominance）。較近期被提出的是Hugo\cite{Hugo2012A}的情感立方体模型，其三维空間的三个坐标軸分別对应5-羟色胺（5-hydroxytryptamine, 5-HT）, 多巴胺（dopamine，DA）和 去甲肾上腺素（noradrenaline，NE）三种神经递质所產生信号的强弱，并对空間中一个立方体的八个顶点标记了其对应的情感。





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

@inproceedings{Alm2005Emotions,
  title={Emotions from Text: Machine Learning for Text-based Emotion Prediction},
  author={Alm, Cecilia Ovesdotter and Dan, Roth and Sproat, Richard},
  booktitle={Conference on Hlt/emnlp},
  year={2005},
}


@article{Ekman1992An,
  title={An argument for basic emotions},
  author={Ekman, Paul},
  journal={Cognition & Emotion},
  volume={6},
  number={3-4},
  pages={169-200},
  year={1992},
}

@article{Plutchik1980Emo,
  title={Emotion: Theory, Research and Experience},
  author={Plutchik, Robert and Kellerman, Henry},
  journal={In Theories of emotion},
  volume={11},
  pages={399},
  year={1980},
}

@article{Russell1980Cir,
  author = {Russell, James},
  year = {1980},
  month = {12},
  pages = {1161-1178},
  title = {A Circumplex Model of Affect},
  volume = {39},
  journal = {Journal of Personality and Social Psychology},
}

@article{Bradley1992Rem,
  author = {M. Bradley, Margaret and Greenwald, Mark and C. Petry, Margaret and J. Lang, Peter},
  year = {1992},
  month = {04},
  pages = {379-90},
  title = {Remembering Pictures: Pleasure and Arousal in Memory},
  volume = {18},
  journal = {Journal of experimental psychology. Learning, memory, and cognition},
}

@article{Watson1985Tow,
  author = {Watson, David and Tellegen, Auke},
  year = {1985},
  month = {10},
  pages = {219-35},
  title = {Toward a Consensual Structure of Mood},
  volume = {98},
  journal = {Psychological bulletin},
}

@article{Rubin2009A,
  title={A comparison of dimensional models of emotion: evidence from emotions, prototypical events, autobiographical memories, and words},
  author={Rubin, David C, and Talarico, Jennifer M,},
  journal={Memory},
  volume={17},
  number={8},
  pages={802-808},
  year={2009},
}

@article{Mehrabian1996Pleasure,
  title={Pleasure-arousal-dominance: A general framework for describing and measuring individual differences in Temperament},
  author={Mehrabian, Albert},
  journal={Current Psychology},
  volume={14},
  number={4},
  pages={261-292},
  year={1996},
}

@article{Hugo2012A,
  title={A new three-dimensional model for emotions and monoamine neurotransmitters},
  author={Hugo, L?Vheim},
  journal={Medical Hypotheses},
  volume={78},
  number={2},
  pages={341-348},
  year={2012},
}