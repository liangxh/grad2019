# 框架


* 摘要
    
    ```
    自Web2.0普及后，人们习惯在互联网的各种平台上透过不同的媒体来分享和传递他们的想法和情感。透过对这些媒体进行情感分析，我们可以得知人们的想法和态度。譬如透过分析产品评论了解用户对新产品是否满意，又或者分析社交平台上的舆论了解网民对新政策是否同意，以此快速响应，其中蕴含着丰富的商业价值和政治价值，其相关技术的研究价值在近年也得到了重视。而文本作为较常见的媒体之一，加之部分微博等社交平台推出了用户生产数据的采集服务，提供了充裕的文本数据资源，面向文本的情感识别研究得以更快的速度发展。然而随着在互联网上的交互方式变得丰富，文本的数据结构也变得多种多样，如微博上的短文本、在线实时聊天的两人或多人对话、讨论区里的帖子回复。在处理不同数据结构时，该如何提取当中的信息并加以运用来预测目标结果，成为了重要的研究课题。

    本文主要探讨了两个不同数据结构下的情感识别问题，并提出了一个通用的文本情感识别系统设计方案。论文的主要内容如下：

    1. 面向微博的反讽识别。反讽作为一种特殊的修辞手法，起着把文本字面意思反转的效果。识别文本中反讽修辞的使用对于正确理解发言者的意图起着关键性的作用。本文研究了在微博中识别反讽的出现以及其对应类型，深入了解实验数据当中各个类型的样本的特性，分析单个分类器对各个类的识别能力，给出一个基于集成学习的反讽识别框架，以此在多个独立分类器的基础上实现一个集成系统来达到更好的识别能力。

    2. 面向三轮对话的情感识别。为了更好地识别一段文本的情感，引入上下文信息被认为有指导性作用。而在文本对话的场景下，要识别某个人在某次发言所表达的情感，可以考虑引入该次聊天的历史记录。本文研究了在两人轮流发言的三轮对话中，识别最后一轮发言所表达的情感。此处采用与面向微博的反讽识别相同的系统设计以评估设计方案的泛用性，另外我们进一步探索了上下文信息的运用方面，透过把不同的运用方面体现在分类器的不同设计方案上，并根据其性能差别和对神经网络权重的分析，了解上下文信息如何有助于识别正文的情感。
    ```

