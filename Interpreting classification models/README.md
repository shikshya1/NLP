# Interpreting Classification Models

When we are building classification models; we are most of the time concerned about the performance criteria (how accurate the model is to classify the output labels). We donot look for explanations as to why it decided to classify the input to a certain class. But there are situations where questioning the decision of classification model becomes necessary.

Suppose we are building classifier that identifies psam emails. It identifies certain email as 'spam' and moves it to spam folder rather than placing it in inbox folder without the need of human intervention. But no NLP models are 100% accurate. We still arenot able to build language models that can accurately understand ambiguity and complexity of natural language. So, if we have a certain way to explian what features are prominent in making a decision whether to mark an email as ham or spam will help humans to understand the model and how it will perform in other similar real world data.  As the interest in interpretability of model is growing, explaining predictions of model will help to assessing trust of people using it. We can use LIME and Shap for this purpose.


## LIME (Local Interpretable Model-agnostic Explanations)

The main reason that author proposed LIME in the original paper was to understand the reasons behind predictions of machine learning models that are usually treated as black box. The authors have argued that is important to trust a model to behave in reasonable ways while using for decision making pupose where predictions cannot be acted upon on blind faith. LIME  learns an interpretable model locally around the prediction.  LIME builds sparse linear models around an individual prediction in its local vicinity.


## SHAP (SHapley Additive exPlanations)

SHAP assigns each feature an importance value for a particular prediction. Its novel components include: (1) the identification of a new class of additive feature importance measures, and (2) theoretical results showing there is a unique solution in this class with a set of desirable properties.


References:

https://arxiv.org/pdf/1602.04938.pdf : Why Should I Trust You?”
Explaining the Predictions of Any Classifier

https://arxiv.org/abs/1705.07874 : A Unified Approach to Interpreting Model Predictions
