# Netflix-Data-Analysis
![img](https://user-images.githubusercontent.com/122275233/216485326-61e725f4-1971-4422-9968-d274aca21692.png)  
This ia a detailed data analysis for popular streaming service Netflix. A web-app which can be used to get recommendations for a series/movie, the app recommends a list of media according to list of entered choices of movies/series in your preferred language.  
### Table of contents
1.  **[Objective](#objective)**
3.  __[Getting data](#getting-data)__
4.  **[Preprocessing and feature selection](#preprocessing-and-feature-selection)**
5.  __[Model Selection](#model-selection)__
______ 

### Objective
The objective of this problem is to analyse users watch history and recommend them shows based on the genre that are most watched by the users.
### Getting data
Here the users watch history is analysed and based on the genres that are watched by the users a table is prepared. Here is the sample table data showing genres, actors, and tags that were most popular among the shows that a particular user has watched.  

![table](https://miro.medium.com/v2/resize:fit:720/format:webp/1*GIVTkfTQmm43uc3iC9dsog.png)  
### Preprocessing and feature selection  
Here the data is converted into the format that can be used by neural network. Here each observation in  dataset mentioned above is a TV-show and season combination. For example, Season 1 of *“13 Reasons Why”*.<sup>[1]</sup> Here genres, tags, and season number as categorical variables, and episode length as a numeric variable.  
Then a _*corelation matrix*_ is created that removes the highly co-related features like removing the overfitting that can be caused due to the corelation of crime and murder genre.  
``` X_corr = X.corr() 
columns = np.full((X_corr.shape[0],), True, dtype=bool) 
#Keep only columns with correlation less than 0.9 
for i in range(X_corr.shape[0]): 
    for j in range(i+1, X_corr.shape[0]): 
        if X_corr.iloc[i,j] >= 0.9: 
            if columns[j]: columns[j] = False 
selected_X = X[X.columns[columns]] 
```
### Model selection  
Then the best model to run on is selected keeping in mind number of nodes, the regularization coefficient, and the dropout value. For that grid search is used.  
______
### Libraries used  
* Pandas
* Numpy
* Matplotlib
* Plotly
******
### Installation and how to run  
- For installing the above mentioned libraries write the below code snippet in terminal.  
`pip install <libraryname> `   
- Then import the libraries.
- This project can be run on Google Colab.  
******
## Author
- Github: https://github.com/heema-1989/Netflix-Data-Analysis/edit/main/README.md  
- Email: heemag2002@gmail.com
________
## References
[1] https://towardsdatascience.com/using-neural-nets-to-recommend-shows-on-netflix-d4fbecffe0b0

