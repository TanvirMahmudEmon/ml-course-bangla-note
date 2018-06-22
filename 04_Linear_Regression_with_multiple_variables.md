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
    - একটি এক্সাম্পলের জন্য ইনপুট ভেক্টর (অর্থাৎ চারটি প্যারামিটারের একটি ভেক্টর i তম ইনপুট এক্সাম্পলের জন্য)
    - ট্রেনিং সেটের একটি ইনডেক্স হল i 
    - তাই 
      - x হল n ডাইমেনশনের (n-dimensional) একটি ফিচার ভেক্টর 
      - যেমনঃ ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x%5E%7B3%7D) তৃতীয় হাউস, এবং এতে ঐ হাউস সম্পর্কিত চারটি ফিচার আছে 
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x_%7Bj%7D%5E%7Bi%7D) 
    - i তম ট্রেনিং এক্সাম্পলে ফিচার j এর মান 
    - তাই 
      - যেমনঃ ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x_%7Bj%7D%5E%7Bi%7D), তৃতীয় হাউসের বেডরুমের সংখ্যা (number of bedrooms)
- এখন আমাদের কাছে একাধিক ফিচার আছে 
  - আমাদের হাইপোথিসিসটি দেখতে কেমন হবে ?
  - আগে আমাদের হাইপোথিসিসটি ছিল এমন 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29%20%3D%20%5CTheta%20_%7B0%7D&plus;%5CTheta%20_%7B1%7Dx)
      - এখানে দুটি প্যারামিটার আছে (theta 1 এবং theta 2) যা কিনা কস্ট ফাংশন (cost function) দ্বারা নির্ণয় করা হয় 
      - একটি ভ্যারিয়েবল x 
  - এখন আমাদের কাছে একাধিক ফিচার আছে 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29%20%3D%20%5CTheta%20_%7B0%7D&plus;%5CTheta%20_%7B1%7Dx_%7B1%7D&plus;%5CTheta%20_%7B2%7Dx_%7B2%7D&plus;%5CTheta%20_%7B3%7Dx_%7B3%7D&plus;%5CTheta%20_%7B4%7Dx_%7B4%7D)
  - যেমনঃ 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29%20%3D%2080&plus;0.1x_%7B1%7D&plus;0.01x_%7B2%7D&plus;3x_%7B3%7D-2x_%7B4%7D) 
      - হাইপোথিসিসের একটি উদহারণ যার মাধ্যমে হাউসের প্রাইস প্রেডিক্ট করার চেষ্টা করা হচ্ছে 
      - এখনো প্যারামিটারগুলো কস্ট ফাংশন দিয়েই নির্ণয় করা হবে 
  - নোটেশনের সুবিধার জন্য ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x_%7B0%7D%3D%201)
    - প্রত্যকেটি এক্সাম্পল i এর জন্য একটি করে অতিরিক্ত o তম ফিচার আছে 
    - তাই এখন আমাদের **ফিচার ভেক্টর** n + 1 ডিমেনশনের ফিচার ভেক্টর যার ইনডেক্স শুরু ০ থেকে 
      - এটি একটি কলাম ভেক্টর যার নাম x 
      - প্রত্যকেটি এক্সাম্পলের সাথে সংযুক্ত একটি কলাম ভেক্টর আছে 
      - ধরি, আমাদের একটি নতুন এক্সাম্পল আছে যার নাম "X"
    - **প্যারামিটারগুলোও** n + 1 ডিমেনশনের ভেক্টর যার ইনডেক্স শুরু ০ থেকে 
      - এটি একটি কলাম ভেক্টরও যার নাম θ
      - প্রত্যেকটি এক্সাম্পলের জন্য এই ভেক্টরটি একই (same)
  - এটি বিবেচনা করে, হাইপোথিসিস লেখা যায় এভাবে 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29%3D%5CTheta%20_%7B0%7Dx_%7B0%7D&plus;%5CTheta%20_%7B1%7Dx_%7B1%7D&plus;%5CTheta%20_%7B2%7Dx_%7B2%7D&plus;%5CTheta%20_%7B3%7Dx_%7B3%7D&plus;%5CTheta%20_%7B4%7Dx_%7B4%7D)
  - যদি আমরা এমন করি 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29%3D%5CTheta%20%5E%7BT%7DX)
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20%5E%7BT%7D) একটি [1 x n+1] ম্যাট্রিক্স 
      - অন্যভাবে বললে, যেহেতু θ একটি কলাম ভেক্টর, ট্রান্সপজিশন (transposition) অপারেশন এটিকে রো ভেক্টরে রূপান্তর করবে 
      - তাই আগে ছিল 
        - θ ছিল ম্যাট্রিক্স [n + 1 x 1]
      - এখন 
        - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20%5E%7BT%7D) হল ম্যাট্রিক্স [1 x n+1] 
      - এর মানে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20%5E%7BT%7D) এবং X এর ভিতরের ডিমেনশনে মিল আছে, সুতরাং তাদেরকে একসাথে গুন করা যেতে পারে এভাবে   
        - [1 x n+1] * [n+1 x 1] 
        - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%3Dh_%7B%5CTheta%7D%28x%29)
        - অন্যভাবে বললে, আমাদের প্যারামিটার ভেক্টরের ট্রান্সপোজ * একটি ইনপুট এক্সাম্পল X আমাদেরকে একটি প্রেডিক্টেড হাইপোথিসিস দিচ্ছে যেটি [1 x 1] ডিমেনশনের (অর্থাৎ একটি সিঙ্গেল মান)
    - এই ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x_%7B0%7D%3D1) থেকে এটি আমরা এভাবে লিখতে পারি 
  - এটি হল মাল্টিভেরিইয়েট লিনিয়ার রিগ্রেশনের (multivariate linear regression) উদাহরণ 
  ### একাধিক ভ্যারিয়েবলের জন্য গ্রেডিয়েন্ট ডিসেন্ট (Gradient descent for multiple variables)
- গ্রেডিয়েন্ট ডিসেন্ট দিয়ে হাইপোথিসিসের জন্য প্যারামিটারগুলো ফিট (fit) করা 
  - প্যারামিটারগুলো হল ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) থেকে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bn%7D)
  - এই প্যারামিটারগুলোকে n সংখ্যক আলাদা আলাদা মান হিসাবে চিন্তা না করে একটি সিঙ্গেল ভেক্টর হিসাবে (θ) চিন্তা করুন 
    - যেখানে θ হল n+1 ডিমেনশনাল (dimensional)
- আমাদের কস্ট ফাংশন হল 

![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image.png)

- একইভাবে, J কে n+1 নাম্বারের একটি ফাংশন হিসাবে চিন্তা না করে শুধুমাত্র প্যারামিটার ভেক্টরের একটি ফাংশন J() হিসাবে চিন্তা করুন 
  - J(θ)

- গ্রেডিয়েন্ট ডিসেন্ট ![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image%20[1].png)

