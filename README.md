# Ex.05 Design a Website for Server Side Processing
## Date:05.04.2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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

## PROGRAM :
```
math.html

<html>
<head>
<title>Surface Area Of Right Cylinder</title>
<style type="text/css">
body 
{
background-color:rgb(249, 0, 170);
}a
.edge {
width: 1440px;
margin-left: auto;
margin-right: auto;
padding-top: 1000px;
padding-left: 300px;
}
.box {
display:block;
border: ridge rgb(16, 247, 4);
width: 600px;
min-height: 400px;
font-size: 20px;
background-color:rgb(250, 237, 5);
}
.suren{
color:rgb(0, 255, 8);
text-align: center;
margin-top: 7px;
margin-bottom: 6px;
}
h1
{
color:rgb(5, 176, 249);
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge" align="center">
<div class="box">
<h1>Surface Area Of A Right Cylinder</h1>
<h2>M.suren 212223230222 </h2>
<br>
<br>
<form method="POST">
{% csrf_token %}
<div class="suren">
Radius : <input type="text" name="Radius" value="{{r}}"></input>(in m)<br/>
<br>
</div>
<div class="suren">
Height: <input type="text" name="Height" value="{{h}}"></input>(in m)<br/>
<br>
</div>
<div class="suren">
<input type="submit" value="Calculate"></input><br/>
<br>
</div>
<div class="suren">
Area : <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
</div>
</form>
</div>
</div>
</body>
</html>

views.py

from django.shortcuts import render
def surfacearea(request):
    context={}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        r = request.POST.get('Radius','0')
        h = request.POST.get('Height','0')
        print('request=',request)
        print('Radius=',r)
        print('Height=',h)
        area = (2*3.14*int(r)*int(h)+(2*3.14*int(r)*int(r)))
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area=',area)
    return render(request,'mathapp/math.html',context)


urls.py

    from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfacearearoot")
]
```


## SERVER SIDE PROCESSING:
![alt text](<Screenshot (11).png>)

## HOMEPAGE:
![alt text](<Screenshot (10).png>)

## RESULT:
The program for performing server side processing is completed successfully.
