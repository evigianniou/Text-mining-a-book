# Text-mining-a-book
‘Father Goriot’: Uncovering Hidden patterns of class inequality, wealth and family!


![image](https://github.com/evigianniou/Text-mining-a-book/assets/118303189/2af62707-ac74-411e-96f5-0011726daeba)

Table of contents:

o	Abstract
o	Introduction
o	Methods and Results
o	Future work
o	Conclusion
o	References


Abstract
This report presents a comprehensive text mining analysis of the novel "Father Goriot" by Honoré de Balzac. The aim of the project was to extract meaningful insights from the text using various methods and techniques. The report describes the preprocessing steps, entity recognition, topic modeling, relationship extraction and co-occurrence analysis performed on the text corpus. Additionally, it highlights the challenges encountered during the analysis and provides recommendations for future work.
Introduction
Text mining, a subfield of natural language processing (NLP), has gained significant attention in recent years due to its ability to extract valuable insights and patterns from textual data. By employing computational techniques and statistical algorithms, text mining enables researchers to explore and analyze large volumes of text in a systematic and efficient manner.

In this project, we apply text mining techniques to the novel "Father Goriot" by Honoré de Balzac. "Father Goriot" is a renowned literary work that provides a captivating portrayal of social realities and human nature in 19th-century Paris. The novel revolves around the tragic story of a kind-hearted yet impoverished father named Jean-Joachim Goriot and the complex relationships among the characters living in a boarding house.

The decision to choose "Father Goriot" for text mining analysis was driven by several factors. Firstly, the novel offers a rich and nuanced narrative with a diverse range of characters and their interactions. This complexity provides an ideal dataset for exploring various text mining methods and extracting meaningful insights.

Moreover, "Father Goriot" presents linguistic challenges due to its inclusion of French language elements within the English text. This aspect adds an additional layer of complexity to the text mining process, requiring specialized techniques to handle multilingual aspects effectively.

Text mining techniques applied to "Father Goriot" can shed light on the characters' relationships, underlying themes, and social dynamics depicted in the novel. By uncovering hidden patterns and associations within the text, we can gain a deeper understanding of Balzac's literary work and its socio-cultural context.

Methods and Results
1.Text extraction and Preprocessing:
The text of "Father Goriot" was first extracted from Project Goutenberg and preprocessed. The preprocessing stage plays a crucial role in preparing the text for further analysis. Initially, the header of the text was deleted and tokenization was applied to separate the text into sentences and then into individual words. Punctuation marks, special characters, whitespaces, new lines, apostrophes and numerical characters were removed using regular expressions. In addition, words with length less than three were deleted from the text. Stopwords, which are common words that do not carry significant meaning, were removed after lowercasing the tokens as stopwords are case sensitive. Removing stopwords is not always a good idea as it can remove words that can be useful for some tasks. Lemmatization was then performed to obtain the grammatical base form of each word, known as lemma, considering the part-of-speech (POS) tags of the words. 


The analysis of the longtail of words on the preprocessed words with its steep decline provided us with insights into their frequency distribution. It was observed that many of the most frequent words were non-meaningful, indicating the need for further filtering of the data. Additionally, the presence of French words in the English text was noted, which required special attention and handling during subsequent analysis.
 

2. Language Identification:
To address the challenge of correctly identifying the language of separated words, the Googletrans library was used. However, this method had limitations in accurately identifying the languages for individual words. As a recommendation for future work, the utilization of a language-independent model such as multilingual BERT was proposed. Such models are designed to handle multilingual text analysis tasks effectively, enabling more accurate language identification.

3. Word Cloud Generation:
Word clouds provide a visual representation of word frequency in a text corpus. In this project, word clouds were generated based on the preprocessed text of "Father Goriot." However, it was observed that the most frequent words in the word clouds were often non-meaningful. To improve the quality of the word clouds, bigrams (pairs of adjacent words) were created to capture more meaningful word associations. The inclusion of bigrams in the word clouds enhanced the representation of contextual information. 
 
Wordcloud of single words
 
Wordcloud of bigrams
4.Tf-idf
Additionally, TF-IDF (Term Frequency-Inverse Document Frequency) analysis was applied to identify meaningful words based on their frequency in the text and rarity in the entire corpus. By assigning weights to each term, TF-IDF highlights words that are frequently present in the text but relatively uncommon in the overall corpus. This approach can be valuable in text mining, as it enables us to focus on key terms that carry significant contextual information. Utilizing TF-IDF analysis provides a useful framework for selecting important words, which in turn support various analysis tasks, such as topic modeling and co-occurrence analysis. Incorporating bigrams into the TF-IDF analysis can further enhance the identification of meaningful word associations and contextual relationships within the text. When removing words from the text based on their TF-IDF scores, careful selection of an appropriate threshold is crucial to ensure meaningful and relevant terms are retained while filtering out less significant ones. It is also important to be careful with deleting words as they can be entities. After finding the tf scores of the words in our text, some of the frequent words found were money, poor, family, father, daughter, death, kill, love, tear, cry, brother, fear, pain, power, lover, mother, wife, husband, child which could be used to find family relationships or events.

 
Boxplot of words with the highest tf-idf scores
5.Dependency Parsing
Dependency parsing plays a crucial role in text mining by uncovering the syntactic structure and relationships between words in a sentence. It allows us to identify the grammatical dependencies and hierarchical organization of words, which provides valuable insights into the underlying meaning and semantics of the text. By analyzing the dependency relationships, we can extract subject-verb-object relationships, identify modifiers and qualifiers, and capture the overall flow of information within the text. Dependency parsing is useful for various text mining tasks, including named entity recognition, sentiment analysis, information extraction, and event detection. The analysis of dependencies can enhance our understanding of the text, enabling us to extract meaningful insights and patterns.
6.Coreference resolution
Coreference resolution plays a vital role in text mining by identifying and linking expressions in the text that refer to the same entity or concept. It addresses the challenge of pronouns, noun phrases, or named entities that are used interchangeably to refer to a specific person, object, or entity throughout the text. By accurately resolving coreferences, we can establish a cohesive understanding of the relationships between mentions and track the flow of information more effectively. Coreference resolution enables us to create coherent and consistent representations of the text, which are essential for tasks such as entity recognition, sentiment analysis, information extraction, and summarization. The fastcoref library was used in a part of the text, successfully giving also the clusters of words related to the same entity.
7. Named Entity recognition
Entity recognition is a crucial step in extracting entities such as names, facilities, and locations from the text. In this project, entity recognition was performed with two different methods, using the nltk library and finetuned Bert. One challenge encountered was identifying French names and handling variations in names and titles. Moreover, recognizing names with specific structures, such as 'name' 'de' 'last name', proved to be challenging for the applied method. Future work suggestions included the development of rules to improve the handling of French names and titles and coreference resolution. Addressing the identification of separate entities referring to the same person, such as "Father Goriot" and "Goriot," was also highlighted. Bigrams were used in order to improve the accuracy of named entities identified by the method. The results for location recognition were disappointing so location_tagger library was used for locations. Bigrams could also improve the identification of locations in future work. One challenge was the existence of spelling errors in  names but also in general. Similarity measures such as Edit distance could be used in the future to address this problem. Edit distance measures the minimum number of operations (insertions, deletions, and substitutions) required to transform one string into another. This can be used for corrections of misspelled words by finding the closest words based on their edit distance.

o	Finetune Bert for NER
Fine-tuning BERT (Bidirectional Encoder Representations from Transformers) for Named Entity Recognition (NER) has proven to be a powerful approach in text mining. BERT, as a pre-trained language model, captures rich contextual information and semantic relationships between words. By fine-tuning BERT specifically for NER using annotated datasets, we can train the model to recognize and classify named entities accurately. The fine-tuned BERT model can effectively identify and label entities such as persons, organizations, locations. Transformers library was used in our project and the conll2003 dataset was loaded from the dataset library and pretrained bert was trained on this dataset to adjust its weights for NER.
Evaluation of the model showed promising results giving high accuracy, precision, recall and f1 score, around 95%. But when predicting in the book text the results were very disappointing as none of the entities were identified correctly as Bert splitted the entities into subwords. This method is left for future work to identify what are the mistakes in the process of predicting the entities using the finetuned Bert.

 


8. Topic Modeling:
Topic modeling was employed to uncover latent topics and thematic patterns within the text corpus of "Father Goriot’’. Specifically, the Latent Dirichlet Allocation (LDA) technique was used. Initially, topic modeling was performed using the preprocessed text. Subsequently, to improve the results, bigrams and trigrams (sequences of three words) were incorporated into the topic modeling process. Bigrams and trigrams provided a more comprehensive understanding of the relationships between words. The optimal number of topics and the number of passes through the text were parameters to be optimized. 
 
Topic Modeling using bigrams
9.Relationship Extraction
Relationship extraction is a crucial task in text mining that focuses on identifying and capturing the connections, associations, and interactions between entities mentioned in a text. By extracting relationships, we can uncover valuable insights about the semantic relationships, dependencies, and patterns present within the text. The process involves techniques such as part-of-speech tagging, named entity recognition, and syntactic parsing to identify the entities involved and the verbs or phrases that express their relationships. Relationship extraction enables us to understand the dynamics, actions, and interactions between entities in a text, allowing for a deeper analysis of the narrative, thematic elements, and underlying structure. It provides a means to uncover complex networks of relationships and dependencies, facilitating tasks such as knowledge graph construction, event extraction, sentiment analysis, and information retrieval. In our text, the existing family relationships were extracted using patterns. For future work is suggested to use these relationships to link them with named entities and find more nuanced relationships. In addition, for each named entity, words that are mostly associated were extracted, but this task needs first coreference resolution to find all the sentences that are related with each character. Additionally, noun and verb phrase chunking was applied to identify subject-object relationships which led to identification of events that are related to death, love, violence, class inequality.

10. Co-occurrence Analysis of Named Entities:
Co-occurrence analysis is a method employed in text mining to examine the relationships between named entities and the surrounding context words. In the case of "Father Goriot," the words surrounding each named entity were extracted as context words. A window of five words before and after the named entity index was considered to capture the immediate context.
 


11.Knowledge Graphs
Knowledge graphs are structured representations that capture relationships between entities. They consist of nodes representing entities and edges representing connections between them. By organizing information in this way, knowledge graphs enable efficient storage, retrieval, and analysis. In text mining, knowledge graphs enhance understanding by revealing hidden patterns and facilitating inference. The networkx library was used to link named entities with words they are mostly associated with.



 
                                                                              Character-top words association


Future Work

There is space for further exploration and improvement of the analysis of our text. The following areas could be addressed in future work:
First of all, better preprocessing is recommended such as keeping stopwords that indicate location such as ‘in’, ‘on’, ‘at’ as these words can improve the accuracy of Entity recognition using specific rules. Moreover, deleting useless tokens such as urls, the last part of the book and words with low tf-idf scores. In addition, dependency parsing and coreference resolution are highly suggested to be applied to the whole text for improving the accuracy of tasks such as Relationship extraction.
Sentiment Analysis: Applying sentiment analysis techniques to the text could provide a deeper understanding of the emotional undertones and character motivations. By analyzing the sentiment expressed by characters towards each other or specific events, we can uncover hidden layers of the narrative.
Network Analysis: Constructing a network representation of the relationships between characters and analyzing their centrality and influence could offer a more comprehensive understanding of the social dynamics within the novel. Network analysis could reveal important characters or groups and their roles in shaping the plot.

Multilingual Analysis: Given the presence of French language elements in the English text, further research can be conducted to incorporate multilingual techniques. This would involve improving entity recognition and relationship extraction algorithms to handle the linguistic complexities and nuances arising from the bilingual nature of the text. The suggested model is multilingual Bert.

Conclusion
In conclusion, the text mining analysis of "Father Goriot" utilized various methods such as topic analysis, entity recognition, relationship extraction and co-occurrence analysis. These techniques provided valuable insights into the novel's themes, characters, and social context. However, there is still ample room for further improvement and exploration in this area of research. Future work could significantly improve the results found in this project using more advanced techniques.



References:
Topic Modeling in Python: Latent Dirichlet Allocation (LDA):
Topic Modeling in Python: Latent Dirichlet Allocation (LDA) | by Shashank Kapadia | Towards Data Science
Named Entity Recognition with NLTK and SpaCy:
Named Entity Recognition with NLTK and SpaCy | by Susan Li | Towards Data Science (medium.com)
Knowledge Graph & NLP Tutorial-(BERT,spaCy,NLTK):
Knowledge Graph & NLP Tutorial-(BERT,spaCy,NLTK) | Kaggle
Image:
Père Goriot, or Old Goriot, or Father Goriot eBook by Honoré de Balzac - EPUB | Rakuten Kobo Netherlands

