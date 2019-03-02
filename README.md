~~~python
import pandas as pd
from math import sqrt

def load_data(file):
    data=pd.read_csv(file)
    return data

def get_rating(data, index):
    result=[]
    result=data[data["user_id"]==index]["rating"].values
    return result
    
def computer_distance(rating_index, rating_me):
    #x[1,1,0,1]
    #y[5,5,0,5]
    sum=0
    for i in range(0,4):
        sum=sum+(rating_index[i]-rating_me[i])*(rating_index[i]-rating_me[i])
        return sqrt(sum)
    
def get_distance_with_me(data,index):
    rating_index=[]
    rating_me=[]
    rating_index= get_rating(data,index)
    print(rating_index)
    rating_me=get_rating(data,4)
    rasult=computer_distance(rating_index,rating_me)
    return rasult
    
def find_min_distance(map):
    index=0
    distance=0
    min=99999
    for key,value in map.items():
        print("key: %s , vlalue:%s" %(key,value))
        if min>value:
            min=value
            index+key
            

```
distance=min
return index, distance
```

file="Q:\\ww.csv"
data=load_data(file)
print(data[data["user_id"]==1]["rating"].values)

map={}
for i in range(1,4):
    map[i]=get_distance_with_me(data,i)
    print(map[i])
    
index, distance=find_min_distance(map)
print("第%s个人最近 他的数值是%s" %(index,distance))
~~~
