# Lesson: Querying APIs in Python

### Lesson Objectives:
* Students will be able to understand and explain what an API is. 
* Students will be able to import the necessary tools needed to interact with an API.
* Students will be able to access and print data from an API.

### Prior Knowledge: 
Before this lesson, students should know how to create and use variables, print statements and create a function in Python. 

### Introduction: What is an API?
Have you ever had a disagreement with a friend or family member? Oftentimes it feels as if you and the other person are speaking a different language. In order to come to a resolution, it might be beneficial to ask someone to mediate the conversations. That's exactly what an API is!

You can think of an API as a mediator between two different entitites. An API helps us access information from a system, service or website. The **user** puts in a **request** to the API for data. The API then gets the data from the system, service or website and brings it back to the user as a **response**. 

### Part 1: Accessing an API
If we envision an API as a mediator of a disagreement between two people, we must also consider how we should communicate with it. Not many arguments are won with yelling and screaming! A calm and reasonable tone is required for a resolution. In the same way, there are specific tools we need to use in order to communicate with an API. 

To begin, we have to install the requests module which allows the user to send HTTP requests using Python. Since we will be using a web API in this lesson, this is the perfect module to use. The initial API we will use is a random advice API "https://api.adviceslip.com/advice"

 `import requests`

Once we've imported the requests module we need to access our web API by using the **GET** request. Create a variable in which to store the address of our random advice API. 

`advice = requests.get("https://api.adviceslip.com/advice")`

When a request is made, a response code is given which lets us know if our request was successful or not. We've seen these response codes before in the form of 404 (Not Found). A full list of response codes can be found via this w3schools link "https://www.w3schools.com/tags/ref_httpmessages.asp" . The code that we wish to see is 200 which means that we were successful in our request. It's helpful to print the status code and its meaning using the following print statements. 

`print(advice.status_code)`

`print(advice.reason)`

The console should print `200` and `ok` which means we can continue to make requests! It is also helpful to know the format the data we are requesting. Are we accessing images, gifs or text? We can use the following code to check:
`print(advice.headers.get("Content-Type"))`

### Part 2: Querying an API

Now that we are confident we can access the API's data, it's now time to query (request data) from the random advice API. Use a print statement to print the data from this random advice API. * Teacher Note: Allow students to run the program multiple times to generate random advice.*

`print(advice.text)`

This web API prints one peice of random advice. At first glance the output may look like words and symbols strung together but since there isn't much text printed, we can read it with some ease. 

Let's take a look at a different web API with a bit more information. The International Space Station API contains data on how many people are currently in space: "http://api.open-notify.org/astros.json". Follow all instructions in part 1 to access this ISS API and then use the `.text` method to print the data from this API.

`iss = requests.get("http://api.open-notify.org/astros.json")`

`print(iss.text)`

The console shpould show that there are a **lot** more words and symols. Since the data is in a text format, we could attempt to read it but it would resemble reading an essay without line spacing, indentation or paragraphs. We would likely get a headache while trying to decipher all of the words! We need to **format** the data in order to read through it with ease.

### Part 3: JSON 
json (javascript object notation) is a text format that stores and formats data in a way that is easily understandable.  In order to use json, we must first import it.

`import json`

Once json is imported, create a function that uses json to format the data. More information on formating data with json can be found a this w3schools link "https://www.w3schools.com/python/python_json.asp" . 

The function we create should take in a variable:
`def buzz(lightyear):` 
The code above shows a function named "buzz" that takes in a variable named "lightyear". 

Create a variable "get_data" and set it equal to "json.dumps()". This json.dumps() method converts Python objects into a json string(words). This method is important because it contains parameters that make it easier to read data. 

`get_data = json.dumps(lightyear, sort_keys=True, indent=1)`

`print(get_data)`

The sort_keys parameter allows the user to sort the keys from the API dictionary and the indent parameter allows the user to indent the data.  

`def buzz(lightyear):
  get_data = json.dumps(lightyear, sort_keys=True, indent=1)
  print(get_data)
 buzz(iss.json())`

We can now easliy read how many people are on the International Space Station, their names and what craft they're on. 
