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

### Variables

Below is a list of the variables included in the datasets.  Additionally, variables stemming from the USDA Food Composition Database have a complete data dictionary available here: https://think.cs.vt.edu/corgis/blockpy/ingredients/ courtesy of the CORGIS Dataset Project.

DHQ Food Group Code - Unique code for the food group this item belongs to.

DHQ Food Group Name - The general food category this item belongs to.

CSFII 1994-96 Food Code - A unique ID for this food item.

Category - The general category of food that this item belongs to.

Description - A full description of this food item, including its category and some sub categories.

Nutrient Data Bank Number - A unique ID for this food item.

Data.Alpha Carotene - Alpha Carotene is a form of carotene with a Beta-ionone ring at one end and an Alpha-ionone ring at the opposite end. It is the second most common form of carotene. Alpha Carotene is common in yellow-orange and dark-green vegetables. Measured in micrograms (mcg).

Data.Beta Carotene - An organic, strongly colored red-orange pigment abundant in plants and fruits. Measured in micrograms (mcg).

Data.Beta Cryptoxanthin - Cryptoxanthin is a natural carotenoid pigment. It has been isolated from a variety of sources including the petals and flowers of plants in the genus Physalis, orange rind, papaya, egg yolk, butter, apples, and bovine blood serum. In the human body, cryptoxanthin is converted to vitamin A (retinol) and is, therefore, considered a provitamin A. As with other carotenoids, cryptoxanthin is an antioxidant and may help prevent free radical damage to cells and DNA, as well as stimulate the repair of oxidative damage to DNA. Measured in micrograms (mcg).

Data.Carbohydrate - In food science and in many informal contexts, the term carbohydrate often means any food that is particularly rich in the complex carbohydrate starch (such as cereals, bread and pasta) or simple carbohydrates, such as sugar (found in candy, jams, and desserts). Carbohydrates are found in wide variety of foods. The important sources are cereals (wheat, maize, rice), potatoes, sugarcane, fruits, table sugar(sucrose), bread, milk, etc. Starch and sugar are the important carbohydrates in our diet. Starch is abundant in potatoes, maize, rice and other cereals. Sugar appears in our diet mainly as sucrose(table sugar) which is added to drinks and many prepared foods such as jam, biscuits and cakes. Glucose and fructose are found naturally in many fruits and some vegetables. Glycogen is carbohydrate found in the liver and muscles (as animal source). Cellulose in the cell wall of all plant tissue is a carbohydrate. It is important in our diet as fibre which helps to maintain a healthy digestive system. Measured in grams (g) by difference.

Data.Cholesterol - An organic molecule that is a sterol (or modified steroid), a type of lipid molecule, and is biosynthesized by all animal cells, because it is an essential structural component of all animal cell membranes; essential to maintain both membrane structural integrity and fluidity. Cholesterol enables animal cells to dispense with a cell wall (to protect membrane integrity and cell viability), thereby allowing animal cells to change shape and animals to move (unlike bacteria and plant cells, which are restricted by their cell walls). Since all animal cells manufacture cholesterol, all animal-based foods contain cholesterol in varying amounts. Measured in milligrams (mg).

Data.Choline - A water-soluble vitamin. Humans make choline in the liver. Whether dietary or supplemental choline is beneficial or harmful to humans is undefined. Measured in milligrams (mg).

Data.Fiber - Dietary fiber or roughage is the indigestible portion of food derived from plants. It has two main components: soluble fiber and insoluble fiber. Measured in grams (g).

Data.Lutein and Zeaxanthin - Lutein is synthesized only by plants and like other xanthophylls is found in high quantities in green leafy vegetables such as spinach, kale and yellow carrots. Zeaxanthin is one of the most common carotenoid alcohols found in nature. It is important in the xanthophyll cycle. Synthesized in plants and some micro-organisms, it is the pigment that gives paprika (made from bell peppers), corn, saffron, wolfberries, and many other plants and microbes their characteristic color. This combined quantity of these two compounds is measured in micrograms (mcg).

Data.Lycopene - Lycopene is a bright red carotene and carotenoid pigment and phytochemical found in tomatoes and other red fruits and vegetables, such as red carrots, watermelons, gac, and papayas, although not in strawberries, or cherries. Although lycopene is chemically a carotene, it has no vitamin A activity. Foods that are not red may also contain lycopene, such as asparagus and parsley. Measured in micrograms (mcg).

