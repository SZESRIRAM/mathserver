# Ex.05 Design a Website for Server Side Processing
# Date:
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
views.py
```
from django.shortcuts import render
def power(request):
    result = None
    a={}
    a['resutlt']='0'
    a['I']='0'
    a['R']='0'
    if request.method == "POST":
        I = float(request.POST.get("current"))
        R = float(request.POST.get("resistance"))
        result = (I ** 2) * R
        print("Current",I)
        print("Resistance",R)
        print("Power",result)
        a['result']=result
        a['I']=I
        a['R']=R
    return render(request,"mathapp/math.html",a)
```
urls.py
```
 from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('Power/',views.power,name='Power'),
    path('',views.power,name='Powerroot'),
]
```
math.html
```
<!DOCTYPE html>
<html>
<head>
    <title>Power Calculation</title>
</head>
<body>

    <h2>P = I²R Calculation</h2>

    <form method="POST">
        {% csrf_token %}

        <label>Current (I):</label><br>
        <input type="numer" name="current" value="{{I}}" required>
        <label>Resistance (R):</label><br>
        <input type="numer" name="resistance" value="{{R}}" required>
        <button type="submit">Calculate</button>
    </form>
{% if result is not None%}
    <h3>Power = {{ result }}</h3>
{% endif %}
</body>
</html>
```
# SERVER SIDE PROCESSING:
<img width="940" height="318" alt="image" src="https://github.com/user-attachments/assets/366f6886-9c75-4114-a0b2-9996f7324724" />

# HOMEPAGE:
<img width="1913" height="618" alt="image" src="https://github.com/user-attachments/assets/e3bdb06f-b8f5-4275-8b32-90c52006d3eb" />

# RESULT:
The program for performing server side processing is completed successfully.
