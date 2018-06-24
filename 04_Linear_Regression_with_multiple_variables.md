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
  - এই প্যারামিটারগুলোকে n সংখ্যক আলাদা আলাদা মান হিসাবে চিন্তা না করে একটি সিঙ্গেল ভেক্টর (θ) হিসাবে চিন্তা করুন 
    - যেখানে θ হল n+1 ডিমেনশনাল (dimensional)
- আমাদের কস্ট ফাংশন হল 

![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image.png)

- একইভাবে, J কে n+1 নাম্বারের একটি ফাংশন হিসাবে চিন্তা না করে শুধুমাত্র প্যারামিটার ভেক্টরের একটি ফাংশন J() হিসাবে চিন্তা করুন 
  - J(θ)

- গ্রেডিয়েন্ট ডিসেন্ট ![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image%20[1].png)

- আরো একবার এটি 
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bj%7D%20%3D%20%5CTheta%20_%7Bj%7D%20-) লার্নিং রেট (α) গুণন ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7BJ%7D%20%28...%29) এর সাপেক্ষে J(θ) এর পার্শিয়াল ডেরিভেটিভ 
  - প্রত্যকেটি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bj%7D) এর মান **যুগপৎ ভাবে আপডেট (simultaneous update)** করে আমরা এটি করব 
- এই এলগোরিদমের বাস্তবায়ন করি 
  - যখন n = 1

![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image%20[2].png)

- উপরে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) ও ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) কে আপডেট করার ক্ষেত্রে সামান্য পার্থক্য দেখা যাচ্ছে 
  - আসলে দুটি একই, ব্যতিক্রম হচ্ছে শেষেদিকে পূর্বে অনির্ণীত (previously undefined) একটি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x_%7B0%7D%5E%7B%28i%29%7D) আছে 1 হিসাবে , তাই দেখানো হয়নি 
- মাল্টিভেরিইয়েট গ্রেডিয়েন্ট ডিসেন্টের জন্য এখন আমাদের কাছে প্রায় হুবহু অনুরূপ রুল (rule) বা নিয়ম আছে   

![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image%20[3].png)

- এখানে কি কাজ হচ্ছে ?
  - প্রতিটি j (0 থেকে n পর্যন্ত) এর জন্য যুগপৎ আপডেট (যেমনঃ যখন n = 1) হিসাবে আমরা এটি করছি 
  - তাই আমরা ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bj%7D) কে পুনরায় স্থাপন করছি 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bj%7D) বিয়োগ লার্নিং রেট (α) গুণন ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bj%7D) এর সাপেক্ষে θ ভেক্টর এর পার্শিয়াল ডেরিভেটিভ
    - ক্যালকুলাস ছাড়া বললে এর মানে দাঁড়ায় 
      - লার্নিং রেট 
      - গুণন 1/m (গাণিতিক হিসাব নিকাশকে সহজতর করে)
      - গুণন যোগফল 
        - ভ্যারিয়েবল ভেক্টর গ্রহণকারী হাইপোথিসিস, বিয়োগ মূল মান, গুণন ভ্যারিয়েবল ভেক্টরের j তম মান প্রত্যেক এক্সাম্পলের জন্য 
    - এটি মনে রাখা জরুরী  যে 
    
![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image%20[4].png)

- এই এলগোরিদমগুলো অনেকটা একইরকম 

### গ্রেডিয়েন্ট ডিসেন্টের ব্যবহার: ১ ফিচার স্কেলিং (Gradient Decent in practice: 1 Feature Scaling)
- এতক্ষন থিওরি দেখলাম, এখন আমরা কিছু ব্যবহারিক প্রয়োগ শিখব 
- ফিচার স্কেলিং 
  - যদি একাধিক ফিচার নিয়ে কোন সমস্যা হয় 
  - এটি নিশ্চিত করা উচিত যে ওই ফিচারগুলো একই স্কেলে আছে  
    - অর্থাৎ গ্রেডিয়েন্ট ডিসেন্ট আরো দ্রুত একই বিন্দুতে এসে মিলিত হবে (অর্থাৎ converge হবে)
  - যেমনঃ 
    - x1 = size (0 - 2000 feet)
    - x2 = number of bedrooms (1-5)
    - অর্থাৎ আমরা যদি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) বনাম ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B2%7D) কে প্লট করি এতে যে কন্ট্যুর (contour) তৈরী হয় বিশাল রেঞ্জের পার্থক্যের কারণে এটি খুব লম্বা ও চিকন আকৃতির হয়    

![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image%20[5].png)

- গ্রেডিয়েন্ট ডিসেন্টে ইনপুট 
  - কাজেই এই ইনপুটটিকে রিস্কেল (rescale) করা দরকার যাতে এটি আরো কার্যকর হয় ***
  - তাই, যদি x1 এবং x2 থেকে প্রতিটি মানকে সর্বোচ্চ মান দ্বারা ভাগ করা হয় প্রত্যেক ফিচারের জন্য 
  - কন্ট্যুর অনেকটা বৃত্তের মত হয়ে যায় (যখন 0 এবং 1 এর মধ্যে স্কেল করা হয়)
- হয়ত সবকিছুকে -1 থেকে +1 রেঞ্জে নিয়ে আসতে চাই (approximately)
  - বিশাল রেঞ্জগুলো বাদ দিতে চাই, একটি থেকে অপরটির মধ্যে ছোট রেঞ্জ অথবা অনেক ভিন্ন রেঞ্জ 
  - গ্রহণযোগ্য রেঞ্জের প্রচলিত নিয়ম হচ্ছে 
    - -3 থেকে +3 হলে সাধারণত খুব ভাল - এর চেয়ে বড় হলে খারাপ 
    - -1/3 থেকে +1/3 হলেও চলে - এর চেয়ে ছোট হলে খারাপ 
- মীন বা গড় দিয়ে নর্মালাইজেশন (mean normalization) করতে পারি 
  - একটি ফিচার ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20x_%7Bi%7D) নেই 
    - এটিকে প্রতিস্থাপন করি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%28x_%7Bi%7D-mean%29/max) দিয়ে 
    - তাই সবগুলো মানের প্রায় ০ এর কাছাকাছি গড় আছে ***

![](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables_files/Image%20[6].png)

- max এর পরিবর্তে স্ট্যান্ডার্ড ডেভিয়েশনও (standard deviation) ব্যবহার করা যায় 

### লার্নিং রেট α (Learning Rate α)