Data.Niacin - Also known as vitamin B3 and nicotinic acid, is an organic compound with the formula C6H5NO 2 and, depending on the definition used, one of the 20 to 80 essential human nutrients. Measured in miligrams (mg).

Data.Protein - Proteins are essential nutrients for the human body. They are one of the building blocks of body tissue, and can also serve as a fuel source. As a fuel, proteins provide as much energy density as carbohydrates: 4 kcal (17 kJ) per gram; in contrast, lipids provide 9 kcal (37 kJ) per gram. There are nine essential amino acids which humans must obtain from their diet in order to prevent protein-energy malnutrition and resulting death. Humans need the essential amino acids in certain ratios. Dietary sources of protein include both animals and plants: meats, dairy products, fish and eggs as well as grains, legumes and nuts. Measured in grams (g).

Data.Retinol - Retinol, also known as Vitamin A1, is a vitamin found in food and used as a dietary supplement. As a supplement it is used to treat and prevent vitamin A deficiency. Measured in micrograms (mcg).

Data.Riboflavin - Riboflavin, also known as vitamin B2, is a vitamin found in food and used as a dietary supplement. It is nearly always well tolerated. Normal doses are safe during pregnancy. Riboflavin is in the vitamin B group. It is required by the body for cellular respiration. Food sources include eggs, green vegetables, milk, and meat. Measured in milligrams (mg).

Data.Selenium - Selenium is a chemical element with symbol Se and atomic number 34. Selenium salts are toxic in large amounts, but trace amounts are necessary for cellular function in many organisms, including all animals. Measured in micrograms (mcg).

Data.Sugar Total - Sugar is the generalized name for sweet, short-chain, soluble carbohydrates, many of which are used in food. They are composed of carbon, hydrogen, and oxygen. There are various types of sugar derived from different sources. Simple sugars are called monosaccharides and include glucose (also known as dextrose), fructose, and galactose. The table or granulated sugar most customarily used as food is sucrose, a disaccharide. (In the body, sucrose hydrolyses into fructose and glucose.) Other disaccharides include maltose and lactose. Longer chains of sugars are called oligosaccharides. Chemically-different substances may also have a sweet taste, but are not classified as sugars. Some are used as lower-calorie food substitutes for sugar, described as artificial sweeteners. Measure in grams (g).

Data.Thiamin - Thiamin (or thiamine) is one of the water-soluble B vitamins. It is also known as vitamin B1. Thiamin is naturally present in some foods, added to some food products, and available as a dietary supplement. This vitamin plays a critical role in energy metabolism and, therefore, in the growth, development, and function of cells. Measured in milligrams (mg).

Data.Water - The amount of water in the food. Measured in grams (g).

Data.Fat.Monosaturated Fat- Fatty acids that have one double bond in the fatty acid chain with all of the remainder carbon atoms being single-bonded. Measured in grams (g).

Data.Fat.Polysaturated Fat - Lipids in which the constituent hydrocarbon chain possesses two or more carbon-carbon double bonds. Polyunsaturated fat can be found mostly in nuts, seeds, fish, algae, leafy greens, and krill. "Unsaturated" refers to the fact that the molecules contain less than the maximum amount of hydrogen (if there were no double bonds). Measured in grams (g).

Data.Fat.Saturated Fat - A saturated fat is a type of fat in which the fatty acids all have single bonds. Measured in grams (g).

Data.Fat.Total Lipid - Lipids comprise a group of naturally occurring molecules that include fats, waxes, sterols, fat-soluble vitamins (such as vitamins A, D, E, and K), monoglycerides, diglycerides, triglycerides, phospholipids, and others. The main biological functions of lipids include storing energy, signaling, and acting as structural components of cell membranes. Measured in grams (g).

Data.Major Minerals.Calcium - Calcium is a mineral needed to build and maintain strong bones and teeth. It is also very important for other physical functions, such as muscle control and blood circulation. Calcium is not made in the body - it must be absorbed from food. To effectively absorb calcium from food, Vitamin D is needed. Measured in milligrams (mg).

Data.Major Minerals.Copper - Copper is an essential trace element that is vital to the health of all living things (humans, plants, animals, and microorganisms). In humans, copper is essential to the proper functioning of organs and metabolic processes. Measured in milligrams (mg).

