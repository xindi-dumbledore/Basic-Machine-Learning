#designing-ml-systems #data 

p.g. 124 of *[[Designing Machine Learning Systems]]*

## Types of missing values
### Missing not at random (MNAR)
- The reason a value is missing is because of the true value itself
- e.g. people with higher income value don't report their income

### Missing at random (MAR)
- The reason a value is missing is not due to the value itself, but due to another observed variable
- e.g. Age values are often missing for respondents of the gender A, which might be because the people of gender A in the survey don't like disclosing their age

### Missing completely at random (MCAR)
- No patten in when the value is missing
- This type of missing is very rare

## Handling Missing values
### Deletion
- Column deletion
	- Remove the variable if most of them are missing
	- Drawback: might remove important information
- Row deletion
	- Can work when the missing values are completely at random and the number of examples with missing values is small, such less than 0.1%
	- Drawback
		- Can remove important information that the model needs to make predictions, especially if the missing values are not at random (MNAR)
		- Can generate biases in the model if the missing values are at random (MAR)
### Imputation
- Fill with defaults, mean, median or mode
- Drawback
	- Risk injecting your own bias into and adding noise to your data, or worse, [[Data Leakage]]