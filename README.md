# FastAPI
نسبتا جدید هست 
به سرعتم داره پیشرفت میکنه برای ای پی ای هایی هست که سرعت میخوان بهتر از جنگو و فلسک هست 
پرفورمنس بیشتری داره 
ما توی فست ای پی ای سرور نداریم که استفاده کنیم 
برای اینکار میتونیم از UVICORN OR HYPERCORN استفاده کنیم نحوه نوشتنس مثل فلسک هست که یعنی اینو بدونیم اونم میدونیم
داکیومنتیشنش خودش داکیومنت ایجاد میکنه به صورت اتوماتیک
فست ای پی ای از تایپ هینت های پایتون استفاده میکنه 
# annotations and typings
انومیشینز برای این هست که کمک کنه به خوننده کد که چی باید وارد کنه (استرینک , اینت و...)
تایپینگ هم برای لیست ها و تاپل هاست که اینا رو بیاره 
```
def hello(name:str,lastname:str)-> str:
  return f"hello{name,lastname}"

OR
import typing as tp
def hello(names:tp.list["str"]):
  return 
```
اجباری نیست ولی اگه میخوای کاری بکنی که پایتون به اینها گیر بده باید از کتابخونه های mypy, pylint استفاده کنی 
فست ای پی ای داره از async io استفاده میکنه 
# app
برای فعال کردنش نیاز داریم به یوی کورن دستورشم به این صورته
```
Uvicorn file_name:app --reload
```
```
from fastapi import FastAPI
app = FastAPI()
def home():
  return "responser"
```
# parameters
ما کوئری پارامتر داریم و پث کوئری داریم
پث کوئری برای نمیاش یک منبع هست 
یک کوئری پارامتر برای تنظیماتی مثل فیلتر کردن براس سرچ و اینا میزارن
کوئری پارامتر ها با علامت سوال شروع میشن در اصل اینها برای نحوه نمایش اطلاعات هستن 
توی این تابع ها میتونیم از انونیتیشن ها استفاده کنیم برای صحت سنجی از تایپ های اونها 
اگه توی آپی که تعریف کردیم اون پارامتر خاص رو نزاریم و یکی پارامتر اضافه بزاریم داخل تابع میتونیم از کوئری پارامتر ها استفاده کنیم 
میتونیم برای این پارامتر ها مقدار دیفالت بزاریم 
# request body
این برای وقتی هست که پارامتر هاس ما خیلی زیاد هستن 
برای اینکه متغیر های زیادی رو خواستیم وارد کنیم از روش زیر استفاده میکنیم 
```
from fastapi import FastAPI
from pydantic import BaseModel


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None


app = FastAPI()


@app.post("/items/")
async def create_item(item: Item):
    return item

```

# query path 
برای محدودیت گذاشتن هست
با پای دانتیک میتونیم متغیر ها رو بنویسیم 
