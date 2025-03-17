# Imports
You have to install the following library in order to interact with API
```python
pip install requests
```

Best way to start is get the API URL from dedicated website and hard code into the script and run the following syntax with a debugger
```python
extractedAPIInfo = requests.get(API_URL)
# Note: Sometimes you have to specify that you want to export the json format
extractedAPIInfo = requests.get(API_URL).json()
```
When running with a debugger (especially in pyCharm) you can look at the data that is stored in the response packet. 
For this example, I now know the contents of the API response and can then extract the information of particular interest. 
![[Pasted image 20250316235407.png]]
In order to extract particular signals we can use the following syntax
```python
latitude = geoData.get("lat")
```
Through this view, we can see how the field of this *dict* data type format are named.

All the outputs are normally in string format