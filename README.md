# Beyond Calories
# Senior Data Science Portfolio Project, Belmont University - Spring 2024

## Project Outline
This project explores the relationship between the glycemic index (GI) and oxalate contents of commonly consumed American foods.  Existing research tends to evaluate these aspects of food in isolation, rather than in tandem.  However, foods with high oxalate levels and with high glycemic index levels have both been linked to adverse health outcomes when consumed in large quantities.  This project seeks to identify overlap between these two food groups and help consumers make more informed dietary choices.

## Literature Review


## Data

Finding free and publicly available data to use for this project formatted for python analysis proved somewhat challenging.  Additionally, the publicly available datasets discovered during this project generally looked at one element, such as glycemic index or oxalate value, in isolation from other nutrient values.  Additionally, the one dataset of oxalate values which was found was only accessible as a .pdf file.

As a result, the first phase of this project involved the creation of a new and publicly available dataset which could be used for future holistic nutritional analysis.  The creation of this dataset takes place in the notebook "Beyond Calories Dataset Creation & Cleaning" available in this repository.  The datasets used and the final datasets are available under the "Data" folder of this repository and may be used for continued research.

The datasets combined for the new datasets were:

National Cancer Institute Glycemic Index Dataset:
https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjYhIbA6ZuEAxX7J0QIHepYAkoQFnoECBYQAQ&url=https%3A%2F%2Friskfactor.cancer.gov%2FDHQ%2Fdatabase%2Fgi_values.csfii_94-96_foodcodes.xls&usg=AOvVaw3E1gKJbWMxXkPdBfP8v2ub&opi=89978449

United States Department of Agriculture’s Food Composition Database as made available through the CORGIS Dataset Project:
https://think.cs.vt.edu/corgis/blockpy/ingredients/

UCI Kidney Stone Center Oxalate Content Dataset:
https://ucikidneystonecenter.com/wp-content/uploads/2020/06/Oxalate-Content-of-Foods.pdf

Upon some inspection, it was found that the glycemic index dataset and the food composition database shared a the same set of unique codes for food items, under different column names.  This enabled these datasets to be easily combined using a join on the unique code.  This combined dataset is referenced as gi_nutrient_df in the "Beyond Calories Analysis" notebook within this project repository.

Unfortunately, the oxalate dataset shared no values with the other two datasets and was significantly smaller.  After converting the .pdf file into a properly formatted excel spreadsheet, this dataset was manually combined with the glycemic index dataset.  For each food in the oxalate dataset, a glycemic index value of a corresponding food was added, along with the food's unique code.  For foods with multiple glycemic indices, one representation of each index was added.  This methodology was chosen in part due to constraints on time and resources.  Furutre projects may benefit from expanding the oxalate dataset to include all glycemic index matches, including those with repeated values.  The benefit of this addition would be the inclusion of more unique food codes.  An increased number of datapoints and unique food codes allows this dataset to later be paired with a greater number of entries from the Food Composition dataset, increasing the overall robustness of the study.

After the combined oxalate value and gycemic index dataset was created, this dataset was combined with the glycemic index and nutrient dataset using an inner join on the unique food code.  While this dataset is the smallest of the three, it has the largest number of variables and allows for the most holistic nutrional analysis.
