\setcounter{page}{1}
\pagenumbering{arabic}
\setlength{\parindent}{0.5in}

# Introducción

This section is meant to introduce the background and objective of the research conducted for this thesis.
The purpose of the first section of this chapter is to provide a concise summary of the study issue.
Following the background are the objectives of the research.
The contributions of this thesis are covered in the next section.
Finally, here is a quick outline of the chapters of this thesis. 


## Contexto   
<!-- Context -->
Model Driven Engineering (MDE) speeds up the process of making high-quality software and keeps people from having to write the same solutions over and over [@mde_in_practice].
It is a useful technique for software development since models facilitate the communication between requirements and implementation phases of the software lifecycle.
Simultaneously conveying a more complete picture, models may also be used to reach agreement on a certain point of view or idea.

Model Driven Engineering and Machine Learning (ML-MDE) refers to the application of ML (Machine Learning) techniques to MDE issues.
As stated previously, the model (or meta-model)[^1] is the primary artifact in MDE, and can be represented as a graph.
In order to apply ML techniques, it must be transformed into a lower level representation, such as text.


[^1]: When we denote _(meta-)model_ we are not referring to just meta-models but possibly to any model that can be used to describe a system. On the contrary, with _meta-model_ we want to denote only meta-models. This is because we intend to expand this work to support virtually any kind of model, not just those that are used as proof of concept. The term is used broadly to maintain consistency with the rest of the literature.

## Objetivos

<!-- Objective -->


We demonstrate the use of RoBERTa[@liu2019roberta], a transformer-based architecture to support the construction of models by means of a recommender system able to predict a masked element of choice in a textual representation of the (meta-)model.



## Contribuciones

This dissertation has produced the publication of a short work titled "Towards a Deep Learning Architecture for Software Models" [@towards_dl_archs], in which the beginning steps of this investigation are explored.


