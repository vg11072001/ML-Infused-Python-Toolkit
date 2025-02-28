


## Pandas And Numpy comparisons for speed


- For loop 
- ![](Pasted%20image%2020250228152038.png)

- For vectorization
- Operating on Array, or series level 
- ![](Pasted%20image%2020250228152215.png)

- **For optimization following techniques used:**
	1. Python for loop over rows:
		1. ![](Pasted%20image%2020250228152705.png)
	2. Looping with .iterrows()
	3. .apply() method
		1. ![](Pasted%20image%2020250228152721.png)
	4. pandas series vectorization
		1. ![](Pasted%20image%2020250228152740.png)
	5. Numpy array vectorization
		```python
		data = {
		    'A': [1, 2, 3, 4, 5],
		    'B': [10, 20, 30, 40, 50],
		    'C': [100, 200, 300, 400, 500]
		}
		df = pd.DataFrame(data)
		
		# Using NumPy vectorization to perform operations efficiently
		df['A_squared'] = np.square(df['A'])  # Square each element in column 'A'
		df['B_log'] = np.log(df['B'])         # Compute natural log of column 'B'
		df['C_normalized'] = (df['C'] - np.mean(df['C'])) / np.std(df['C'])  # Normalize column 'C'
		
		```

summary:
 ![](Pasted%20image%2020250228161352.png)

**if else condition on columns of dataframe:**

- ![](Pasted%20image%2020250228153857.png)
- on more solution
- ![](Pasted%20image%2020250228154051.png)

**if multiple conditons:**
- ![](Pasted%20image%2020250228154156.png)
- better is there
- numpy select if multiple conditons:
- ![](Pasted%20image%2020250228154230.png) orders is very important
- ![](Pasted%20image%2020250228154436.png) comparison


if nested condtions:
- ![](Pasted%20image%2020250228154630.png)
- ![](Pasted%20image%2020250228154649.png)



**compicated things : with strings, dictionaries, dates, and other rows**

- ![](Pasted%20image%2020250228154836.png)
- ![](Pasted%20image%2020250228155045.png)


dictionary loopup

- ![](Pasted%20image%2020250228155247.png)

dates:

1000 faster
- ![](Pasted%20image%2020250228155457.png)


- 11k faster
![](Pasted%20image%2020250228155713.png)

**extra more complicated!**

![](Pasted%20image%2020250228155749.png)


- ![](Pasted%20image%2020250228155936.png)

More techniques are:

- casting values on dataframes, to heir dtypes possible on columns
- like to category, int, like this:
- ![](Pasted%20image%2020250228160713.png)


References: 
- https://www.youtube.com/watch?v=CG3EV7UBELA
- https://www.youtube.com/@robmulla
- https://youtu.be/nxWginnBklU?si=PuKZeNPGeAThfupz
