# Beyond Calories
# Senior Data Science Portfolio Project, Belmont University - Spring 2024

## Project Outline
This project explores the relationship between the glycemic index (GI) and oxalate contents of commonly consumed American foods.  Existing research tends to evaluate these aspects of food in isolation, rather than in tandem.  However, foods with high oxalate levels and with high glycemic index levels have both been linked to adverse health outcomes when consumed in large quantities.  This project seeks to identify overlap between these two food groups and help consumers make more informed dietary choices.

## Literature Review

Many Americans grow up learning that nutrition is all about counting calories.  While counting calories can be important under certain circumstances, reducing dietary choices down to this one component is hurtful in many ways.  Focusing purely on calories often misses the overall nutritional content of a food and can lead to unsustainable and unhealthy consumption patterns.  While more individuals have become interested in counting macronutrients throughout the day, aspects like glycemic index and oxalte values go largely unconsidered by many American consumers.  However, both of these nutritional values can play a role in a holistic dietary evaluation.  This project is aimed at raising awareness of these components and increasing the ability of individuals to track their consumption over time.  Below is a brief overview of these two nutritional components and why they matter just as much, if not more, than calories.

### Glycemic Index

Simply put, Glycemic Index (GI) is a measure of how much our blood sugar spikes after consuming different types of foods.  GI for foods is always compared to a baseline of how much a pure sugar drink spikes blood sugar levels.  For instance, a GI of 60 indicates that consuming the specified amount of this food leads to a blood sugar spike that is 60% of the spike caused by consuming the pure sugar drink.  If you're interested in learning more about how Glycemic Index is measured, you might want to watch "The Glycemic Index, Explained" by Nourishable on YouTube here: https://www.youtube.com/watch?v=85CksrhnPCM.

According to Matthew Solan, Executive Editor of Harvard Men's Health Watch, high-glycemic diets can increase risk for cardiovascular disease, strokes, and death.  Furthermore, prioritizing low-glycemic foods has long been encouraged as a component of diabetes management.  More on this can be read here: https://www.health.harvard.edu/staying-healthy/high-glycemic-diets-could-lead-to-big-health-problems. With Alzheimer's Disease now being labelled as Type III diabetes, there is no shortage of reasons why consumers may want to be more mindful of the glycemic index and how it plays into their dietary choices.

### Oxalate Value

Oxalate, or oxalic acid, is a naturally ocurring compound found in plant foods, particularly in leafy greens.  In recent years, there have been mixed opinions on the effects of oxalates on the body, with some people dubbing them "antinutrients".  During the digestive process, oxalate binds to minerals in the body to form compounds, such as calcium oxalate which make up kidney stones.  More information on oxalates can be found here: https://www.healthline.com/nutrition/oxalate-good-or-bad#TOC_TITLE_HDR_2

Anecdotally, both of my parents have suffered from kidney stones, as well as some close friends.  Additionally, a former coworker of mine consistently suffered severe and unexplainable neuropathy after consuming foods that were high in oxalates.  Although research is inconclusive as to whether the general population should monitor their oxalate intake, the ability to do so is incredibly important to people like those I mention here.  For this reason, oxalate values have also been included in this project.

### Previous Studies

One notable study found during the planning of this project was "Effect of ethnicity on glycaemic index: a systematic review and meta-analysis" available here: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4521176/#.  In this study, Wolever et al. conducted a meta-analysis to ascertain whether ethnicity plays a role in glycemic index values of foods.  This was deemed necessary after Health Canada asserted that labeling foods with GI values would be misleading to to the effect of ethnicity on glycemic index.  However, using 95% confidence levels, researchers found that evidence suggests GI values are not affected by ethnicity, with a possible exception of rice.  However, there is some question of whether the difference was due to genetics or to the chewing patterns of different cultures, and the number of study participants supporting this difference was notably low.

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
