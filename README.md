# Connections Solver
Python notebook that helps you solve the NYT Connections game using Word2Vec embeddings and k-means clustering algorithms.

*Connections Solver* is a Python Jupyter Notebook that provides a second brain to help you solve the NYT Connections game on particularly hard days. It uses Word2Vec embeddings and k-means algorithms to predict likely Connections solutions using word-pairing similarity scores.

Two different algorithms are used: one that follows the highest similarity score pairing to find each set of words, and the other using SciPy and Sci-kit learn kmeans algorithms. Use any and all of these to help you crack the puzzle.

# Algorithms
## Load game
1. The script loads the words for the day’s Connections using Selenium ChromeDriver. Alternatively, you can manually input your own 16 words.
2. Import the pre-trained [‘glove-wiki-gigaword-50’](https://huggingface.co/fse/glove-wiki-gigaword-50) as a Word2Vec model.

## Algorithm A) “Follow the Leader”
1. Creates a matrix of similarity scores between each word pairing using the word vector model.
2. Finds the word pairing with the highest similarity score. This initiates the first set of solutions.
    1. Finds the next two words of the set that have the highest similarity scores when paired with one of the original words.
    2. Repeats 3 more times to find a total of 4 sets of words.

## Algorithm B) Classic Clustering
1. Collects all word vectors in original feature space.
    1. Depending on user input, PCA is applied to reduce dimensionality of the vectors before clustering.
2. Uses both sklearn KMeans and sciPy kmeans2 to organize the word vectors into 4 clusters.
3. Returns the words in each cluster. Note that cluster sizes often vary.
    1. If PCA was applied to operate the clustering in 2D space, each word is also plotted on a graph for easy visualization.
