http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables.html
# একাধিক ফিচার নিয়ে লিনিয়ার রিগ্রেশন (Linear regression with multiple features)
একাধিক ফিচার নিয়ে লিনিয়ার রিগ্রেশনের নতুন ভার্সন 
- একাধিক ভ্যারিয়েবল = একাধিক ফিচার 
- মূল ভার্সনে ছিল 
  - X = house size, প্রেডিক্ট করার জন্য এটি ব্যবহার করা হত 
  - Y = house price
- যদি নতুন করে আমাদের আরো কিছু ভ্যারিয়েবল থাকে (যেমনঃ number of bedrooms, number floors, age of the home)
  - চারটি ফিচার হচ্ছে x1, x2, x3, x4
    - x1 - size (feet squared)
    - x2 - Number of bedrooms
    - x3 - Number of floors
    - x4 - Age of home (years)
  - Y হচ্ছে আউটপুট ভ্যারিয়েবল (price)
- আরো কিছু নোটেশন 
  - **n**
    - ফিচার সংখ্যা (n = 4)
  - **m**
    - এক্সাম্পল সংখ্যা (অর্থাৎ একটি টেবিলে যতগুলো সারি-row আছে)
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x%5E%7Bi%7D)
    - একটি এক্সাম্পলের জন্য ইনপুট ভেক্টর (কাজেই চারটি প্যারামিটারের ) 
