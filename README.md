# TV Show Lifespan

The objective of my project was to predict the lifespan of a tv show. In particular, the question I wanted to answer was, "Can I predict the number of seasons a tv series will run for?"

**Tools used:** Selenium, pandas, sklearn, statsmodels, yellowbrick

**Features:** Release Year, Season 1 rating, Number of episodes per season, genre, MPAA Rating, production company (collected but not included in final model)

**Target Variable:** Number of Seasons


# Data Collection

To start, I scraped data on 1,000 tv shows from [RatinGraph](https://www.ratingraph.com/tv-shows/). Then I scraped [IMDb](https://www.imdb.com/?ref_=nv_home) for the MPAA rating and production companies for each show I collecting from RatinGraph.


[RatinGraph Scrape](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/Ratingraph_scrape_selenium.ipynb)

[IMDb Scrape](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/imdb_scrape_selenium.ipynb)

# Data Processing

I cleaned the RatinGraph data, eventually finding and removing outliers for number of episodes per season for a few shows. I also combined genres that occured fewer than 7 times into an "others" category. I created a dummy variable column for each genre. Next, I cleaned the data from IMDb, removing duplicates and shows that did not have a valid MPAA rating. I then merged the two data frames. 

After each milestone in data processing, I created an EDA notebook to study the baseline model. Those notebooks can be seen in the appendix.

[RatinGraph Data Processing (including inner merge with IMDb data)](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/tv_show_data_processing.ipynb)

[IMDb Data Processing](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/imdb_data_processing.ipynb)



# Regularization

Throughout the EDA notebooks (in appendix), I tested Linear Regression, Polynomial Regression, Lasso, and Ridge. I decided to move forward focusing on Lasso and Ridge, and used LassoCV and RidgeCV to make my final decision of using RidgeCV to build my model.


[Lasso vs. Ridge Regularization](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/Regularization.ipynb)

# Final Model Choice Analysis

The final RidgeCV model had an alpha of 10, R^2 of ~.37, and Mean Absolute Error of ~1.6 seasons on the test set.

[RidgeCV Analysis](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/Final_model_choice_analysis.ipynb)

# Presentation

[Final Presentation Slidedeck](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/TV_Show_Lifespan_Slidedeck.pdf)

## Appendix

[First EDA - Basic Model (Train set only)](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/first_df_EDA_basic.ipynb)

[Second EDA - Model With Genres (Train set only)](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/second_df_EDA_genres_added.ipynb)

[Third EDA - Model With MPAA Rating (Train set only)](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/third_EDA_MPAA_added.ipynb)

[Fourth EDA - Model With Production Company (Train set only)](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/fourth_EDA_production_comp_added.ipynb)

[Model with Production Company (Train - Val)](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/Model_Train_Test_including_prod_co.ipynb)

[Model without Production Company (Train - Val)](https://github.com/Neda-Sal/tv_show_lifespan/blob/master/Model_Train_Test_without_prod_co.ipynb)



