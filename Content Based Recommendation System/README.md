# **NETFLIX RECOMMENDATION SYSTEM**
This is a content based recommendation system. I have used pandas, neattext, and scikit learn's cosine_similarity and CountVectorizer. This method looks at how similar the conent of the movies is, such as their directors, cast, genre, rating, description and depending on that is recommends movies.

I have uploaded tow notebooks.
1. One with the the entire flow and more data description. This is more flexible, less organized.
2. One where the entire process has been automated using class and functions. Just call the automate() function. This is more organized, neat, but lacks flexibility.

# **LOGIC AND FLOW**

1. Clean the data and seperate the data into 2 different datasets(Movie and TV Shows)
2. Remove stopwords(the,a,and,etc.) and special characters(!,&,%,etc.) from the text as they might skew the analysis and hinder the recommendation system's output.
3. Vectorize the desired columns of both the datasets, these will be used for calculating cosine simlarity. Vectorizing is similar to one hot encoding where text is split into tokens/words/bag-of-words and values are alotted. 1 if the word/token/bag-of-words is present else 0. 
4. These vecotized columns are concatinated into a single dataset where rows are movie or tv shows and columns are  word/token/bag-of-words.
5. Cosine Similarity of the two vectorized datasets is calculated. Values are between 0 and 1. Higher the value of Movie 1 and Movie 2, implies they are smililar and movie 2 shold be recommended to someone who likes movie 1.
6. A recommendation function is created, where given an input movie/tv show, the cosine values of other movies/tv shows is compared and the top 5 movies/tv shows with highest cosine values are recommended. 

# **COSINE SIMILARITY**
Takes the concatenated vectorized datasets as input and calculates cosine_similarity. Cosine_similarity calculates angle between 2 vectors, here each vector is the vectorized data of a movie. 

$$
\text{Cosine Similarity (A, B)} = \frac{A \cdot B}{\|A\| \|B\|}
$$

Where A and B are of the form: [0,1,1,0,0,........] and A.B is the dot product of the vectors, and \|A\| \|B\| is the product of the magnitude of these vectors.

The resulting output is square matrix of the size = number of movies/tv show. Each cell will have a value between 0 and 1, where 0 means no co-relation/similarity between the 2 movies and 1 means both movies are the same.

For example, if the cosine value at matrix location [7,50] is 0.854 means the simialiry between Movie Number 8 and Movie Number 51 is high.

The higher the value, the more similar/co-related the movies/tv shows and vice versa.