Data.Major Minerals.Iron - Iron is a mineral that is naturally present in many foods, added to some food products, and available as a dietary supplement. Dietary iron has two main forms: heme and nonheme. Plants and iron-fortified foods contain nonheme iron only, whereas meat, seafood, and poultry contain both heme and nonheme iron. Measured in milligrams (mg).

Data.Major Minerals.Magnesium - Magnesium is an essential mineral for human nutrition. Magnesium is needed for more than 300 biochemical reactions in the body. It helps to maintain normal nerve and muscle function, supports a healthy immune system, keeps the heart beat steady, and helps bones remain strong. It also helps regulate blood glucose levels and aid in the production of energy and protein. There is ongoing research into the role of magnesium in preventing and managing disorders such as high blood pressure, heart disease, and diabetes. However, taking magnesium supplements is not currently recommended. Diets high in protein, calcium, or vitamin D will increase the need for magnesium. Most dietary magnesium comes from vegetables, such as dark green, leafy vegetables. Measured in milligrams (mg).

Data.Major Minerals.Phosphorus - Phosphorus is an essential macromineral, included in almost all foods. Phosphorus is the second most abundant mineral nutrient in the body, after calcium. This mineral is part of all cells, especially cell membranes, and is essential to bone strength, because it's the main structural component of bones and teeth, as calcium phosphate. Phosphorus is also an important element in energy production. Measured in milligrams (mg).

Data.Major Minerals.Potassium - Potassium is a mineral and electrolyte that helps nerves to function and muscles to contract, among many other tasks. Potassium sources include leafy greens, fruit from vines, root vegetables, and citrus fruits. Measured in milligrams (mg).

Data.Major Minerals.Sodium - Salt, also known as sodium chloride, is about 40 percent sodium and 60 percent chloride. It adds flavor to food and is also used as a preservative, binder, and stabilizer. The human body needs a very small amount of sodium - the primary element we get from salt - to conduct nerve impulses, contract and relax muscles, and maintain the proper balance of water and minerals. But too much sodium in the diet can lead to high blood pressure, heart disease, and stroke. Measured in milligrams (mg).

Data.Major Minerals.Zinc - Zinc is found in cells throughout the body. It is needed for the body's defensive (immune) system to properly work. It plays a role in cell division, cell growth, wound healing, and the breakdown of carbohydrates. Zinc is also needed for the senses of smell and taste. Measured in milligrams (mg).

Data.Vitamins.Vitamin A - RAE - Vitamin A is a fat soluble vitamin that is also a powerful antioxidant. Vitamin A plays a critical role in maintaining healthy vision, neurological function, healthy skin, and more. Measured in retinol activity equivalents (micrograms, or mcg).

Data.Vitamins.Vitamin B12 - Vitamin B12, also called cobalamin, is a water-soluble vitamin that has a key role in the normal functioning of the brain and nervous system, and the formation of red blood cells. It is one of eight B vitamins. It is involved in the metabolism of every cell of the human body, especially affecting DNA synthesis, fatty acid and amino acid metabolism. No fungi, plants, nor animals (including humans) are capable of producing vitamin B12. Only bacteria and archaea have the enzymes needed for its synthesis. Proved sources of B12 are animal products (meat, fish, dairy products) and supplements. Measured in micrograms (mcg).

Data.Vitamins.Vitamin B6 - Vitamin B6 is involved in many aspects of macronutrient metabolism, neurotransmitter synthesis, histamine synthesis, hemoglobin synthesis and function, and gene expression. Vitamin B6 is widely distributed in foods in both its free and bound forms. Measured in milligrams (mg).

Data.Vitamins.Vitamin C - Vitamin C, also known as ascorbic acid and L-ascorbic acid, is a vitamin found in food and used as a dietary supplement. Foods that contain vitamin C include citrus fruit, tomatoes, and potatoes. Measured in milligrams (mg).

Data.Vitamins.Vitamin E - Vitamin E refers to a group of compounds that include both tocopherols and tocotrienols, usually found in various oils (corn oil, soybean oil, wheat germ oil). Measured in milligrams (mg).

Data.Vitamins.Vitamin K - Vitamin K (Phylloquinone) is a group of structurally similar, fat-soluble vitamins the human body requires for complete synthesis of certain proteins that are prerequisites for blood coagulation and which the body also needs for controlling binding of calcium in bones and other tissues. Measured in micrograms (mcg).

Food Group - The category of food this item is classified as.

Subgroup - The subcategory of food this item is classified as.

