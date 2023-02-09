
It is necessary to declare a decorator class named HandlerGET, which will simulate the processing of GET requests on the server side. To do this, the HandlerGET class itself needs to be designed so that it can be applied to any function as a decorator. For example:

@HandlerGET
def contact(request):
return "Sergey Balakirev"
Here request is an arbitrary dictionary with the data of the current request, for example, such as: {"method": "GET", "url": "contact.html "}. And the function should return a string.

Then, when calling the decorated function:

res = contact({"method": "GET", "url": "contact.html"})
a string in the format should be returned:

"GET: <data from function>"

In our example, it will be:

"GET: Sergey Balakirev"

If there is no method key in the request dictionary, then a GET request is assumed by default. If the method key takes a different value, for example, "POST", then the decorated contact function should return the value None.

To implement a simulated GET request in the HandlerGET class, declare an auxiliary method with the following signature:

def get(self, func, request, *args, **kwargs): ...
Here func is a reference to the function being decorated; request is a dictionary with the data passed when calling the decorated function. It is in this method that the returned string should be formed in the specified format:

"GET: Sergey Balakirev"

P.S. It is enough to declare only a class in the program. You don't need to display anything on the screen.
