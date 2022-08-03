# pygeocode

### a dead simple function to geocode an address to latitude and longitude

pyGLocate is a python interface for google maps geocode API from GCP.
Its use implies you have an active project in GCP and the ability to activate the necessary API.

It should be noted that the use of this API requires the api is active on your GCP account 
and is not free (although it is very cheap) $0.005 per request upto 100,000 requets. As of writing this Google Maps still offers a $200 monthly credit for maps services including geocoding which is roughly 40,000 requests/month free.

You can view how to setup the geocode API in Google Cloud [here](https://developers.google.com/maps/documentation/geocoding/cloud-setup).

To use the `geocode` function paste your API Key into the API_KEY variable 

Example with multi address:
```python

from pygeocode import geocode

multi_address = ["1600 Amphitheatre Pkwy, Mountain View, CA 94043", 
                "1 Hacker Way, Menlo Park, CA 94025", 
                "1 Apple Park Way Cupertino, California, 95014"]
        
ma = geocode(multi_address)

print("multiple addresses:")
print(ma)

```
Output: 

```python

multiple addresses:
[{'lat': 37.4223878, 'lng': -122.0841877}, {'lat': 37.4844547, 'lng': -122.1478049}, {'lat': 37.3293877, 'lng': -122.0084115}]

```
Example with single address:

```python

single_address = geocode(["1600 Amphitheatre Pkwy, Mountain View, CA 94043"])
print("single address:")
print(single_address)

```
Output:

```python

single address:
{'lat': 37.4223878, 'lng': -122.0841877}

```

**Note:**

currently google rate limits requests to 50 per second with no daily max. There is no rate limiting in this function so large requests need to be limited in the specific implimentation.

