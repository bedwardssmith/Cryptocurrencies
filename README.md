<h1>Accountability Accounting</h1>
<h2>Purpose</h2>
<p>Accountability Accounting is interested in offering a new cryptocurrency investment portfolio to its customer.  In order to provide such a portfolio they must first decide how the cryptocurrencies should be grouped together to create a classification system for the new investments.</p>
<p>As there is no specific starting point for classification it was decided that unsupervised machine learning would be used to look for groupings, trends or other information that could assist with the classification.</p>
<h2>Analysis</h2>
<p>Unsupervised learning can be used to transform data to create intuitive representation for analysis or for use in another machine learning model or clustering algorithms.  In our analysis we first transformed data and then used clustered data to group similar objects into clusters.</p>
<p>The first step in using unsupervised machine learning is data selection.  In this case a dataset was used containing trading information for 532 different cryptocurrencies. This step is followed by data processing where data was cleansed for use by the unsupervised machine learning algorithm.</p>
<h3>Processing</h3>
<p>First step was to filter the data to include only cryptocurrencies that are being traded.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/Cryptocurrencies_trading.png">
<p>Null values were checked to ensure that all cryptocurrencies have a working algorithm.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/active_algorithms.png">
<p>The “IsTrading” column was dropped from the dataframe as it provided no relevant information for the analysis.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/remove_trading_column.png">
<p>Rows with at least one null value were then dropped from the dataframe.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/remove_rows_with_null.png">
<p>Dataframe was then filtered to include only rows where coins have been mined.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/remove_rows_where_not_mined.png">
<p>A new dataframe was the created to hold only the currency names.  The coin name was then dropped from the dataframe.</p>
<p>The get_dummies() method was then used to create variables for algorithm and prooftype which were then stored in a dataframe named “X”.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/get_dummies.png">
<p>StandardScaler fit_transform() funtion was then used to standardize the features from the X dataframe.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/standard_scaler.png">
<p>PCA was then used to reduce the dimensions to three principal components.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/df_with_3_principal_components.png">
<p>An elbow curve was created using the three dimensional dataset.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/elbow_curve.png">
<p>Using the best fit determined by the elbow curve the K-means algorithm was used to make predictions of the K clusters.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/predictions.png">
<p>A clustered dataframe was then created using the original dataframe together with the new dataframe created with the PCA dimensions.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/clustered_df.png">
<p>The coin names previously removed as well as the class holding the predictions was then added to the dataframe.</p>
<p>Using the new dataframe a 3D scatter plot was created using Plotly Express.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/3d_scatter.png">
<p>A table containing tradeable currencies was then created using hvplot.table.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/tradeable_currencies_table.png">
<p>The number of tradeable cryptocurrencies was calculated using the .count() function.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/number_of_tradeable_currencies.png">
<p>The MinMaxScaler().fit_transform() method was then used to scale the total coin supply and total coins mined.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/scale_min_max.png">
<p>A new dataframe was then created that contains the scaled data.  The coin names and class information were added to the dataframe once created.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/df_with_2_features.png">
<p>A 2D scatter plot was then created using the revised dataframe.</p>
<img src="https://github.com/bedwardssmith/Cryptocurrencies/blob/main/Resources/Images/2d_plot.png">
<h2>Results</h2>
<p>The first diagram that was created was the elbow curve which is used to determine the best K value.  When looking at an elbow curve you are looking at the point to which the line shifts to a strong horizontal line.  In our case the strong horizontal line starts at 4.  This value was then used in the K-Means model; n_clusters=4.  It was this model that was used to produce the 3D plot which shows that there are in fact 4 distinct clusters.</p>
<p>The final diagram produced is a 2D plot containing only 2 features, total coin supply and total coins mined, from this we can see that these features on their own do not create distinct clusters.</p>