* 引言
    * 研究背景与意义 (任务目标 场景 动机)

    ```
    自Web2.0普及后，大量网民每天在互联网生产着不同媒体类型的数据，其中包含各种信息，如个人生活经历，购买行为，对产品服务的体验评价，对社会时事的看法等等。从人们的日常社交需求来看，这种借由互联网媒体的分享非常便捷，我们可以了解到亲朋好友的近况，也或者随时和不认识的网民交流对具体事件的想法。在商业上，借由对用户的网络行为进行分析，企业可以对应客户或者潜在客户有更深入的了解，对他们的需求和反馈及时作出反应将带来战略性的优势。在社会管理上，政府可以透过对网民在网络上的发言了解人民的想法和舆论的走向，进而作出相应的措施。正因为互联网的普及，才使得以上基于对特定人群的了解来进行决策的做法成为可能。随着数据资源变得丰富，相应的技术在近年有明显的发展，目前市面上已经有公司（如国内的腾讯和阿里巴巴，以及国外的微软和亚马逊等）提供基于大型社交媒体平台(如微博，讨论区等)上的数据进行意图分析相关的规泛化服务，然而相应的技术依然有进步空间，研究工作还在不同方向上摸索。

    情感在人们的思想表达和交流中起着重要作用\cite{Banerjee2015Detection}，比起了解该思想的细节内容，情感对应该思想的大体倾向。譬如在分析用户对新产品的评论时，从对正负性情感反馈的统计可以得知新产品是否能让大部分的客户满意，或者筛选出表示不满意的用户再进行深入分析。因此情感识别是意图分析中是非常重要的一环，而由于在互联网上，大部分情况下用户以文本表达想法，面向文本的意图识别成为了近年的最要研究课题之一。在人们面对面的交流，发言者的肢体语言，面部表情，声调变化等都有助于聆听者对所表达内容的了解，然而这些信息并不存在于文本当中，这也正是对文本进行情感识别本身的难点之一\cite{SemEval2019Task3}。
    ```

    * 情感模型

    ```
    情感计算的基础是对情感作出描述，现有的描述方式可以分成两个大类: 范畴观和维度观。范畴观即把不同情感对应到一组离散的情感标签上Alm等人\cite{Alm2005Emotions}，其中具代表性的有Plutchik的情感模型\cite{Plutchik1980Emo}和Ekan的情感理论\cite{Ekman1992An}和。Plutchik的情感模型包含十种情感：愤怒、恐惧、悲伤、厌恶、期待、信任、高兴、惊讶；这些情感都各自对应具有重要生存意义的行为，各种复杂的情感都是由这此基本情感构成，另外这十种情感可以分成五组对立的情感对。Ekan在十年后提出的情感理论和Plutchik的相似，但相对地少了期待和信任，是一个六类情感模型。

    以维度观描述情感就是把情感映射到多维空间的点上，而目前维度观情感模型以二维和三维空间的为主。二维情感模型中较有代表性的是Russell提出的环状模型（Circumplex Model）\cite{Russell1980Cir} ，其中纵坐标对应情感的激活度（Arousal），横坐标对应情感向性（Valence），而不同的情感则分布在一个环状的区域内。Bradley等人\cite{Bradley1992Rem}提出的向量模型（Vector Model）对横轴和纵轴的定义相似，但其理论认假设高激活度的情感应该有较明显的正向或负向，相对地低激活度的情感则偏向中性，故情感分布在一个回力标形状的区域。Watson和Tellegen \cite{Watson1985Tow} 提出的 PANA（positive activiation-negative activation）模型和前两者在理论基础上则有明显的不同，他们认为情感的正面作面和负面作用是两个独立的成分，所以在模型中纵轴和横轴分别表示情感正面作用和负面作用的强弱，其效果相当于把Russell等人提出的环状模型的向量空间旋转45度\cite{Rubin2009A}。

    基于三维空间的情感模型中具有代表性的有Plutchik\cite{Plutchik1980Emo}提出的倒置椎体三维模型，Plutchik认为情绪之间包含强度，相似性和两极性三种维度，椎体的顶部和底部分别对应强的情绪和弱的情绪，相似的情感对应椎本中相近的位置，对立的的情绪则会对应到椎体中对立的位置上。另外还有Mehrabian \cite{Mehrabian1996Pleasure}提出的PAD模型，其三维空间的三个坐标轴分别对应情感愉悦度（Pleasure）、激活度（Arousal）以及优势度（Dominance）。较近期被提出的是Hugo\cite{Hugo2012A}的情感立方体模型，其三维空间的三个坐标轴分别对应5-羟色胺（5-hydroxytryptamine, 5-HT）, 多巴胺（dopamine，DA）和 去甲肾上腺素（noradrenaline，NE）三种神经递质所产生信号的强弱，并对空间中一个立方体的八个顶点标记了其对应的情感。
    ```

    ```
    在文本中，情感的表达和理解跟背景信息密切相关\cite{Seyeditabari2018Emotion}，当一段文本涉及多个对象或背景时，识别其中的依赖关系会变得困难，而针对不同的对象，所表达的情感更有可能不同。譬如"这款手机的拍照功能很好，较同等价位的其他手机清晰，但是太耗电了续航能力不行"，这里就涉及了"很好"的"拍照功能"以及"不行"的"续航能力"，分别是正面和负面的反馈，此时用户对"手机"的整体反馈是好是坏则难而判断，需要进一步了解该用户的需求更偏重于"拍照功能"还是"续航能力"。因此对背景的认知和理解对于识别文本中的情感就起着不可忽视的作用。

    ```

    * 国内外研究现状（应用 学术）
        * 情感识别

        ```
        对应上述情感模型的分类，情感识别研究可以分成两类。第一类对应范畴观，给定一组情感类型，判断一段文本或针对文本内的某个方面所表达的情感倾向于该组情感中的哪一个，或者是否包含这一组情感中的一个或多个情感。如国际比赛SemEval2018 \cite{mohammad2018semeval}任务一的子任务要求识别一段微博中是否包含愤怒、恐惧、悲伤等十一种情感中的一种或多种情感。另一类情感识别研究对应维度观，对于给定的情感属性，判断一段文本中该情感属性的强度。其中常见的有情感向性的二分类问题（正性或负性）、三分类问题（正性、中性或负性）、五分类问题（非常正性，正性、中性、负性或非常负性）。其中五分类问题的研究对象一般是互联网上五星评分制的产品评论或者电影评论等。

        目前文本情感识别的研究按照文本的粒度可以大致分成三类：文章级别, 句子级别，属性级别。在文章级别的情感识别中，文章由多个句子组成一个或者多个段落，假设整篇文章存在某种情感偏向，研究目标则是自动识别出该情感偏向的类型或强度。

        Turney \cite{turney2002thumbs} 利用线上电影评论中"推荐"（大拇指朝上）和"不推荐"（大拇指朝下）的标记研究对电影评论的正负性情感识别。他提出利用点互信息(Pointwise Mutual Information，PMI)来评估单词的语义倾向性，其中PMI透过在大型语料库中统计两个单词的共同出现的情况来评估两个单词的相似度。首先利用PMI值评估各个单词与正向情感的代表性单词"excellent"和负向情感的代表性单词"poor"的相似性，再取这两个PMI值作差得出该单词在语义上倾向于哪一种情感。最近透过计算整段评论的平均语义倾向性评估整体的情感倾向。


        Pang和Lee \cite{pang2004sentimental} 利用线上电影评论中"喜欢"和"不喜欢"标记研究对电影评论的正负性情感识别。他们首先对评论中每个句子的主观程度进行评分，利用评分构造一个带权重的句子关系图，再基于最小割算法结合上下文加强对每个句子主观程度的判断，过滤评论中不带主观情感的句子后再判断整个评论的情感向性，以此加增强识别能力。

        [12], [26], [29], [30], [45], [48], [55], [61], [65]

        ```

        * 跨领域情感识别
        * 面向社交媒体的情感识别

    * 研究内容和贡献
    * 本论文的内容安排

