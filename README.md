# Smart-Ai-Chatbot-Using-Python
Smart-Ai-Chatbot-Using-Python

Hi Thanks Viewing this project of mine .



Installation

Install from PyPI:

pip install chatbotAI

install from github:

git clone https://github.com/karanarya98/Smart-Ai-Chatbot-Using-Python.git
cd Chatbot
python setup.py install

Demo

>>> from chatbot import demo
>>> demo()
Hi, how are you?
> i'm fine
Nice to know that you are fine  
> quit
Thank you for talking with me.
>>> 

List of feature supported in bot template

    Memory
    Get matched group
    Recursion
    Condition
    Change Topic
    Interact with python function
    REST API integration
    Topic based group
    Learn
    To upper case
    To lower case
    Capitalize
    Previous

Memory
Set Memory

{ variable : value }

In think mode

{! variable : value }

Get Memory

{ variable }

Get matched group
Get Nth matched group of client pattern

%N

Example to get first matched

%1

Get Nth matched group of bots pattern

%!N

Example to get first matched

%!1

Recursion

Get response as if client said this new statement

{% chat statement %}

It will do a pattern match for statement
Condition

{% if condition %} do this first {% elif condition %} do this next {% else %} do otherwise {% endif %}

Change Topic

{% topic TopicName %}

Interact with python function

{% call functionName: value %}

REST API integration
In API.json file

{
   "APIName":{
       "auth" : {
           "url":"https://your_rest_api_url/login.json",
           "method":"POST",
           "data":{
               "user":"Your_Username",
               "password":"Your_Password"
           }
       },
       "MethodName" : {
           "url":"https://your_rest_api_url/GET_method_Example.json",
           "method":"GET",
           "params":{
               "key1":"value1",
               "key2":"value2",
               ...
           },
           "value_getter":[order in which data has to be picked from json response]
       },
       "MethodName1" : {
           "url":"https://your_rest_api_url/GET_method_Example.json",
           "method":"POST",
           "data":{
               "key1":"value1",
               "key2":"value2",
               ...
           },
           "value_getter":[order in which data has to be picked from json response]
       },
       "MethodName2" : {
           ...
       },
       ...
   },
   "APIName2":{
       ...
   },
   ...
}

If authentication is required only then auth method is needed.The data and params defined in pi.json file acts as defult values and all key value pair defined in template file overrides the default value.value_getter consistes of list of keys in order using which info from json will be collected.
In Template file

[ APIName:MethodName,Key1:value1 (,Key*:value*) ]

you can have any number of key value pair and all key value pair will override data or params depending on method, if method is POST then it overrides data and if method is GET then it overrides params.
Topic based group

{% group topicName %}
  {% block %}
      {% client %}client says {% endclient %}
      {% response %}response text{% endresponse %}
  {% endblock %}
  ...
{% endgroup %}

Learn

{% learn %}
  {% group topicName %}
    {% block %}
        {% client %}client says {% endclient %}
        {% response %}response text{% endresponse %}
    {% endblock %}
    ...
  {% endgroup %}
  ...
{% endlearn %}

To upper case

{% up string %}

To lower case

{% low string %}

Capitalize

{% cap string %}

Previous

{% block %}
    {% client %}client's statement pattern{% endclient %}
    {% prev %}previous bot's statement pattern{% endprev %}
    {% response %}response string{% endresponse %}
{% endblock %}
