Final Report: Detecting Real vs. Fake News

1. Custom Tokenizer and Lemmatizer Design

Custom Tokenizer
A simple tokenizer was created that:

  * Converts all text to lowercase.
  * Detects words with repeated letters (like “sooooo”) and replaces the repeats with a special token indicating how many letters were repeated.
    For example, “sooooo” becomes “so [REPEAT:5](REPEAT:5)”.
  * Separates punctuation marks (like !, ?, .) from words so they become individual tokens.
  * Splits the text into tokens based on spaces.

This approach helps the model recognize when words are exaggerated, which is common in fake news.

Part-of-Speech (POS) Tagging

A basic POS tagger assigns types to each word:

  * Words ending with “ing” are tagged as verbs.
  * Words ending with “ly” are tagged as adverbs.
  * Common articles and prepositions like “a”, “the”, “in” are tagged as determiners.
  * Some adjectives like “shocking” and “unbelievable” are tagged as adjectives.
  * All other words are tagged as nouns.

Lemmatizer

Using the POS tags, words are converted to their base forms:

  * For verbs, endings like “ing” or “ed” are removed and some irregular verbs are handled (e.g., “ran” becomes “run”).
  * For nouns, plural “s” endings are removed if the word is sufficiently long.
  * Other words remain unchanged.

This reduces different word forms to a single base form, simplifying the model’s task.


2. Impact on Model Performance

Repeated-Character Normalization:
  Captures emotional emphasis often present in fake news (e.g., “soooo” or “shocking!!!”). Instead of treating repeated letters as different words, this approach simplifies them while preserving emphasis information.

POS-Guided Lemmatization:
  Groups similar words by their base forms while reducing errors by considering word types.

These preprocessing steps reduce ambiguity and improve the model’s ability to detect fake news based on language style.

Both Naive Bayes and SVM classifiers performed well using this custom setup.



3. Comparison with Off-the-Shelf Pipelines

* Off-the-shelf models use built-in tokenizers and do not handle repeated characters or specific word forms explicitly.
* These models also performed well (Logistic Regression achieved approximately 95% accuracy).
* However, the custom tokenizer and lemmatizer capture specific language patterns in fake news that standard tools often miss.
* Custom preprocessing adds interpretability and may improve detection of nuanced fake news examples.


4. Visualizations

* Common words in real vs. fake news were analyzed.
* Confusion matrices were used to evaluate model predictions for real vs. fake news.

These visualizations provide insights into the linguistic differences and model behavior.

5. Conclusion

* The custom tokenizer and lemmatizer effectively handle repeated letters and word forms common in fake news.
* Simple POS tagging supports accurate lemmatization.
* This approach allows the model to focus on important language cues and achieves strong performance.
* While off-the-shelf models provide strong baselines, adding custom text processing improves results for this task.


