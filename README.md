# Synthetic World Populations
Exploration of different methods for sampling from distributions using the example of world population. In this exploratory project, I create synthethic population for countries of the world and compare the numbers generated to real distributions. The purpose is to evaluate the usefuleness of different methods for similar tasks. Aspects such as accuracy of the result and speed of execution are considered.

### Data used
World Bank country population 2019 (https://data.worldbank.org/indicator/SP.POP.TOTL)<br>
United National World Population Prospects (https://population.un.org/wpp/Download/Standard/CSV/)<br>

## Methods explored

### 1 - Walker Alias Method
This is a method developed in 1974, which allows to sample from frequency distributions using the idea of 'buckets' and 'liquids' being moved from bucket to bucket so that all of them can be filled and random selection can be done using two randomly generated numbers.
### 2 - Pseudorandom Number Generation
This methods allows to pick a random item from a list based on frequency distribution provided for the function. It benefits from the fact that it is implemented in Python and can therefore operate on NumPy arrays, giving it a potential advantage of speed.

## Conclusions
Both methods were capable of generating a realistic population totals given the frequency distributions. For both methods, I generated 1 million individuals and compared the frequency distributions of the synthetic population to the real population.<br><br>
However, the methods had different speeds of execution. Walker Alias Method took 0.3366 minutes to execute, while Pseudorandom Number Generation took 0.0256 minutes to execute and was therefore considerably faster.<br><br>
Furthermore, Pseudorandom Number Generation is already implemented as part of `random` package in Python and therefore is much easier to use - requiring one external library and just one line of code, while Walker Alias Methods implementation required 44 lines of code. Given that both methods produced similar results, I therefore conclude that the Pseudorandom Number Generation is more suitable for this task.
## Example
```Python
from random import choices
# given a list of values
countries = ['China', 'India', 'United States', 'Indonesia', 'Pakistan', 'Other']
# and their distribution frequencies
# the frequencies should add up to 1
frequencies = [0.182557, 0.178469, 0.042872, 0.035347, 0.028286, 0.532469]
# generate 1000 random individuals based on the above data
result = choices(countries, frequencies, k=1000)
# display the resulting distributions
from collections import Counter
print(f'Generated frequencies: {Counter(result)}')
```
```
Generated frequencies: Counter({'Other': 524, 'China': 189, 'India': 179, 'Indonesia': 46, 'United States': 35, 'Pakistan': 27})
```
