# Plagiarism-Detector-Ngrams
# Machine Learning

This is a Plagiarism Detection Project. It classifies an answer text as plagiarzed or non-plagiarized depending on its similarity with a source text. 

#DATA
The data for this project is taken from https://ir.shef.ac.uk/cloughie/resources/plagiarism_corpus.html

The corpus folder contains 100 text files(out of which 5 are original wikipedia texts). Each text file is associated with one Task(A-E) and one Category of plagiarism. Each task, A-E, is a question about a different topic and the 95 text files include the answers to any one of them.

Categories of plagiarism: 
cut: An answer is plagiarized; it is copy-pasted directly from the relevant Wikipedia source text.
light: An answer is plagiarized; it is based on the Wikipedia source text and includes some copying and paraphrasing.
heavy: An answer is plagiarized; it is based on the Wikipedia source text but expressed using different words and structure. Since this doesn't copy directly from a source text, this will likely be the most challenging kind of plagiarism to detect.
non: An answer is not plagiarized; the Wikipedia source text is not used to create this answer.
orig: This is a specific category for the original, Wikipedia source text. We will use these files only for comparison purposes.

This project implements stratified random sampling to randomly split data by task & plagiarism amount. Stratified sampling ensures that we get training and test data that is fairly evenly distributed across task & plagiarism combinations. Approximately 25% of the data is held out for testing and 75% of the data is used for training.

#Similarity Features based on N-grams
Containment is used for this purpose. Containment is defined as the intersection of the n-gram word count of the Wikipedia Source Text (S) with the n-gram word count of the Student Answer Text (S) divided by the n-gram word count of the Student Answer Text.
$$ \frac{\sum{count(\text{ngram}_{A}) \cap count(\text{ngram}_{S})}}{\sum{count(\text{ngram}_{A})}} $$
If the two texts have no n-grams in common, the containment will be 0, but if all their n-grams intersect then the containment will be 1.

