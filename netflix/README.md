# Netflix Prize dataset
Due to this dataset's big size it cannot be uploaded, here's the instructions how to get the dataset.

1) Download from [Kaggle](https://www.kaggle.com/netflix-inc/netflix-prize-data)
2) Unzip the files to this **netflix** folder
3) Run this code to combine all the files into one:
```python
# opening the netflix data files and combining them into one
if not os.path.isfile("netflix_ratings.csv"): 
    data = open("netflix_ratings.csv", mode = "w")
    files = ['netflix/combined_data_1.txt', 'netflix/combined_data_2.txt', 
             'netflix/combined_data_3.txt', 'netflix/combined_data_4.txt']
    for file in files:
        print("Reading from file: "+str(file)+"...")
        with open(file) as f:  
            for line in f:
                line = line.strip() 
                if line.endswith(":"):
                    movieID = line.replace(":", "")
                else:
                    row = [] 
                    row = [x for x in line.split(",")] 
                    row.insert(0, movieID)
                    data.write(",".join(row))
                    data.write("\n")
    data.close()
```