Food Item - The specific food itme.

Serving size - The serving size of the food.  Given in inconsistent units.

Oxalate Category - The oxalate classification given (Very high, High, Moderate, Low, Very Low, Little or None).

Oxalate Value - The amount of oxalates in a given food, measured in mg.

Food Description in 1994-96 CSFII - A brief desciption of the food item, preparation methods, food type.

GI Value - The glycemic index value of the food item.

GI Links to:   Foster-Powel K, Holt, SHA, Brand-Miller JC. International table of glycemic index and glycemic load values: 2002. Am J Clin Nutri 2002;76:5-56. - Where the GI data originated.


# Analysis

Analysis for this project can be found in the "Beyond Calories Analysis" notebook.

## Comparing GI of Foods Based on Cholesterol Level

After my preliminary analysis of the data, I was curious whether there was any significant difference in the GI value of high versus low cholesterol foods.  To determine this, a permutation test was used with a confidence level of 95%.  For this test, "high" cholesterol foods were those in the 75 percentile and higher.

Under 10000 simulations, a statistically significant difference in the glycemic indices of high and low/average cholesterol foods was found.  Foods with higher cholesterol levels had significantly lower glycemic indices than foods with low and average cholesterol levels.  The p-value was found to be 0.0, indicating with 95% confidence I can reject the null hypothesis that GI values are equal for foods of differing cholesterol levels.

## Cholesterol and Oxalate Content

Next, I wanted to know if cholesterol level affects oxalate level of foods.  This seems like it should be the case since cholesterol levels tend to be higher in animal-based foods and oxalate levels are higher in plant-based foods.  Because the oxalate dataset is somewhat smaller, I chose to bootstrap a confidence interval to answer this question.  Once again "high" cholesterol was determined as being at or above the 75th percentile.  Notably, this threshold changed for this test.  This is because the 75th percentile cholesterol cutoff for the smaller oxalate inclusive dataset dropped from about 60mg to about 30mg.

A confidence interval of 95% was again chosen.  This time, a statistically significant difference was found at a 95% confidence level under 1,000,000 simulations.  The observed average oxalate values for low and average cholesterol foods was about 12mg, while the bootstrapped confidence internal for the oxalate value of high cholesterol foods was between roughly 0mg and 2mg.  There is enough evidence to reject the null hypothesis that oxalate values are even across foods of various cholesterol levels.

## Classification Matters Using Random Forest

Since the datasets combined in this project each use their own food item classifications, I wnted to evaluate whether one of these classification systems was better predicted by purely the nutritional informaiton about the food item.  To check this, I created two random forest models, one predicting "Food Group" and the other predicting "Subgroup".  Both models were trained and evaluated using the triple_threat_df, the smallest but of the datasets, but the one with the most predictors.

For the Food Group model, bootstrapping had a negligible effect.  Average CV accuracy without bootstrapping was 83.11%, and average CV accuracy with boostrapping was 84.23%.

Surprisingly, the food Subgroup model performed worse.  Average CV accuracy without bootstrapping was 74.45% and with bootstrapping was 72.23%.  The difference of these models showcased how important classification is when drawing conclusions from our data.

## More Classification Matters

After noticing the difference in the Random Forest models, I was curious if a KNN model would perform any better in predicting food Subgroup, the weaker of the two categories.  After manually trying a few values for k, 8 seemed to produce the best results with 0.6 accuracy score.  This was even worse than the Random Forest.  So, I then wrote a function to include a cross validation component and attempt to identify the best k value, in case I hadn't manually tried it.  This function found the best k to be 1 with an accuracy score of a sorry 0.5109, essentially a coin flip.  As poor as the Random Forest Subgroup model performed compared to the model for Food Group, it still outshone KNN by a longshot.

## PCA

Notably, a Principal Component Analysis showed that no one variable was able to account for a significant amount of the predictive power.  That said, Niacin, Riboflavin, and Water were the top 3 most influential variables.

## Predicting Glycemic Index with Nutrient Data

Finally, I used SVM to predict GI using only the nutrient data.  I started with a radial basis function kernal since this is a more complex problem that hasn't seemed to have much luck with linear relationships.  The initial r^2 was a low 0.3512.  After some fine-tuning using GridSearch, the best model parameters identified were 'C': 100, 'epsilon': 1, 'gamma': 0.1 with a much improved but still not incredible r^2 score of 0.6546.

