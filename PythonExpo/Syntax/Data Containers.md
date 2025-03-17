Quick overview of the different ways data can be stored in python
- list
- dict
- tuple
- namedduple
- dataclass
## List
Stores a number of items of the same type. It is good if you attempt to run through the whole data set as looking for individual values is very slow (like string matching)
```python
cities = ["New York", "London", "Tokyo"]
print(cities[0])  # Access by index
```
Very easy to append more information to the list.

The data in the list is very much assorted which makes looking for specific data difficult

## Dictionaries
Very useful for object oriented design. You can create the same structure of variables associated with the object and then populate them. Very fast access.
```python
city = {
    "name": "New York",
    "population": 8_336_817,
    "country": "USA"
}
print(city["name"])  # Access by key
```
Each of the left hand side elements are called 'keys' which you use to extract information out of a *dict*


## Tuple
A list of data that is locked after instantiation (cannot be changed once created)
Very similar to lists but note the paranthesis () rather than [] on initiation:
```python
coordinates = (40.7128, -74.0060)  # (latitude, longitude)
print(coordinates[0])  # Access by index
```
It's not a named structure so when accessing it, you need to know that latitude is under index 0


## Named Tuple
Similar concept of modification i.e cannot be changed after creation. The difference is that the components are named
```python
from collections import namedtuple

City = namedtuple("City", ["name", "population", "country"])
nyc = City("New York", 8_336_817, "USA")

print(nyc.name, nyc.population)  # Access by attribute
```
We create the template of the namedtuple (just like  a struct/class) and then we instantiate by populating the predetermined data fields


## Data Class
Good for structured objects with default values. Similar concept to Named Tuples where you end up having predetermined fields for objects.
The difference to the Tuples is that you can edit it post creation

```python
from dataclasses import dataclass

@dataclass
class City:
    name: str = "unknown" # default string
    population: int = 0 # default value
    country: str 

nyc = City("New York", 8_336_817, "USA")
nyc.population = 9_000_000  # Allowed (mutable)

print(nyc.name, nyc.population)
```