# MovieLens Recommendation Systems

**Python · Recommendation Systems · Collaborative Filtering · Matrix Factorization · Keras**

A notebook-based study of movie recommendation methods using MovieLens 1M, from genre similarity to latent-factor rating prediction.

## Dataset and scope

Saved notebook outputs show **1,000,209 ratings**, **6,040 users** and **3,883 movies**. Movie IDs are not contiguous: the maximum ID is 3,952, which is not the movie count.

## Explore the notebooks

| Notebook | Focus |
| --- | --- |
| [Data Processing](Data_Processing.ipynb) | Load MovieLens files, map user attributes and export tab-separated CSVs |
| [Content-Based and Collaborative Filtering](Content_Based_and_Collaborative_Filtering_Models.ipynb) | Genre TF-IDF, cosine similarity and exploratory neighborhood methods |
| [SVD Model](SVD_Model.ipynb) | Matrix factorization, personalized recommendations and Surprise SVD evaluation |
| [Embedding Model](Deep_Learning_Model.ipynb) | Keras user/movie embeddings with a dot-product rating predictor |

Links above open the notebooks **in this repository**.

## Workflow

1. Load user, movie and rating records.
2. Explore movie genres and rating distributions.
3. Create genre-based recommendations using TF-IDF similarity.
4. Explore collaborative filtering and matrix factorization.
5. Fit an embedding-based rating predictor.
6. Rank unseen movies for an example user.

## Results from saved outputs

| Method | Saved result | Evaluation context |
| --- | ---: | --- |
| Surprise SVD | **0.8736 mean RMSE** | Five-fold evaluation |
| Keras embedding model | **0.8616 minimum validation RMSE** | Best validation epoch: 17; 90/10 training/validation split |

These are **historical notebook outputs, not newly reproduced results**. The two methods use different evaluation procedures, so their values should not be treated as a controlled head-to-head comparison.

The SVD notebook recommends movies such as *Witness* and *Rain Man* for example user 1310. The embedding notebook produces a ranked list for user 2000, including *It's a Wonderful Life* and *Pather Panchali*. These lists demonstrate output format, not independently measured recommendation quality.

### Existing recommendation visuals

![SVD recommendation example](images/SVD-Recommendation.png)

![Embedding-model recommendation example](images/Deep-Learning-Rec.png)

*Existing repository illustrations associated with the recommendation examples.*

## Important evaluation limitations

- The neighborhood-CF notebook operates on rows containing user IDs, movie IDs and ratings rather than a correctly constructed user-by-item ratings matrix. Its RMSE outputs are therefore not reliable measures of movie-rating prediction quality.
- The Keras notebook selects its best epoch on validation loss; no independent final test result is shown.
- Random rating splits do not measure performance on new users, new items or future interactions.
- The genre recommender can return the input movie when similarity ties occur; explicit self-exclusion would improve it.
- The notebooks use legacy Python/Keras/Surprise/scikit-learn APIs and require modernization before a clean run with current packages. The embedding notebook also references `RNG_SEED` without defining it locally.

## Running the project

The repository includes source MovieLens files under `dat/`, processed CSVs, `CFModel.py` and `weights.h5`. Start with the data-processing notebook, then explore the modeling notebooks. Despite their names, the processed CSV files use tab separators.

Dependencies used include pandas, NumPy, SciPy, matplotlib, seaborn, scikit-learn, wordcloud, scikit-surprise, Keras and h5py. Exact dependency versions and a modern reproducible environment have not been established; this README update does not rerun training.

[MovieLens 1M dataset source](https://grouplens.org/datasets/movielens/1m/)

## Attribution and license

The existing notebooks and original README reference [James Le's MovieLens tutorial repository](https://github.com/khanhnamle1994/movielens). The [MIT license](LICENSE) credits **James Le, 2018**. This repository presents that educational implementation; Hiral Choksi's specific extensions are not documented here. Original attribution and licensing are retained.

## Skills explored

Data preparation · Recommender systems · TF-IDF · Cosine similarity · Collaborative filtering · SVD · Embeddings · Rating prediction · Model evaluation
