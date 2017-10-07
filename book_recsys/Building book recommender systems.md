# Building book recommender systems

[TOC]

## 1. Data

-[Book-Crossings](http://www2.informatik.uni-freiburg.de/~cziegler/BX/) is a book ratings dataset compiled by Cai-Nicolas Ziegler. 

- it contains 1.1 millions ratings of 270,000 books by 90,000 users.

- the ratings are on a scale from 1 to 10.

- the data consists of three tables: ratings, books info, and users info.

  ```python
  import pandas as pd	
  import numpy as np
  import matplotlib.pyplot as plt
  ```

  ```python
  books = pd.read_csv('BX-Books.csv', sep=';', error_bad_lines=False, encoding="latin-1")
  books.columns = ['ISBN', 'bookTitle', 'bookAuthor', 'yearOfPublication', 'publisher', 'imageUrlS', 'imageUrlM', 'imageUrlL']
  ```

  With the command `pd.read_csv`, it has the option `error_bad_lines`, by default, this option is set to `True` (boolean type) which means that when lines with too many fields (i.e. a CSV line with too many commas, meaning it has too many columns when you opening CSV file in Microsoft Excel), it will cause an exception to be raised, and no returned DataFrame.

  If this options is set to `False`, then these "bad lines" will dropped from the DataFrame that is returned.

  When it is set to `False`, the program will output the following error line:

  > b'Skipping line 6452: expected 8 fields, saw 9\nSkipping line 43667: expected 8 fields, saw 10\nSkipping line 51751: expected 8 fields, saw 9\n'


```
This above error means that a line numbered 6452 has 9 columns (8 commas), which is wrong compared to 8 fields (7 commas) ('ISBN', 'bookTitle', 'bookAuthor', 'yearOfPublication', 'publisher', 'imageUrlS', 'imageUrlM', 'imageUrlL')
```

