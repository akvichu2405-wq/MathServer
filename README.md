# Ex.04 Design a Website for Server Side Processing
## Date:09/12/2025

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
```
math.html

<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>MILEAGE</title>
<title>Vishnu Priya A K (25018523)</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body
{
background-color:014D4E;
.edge {
width: 1440px;
margin-left: auto;
margin-right: auto;
padding-top: 250px;
padding-left: 300px;
}
.box {
display:block; 
width: 500px;
border: Thick dashed D44641;
min-height: 350px;
font-size: 20px;
background-color:D44641;
}
.formelt{
color:black;
text-align: center;
margin-top: 7px;
margin-bottom: 6px;
}
h1
{
color:014D4E;
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
 <h1>MILEAGE</h1>
<h4>        Vishnu Priya A K (25018523)</h4>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Distance : <input type="text" name="distance" value="{{d}}"></input>(in km)<br/>
</div>
<div class="formelt">
Fuel consumed : <input type="text" name="fuel consumed" value="{{f}}"></input>(in L)<br/>
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Mileage : <input type="text" name="mileage" value="{{mileage}}"></input>km/L<br/>
</div>
</form>
</div>
</div>
</body>
</html>


views.py

rom django.shortcuts import render
def mileage(request):
    context={}
    context['mileage'] = "0"
    context['d'] = "0"
    context['f'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        d= request.POST.get('distance','0')
        f = request.POST.get('fuel consumed','0')
        print('request=',request)
        print('distance=',d)
        print('fuel consumed=',f)
        mileage = int(d)/int(f)
        context['mileage'] = mileage
        context['d'] = d
        context['f'] = f
        print('Mileage=',mileage)
    return render(request,'mathapp/math.html',context)


urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('mileage/',views.mileage,name="mileage"),
    path('',views.mileage,name="mileage")
]
```


## OUTPUT - SERVER SIDE:
![alt text](<Screenshot 2025-12-09 204951.png>)

## OUTPUT - WEBPAGE:
![alt text](<Screenshot 2025-12-09 204814.png>)

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