* 问题分析和框架设计
    * 问题分析
        * 脱离具体实验的数据
        * 
    * 框架设计
        * 
        * 
    * 本章小结

* 情感识别技术 (下面章节的导读)
    * 词向量的训练方法也可以提到
    * 有些相关但没有用的方法可以提但不用细说
    * 
    * 特征提取

* 数据预处理
    * 社交平台上普遍出现的情况是文本写作有别于正规的语言用法，也可以认为在社交平台发展起来的一种语言

* 结论与展望


================================

* 文本的情感
    * 嘲讽作为一种副语言现象 ( para(l?)linguistic )


* 通用的针对社交媒体文本的处理

* 用同一个框架套到两个问题

* 两个问题都要包含
    * 嘲讽（单句）
    * 情感识别（对话）1.5文本量
        * 多个单句
        * 结合3个turn

* 对比的方法也要给出介绍
    * 论据和论点

* 每章小结

参考扈浩的论文 三个实验 同一批数据 不同方法 串起来了

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

@article{Seyeditabari2018Emotion,
  title={Emotion Detection in Text: a Review},
  author={Seyeditabari, Armin and Tabari, Narges and Zadrozny, Wlodek},
  year={2018},
}

@inproceedings{mohammad2018semeval,
  title={Semeval-2018 task 1: Affect in tweets},
  author={Mohammad, Saif and Bravo-Marquez, Felipe and Salameh, Mohammad and Kiritchenko, Svetlana},
  booktitle={Proceedings of The 12th International Workshop on Semantic Evaluation},
  pages={1--17},
  year={2018}
}

@inproceedings{pang2004sentimental,
  title={A sentimental education: Sentiment analysis using subjectivity summarization based on minimum cuts},
  author={Pang, Bo and Lee, Lillian},
  booktitle={Proceedings of the 42nd annual meeting on Association for Computational Linguistics},
  pages={271},
  year={2004},
  organization={Association for Computational Linguistics}
}

@inproceedings{turney2002thumbs,
  title={Thumbs up or thumbs down?: semantic orientation applied to unsupervised classification of reviews},
  author={Turney, Peter D},
  booktitle={Proceedings of the 40th annual meeting on association for computational linguistics},
  pages={417--424},
  year={2002},
  organization={Association for Computational Linguistics}
}