http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr.html

## লিনিয়ার রিগ্রেশন 

- হাউস প্রাইস ডাটার উদাহরণ আগে দেখানো হয়েছে 
  - লিনিয়ার রিগ্রেশন একটা সুপারভাইসড লার্নিং (Supervised Learning) প্রবলেম 
- আমরা শুরু করব কি দিয়ে ?
  - ট্রেনিং ডাটা সেট (আপনার কাছে যে ডাটা সেট টা আছে)
  - এই পুরো কোর্সে যে নোটেশন গুলো ব্যবহার করা হয়েছে
    - m = **ট্রেনিং এক্সাম্পল এর সংখ্যা** 
    - x = ইনপুট ভ্যারিয়েবল বা ফিচার 
    - y = আউটপুট ভ্যারিয়েবল বা টার্গেট ভ্যারিয়েবল 
      - (x,y) = যে কোন ১টা ট্রেনিং এক্সাম্পল 
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%28x%5E%7Bi%7D%2Cy%5E%7Bj%7D%29) = ১টা সুনির্দিষ্ট ট্রেনিং এক্সাম্পল (i তম ট্রেনিং এক্সাম্পল)
        - i দিয়ে ট্রেনিং সেট এর ১টি ইনডেক্স বুঝানো হচ্ছে 
![house_price.png](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[6].png)
- আমাদের ট্রেনিং সেট দেয়া আছে, এখন আমরা এটাকে কিভাবে ব্যবহার করব ?
  - ট্রেনিং সেটটা নিতে হবে 
  - একটা লার্নিং এলগোরিদমে ফেলতে হবে 
  - এলগোরিদমের আউটপুটে ১টি ফাংশন পাওয়া যাবে (যাকে প্রকাশ করা হয় h দিয়ে, h = **হাইপোথিসিস**)
    - এই ফাংশনটি ১টি ইনপুট গ্রহণ করে (যেমন: নতুন হাউসের সাইজ (Size) ইনপুট নিতে পারে)
    - এই ফাংশনটি আউটপুট হিসাবে Y এর (যথাসম্ভব কাছাকাছি) মান বের করে দেয়ার চেষ্টা করে
- হাইপোথিসিস h কে আমরা কিভাবে লিখতে পারি ?
  - h কে এভাবে লেখা যায়:
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%20%7D%28x%29%3D%5CTheta%20_%7B0%7D&plus;%5CTheta%20_%7B1%7Dx)
    - h(x) (সংক্ষেপে লিখলে)

![hypothesis equation](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[7].png)
- এর মানে কি বুঝাচ্ছে ?
  - x এর একটি লিনিয়ার ফাংশন হল Y  
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bi%7D) হল **প্যারামিটার** 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) হল জিরো হবার শর্ত (Zero condition)
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) হল গ্রাডিয়েন্ট 
- এই ধরণের ফাংশনকেই বলে ওয়ান ভ্যারিয়েবল(one variable) লিনিয়ার রিগ্রেশন 
  - একে  univariate linear regression ও বলা হয়ে থাকে 
- তাহলে সংক্ষেপে বললে
  - একটি হাইপোথিসিস কিছু ভ্যারিয়েবল গ্রহণ করে 
  - লার্নিং সিস্টেম যেসব প্যারামিটারের কথা বলে দেয় সেসব ব্যবহার করে 
  - ইনপুটের ভিত্তিতে আউটপুটে একটি প্রেডিকশন (prediction) দেয় 

### লিনিয়ার রিগ্রেশনের প্রয়োগ (কস্ট ফাংশন-cost function) 
- আমাদের ডাটায় কিভাবে সোজা লাইনটা (straight line) সঠিকভাবে বসবে কস্ট ফাংশন (cost function) সেটা বের করতে সাহায্য করে 
-  ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bi%7D) (parameters) এর জন্য মান বাছাই করা 
  - একেক মান থেকে একেক ফাংশন পাওয়া যায় 
  - যদি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D%20%3D%201.5) এবং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%200) হয় তবে আমরা X অক্ষের সাথে সমান্তরাল (parallel) একটি সোজা লাইন পাব যা (Y অক্ষে 1.5)
  - আর যদি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3E%200) হয় তবে একটি পজেটিভ ঢাল (slope) পাব 
- আমাদের ট্রেনিং সেটের ভিত্তিতে আমরা প্যারামিটার বের করতে চাচ্ছি যা কিনা সোজা লাইনটা (straight line) তৈরী করবে 
  - প্যারামিটারগুলোকে এমনভাবে বাছাই করছি যেন ট্রেনিং এক্সাম্পলের জন্য ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29) y এর কাছাকাছি থাকে 
    - আসলে ট্রেনিং সেটে x কে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29) সাথে ব্যবহার করা হচ্ছে যথাসম্ভব y এর মানের কাছাকাছি আউটপুট বের করে দেয়ার জন্য 
  - ধরে নিন ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29),  y কে নকল করছে ("y imitator") - x কে y তে কনভার্ট করার চেষ্টা করছে, এবং ধরে নিচ্ছে আমাদের কাছে y আছে তাই আমরা যাচাই করে দেখতে পারছি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%7D%28x%29) এই কাজটি ঠিক ভাবে করতে পারছে কিনা (অর্থাৎ y তে কনভার্ট করার কাজটি)
- বিষয়টা আরেকটু গুছিয়ে বললে:
  - আমরা একটা মিনিমাইজেশন প্রব্লেম (minimization problem) সমাধান করতে চাই 
  - মিনিমাইজ করব ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%28h_%7B%5CTheta%7D%28x%29%20-%20y%29%5E%7B2%7D) 
    - প্রত্যেকটা ট্রেনিং এক্সাম্পলের জন্য h(x) এবং y এর পার্থক্যকে কমাতে (minimize) হবে 
  - তারপর সাম (Sum) করতে হবে পুরো ট্রেনিং সেটের জন্য 
  
![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[8].png)  
- প্রেডিক্টেড হাউস প্রাইস ও আসল হাউস প্রাইসের বর্গের পার্থক্যকে (squared difference) মিনিমাইজ করা 
  - 1/2m
    - 1/m - এর মানে আমরা গড় (average) হিসাব করছি 
    - 1/2m - 2 গাণিতিক হিসাবকে আরেকটু সহজ করে দিচ্ছে, এর কারণে আমরা যে মান বের করছি সেই মানের কোন পরিবর্তন হচ্ছে না (অর্থাৎ ক্ষুদ্রতম মানকে 2 দ্বারা ভাগ করে অর্ধেক করলেও সেটা ক্ষুদ্রতমই থাকে!)
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D/%5CTheta%20_%7B1%7D) কে মিনিমাইজ করা মানে আমরা ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এর এমন মান পাচ্ছি যা খুঁজে বের করছে গড়ে y থেকে x এর সর্বনিম্ন বিচ্যুতি (minimal deviation) কত যখন আমরা ঐ প্যারামিটারগুলো আমাদের হাইপোথিসিস ফাংশনে ব্যবহার করছি 
- আরেকটু ভেঙে বললে বলা যায়, এটা একটা কস্ট ফাংশন (cost function)

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[9].png)
- এবং আমরা এই কস্ট ফাংশনকে (cost function) মিনিমাইজ করতে চাই 
  - সামেশন (summation) থাকার কারণে কস্ট ফাংশন (cost function) স্বাভাবিকভাবে সবসময় ট্রেনিং সেটের সব ডাটা নিয়েই কাজ করবে 
- **আবার একটু বলি** 
  - **হাইপোথিসিস** - প্রেডিকশন মেশিনের মত, মেশিনে x দিলে y এর আনুমানিক মান পাওয়া যায় 

  ![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[10].png)
  
  - **কস্ট (Cost)** - এমন একটা উপায় যেখানে ট্রেনিং ডাটাকে ব্যবহার করে θ র মান নির্ণয় করা হচ্ছে যাতে হাইপোথিসিসটি যথাসম্ভব সঠিক হয় 
  
  ![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[11].png)

    - এই কস্ট ফাংশনকে (cost function) স্কয়ার্ড এরর কস্ট ফাংশনও (squared error cost function) বলা হয় 
      - এই কস্ট ফাংশন (cost function) অধিকাংশ রিগ্রেশন ফাংশনের জন্যই মোটামোটি কার্যকর  
      - সম্ভবত সবচেয়ে বহুল ব্যবহৃত ফাংশন 
  - যদি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5Ctheta%20_%7B0%7D%2C%5Ctheta%20_%7B1%7D%29) বুঝতে সমস্যা হয়, ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5Ctheta%20_%7B0%7D%2C%5Ctheta%20_%7B1%7D%29) কি করছে, কেন করছে, কিভাবে আমরা এটি ব্যবহার করছি তা নিয়ে আলোচনা আসছে 
  
**কস্ট ফাংশন (Cost function) - আরেকটু গভীরভাবে দেখলে**
- চলুন কস্ট ফাংশন নিয়ে কিছু ইনটুইশন (intuition) বিবেচনা করি এবং কেন এটি আমরা ব্যবহার করতে চাই 
  - কস্ট ফাংশন প্যারামিটার নির্ণয় করে 
  - আপনার হাইপোথিসিস কেমন আচরণ করবে প্যারামিটারের সাথে যুক্ত মান এটি নির্ণয় করে, বিভিন্ন মান থেকে বিভিন্ন কিছু তৈরী হয় 
- সহজ সরল হাইপোথিসিস 
  - ধরি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D%20%3D%200)

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[12].png)

- কস্ট ফাংশন এবং এর লক্ষ্য অনেকটা আমাদের কাছে খুব সিম্পল প্যারামিটার সহকারে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) থাকার মত 
  - হাইপোথিসিস সিম্পল হলে কস্ট ফাংশন J() কে সহজে ভিজুয়ালাইজ (visualizing) করা যায় 
- তাই হাইপোথিসিস 0,0 দিয়ে অতিক্রম করছে 
- দুটি মূল ফাংশনকে আমরা বুঝতে চাচ্ছি
http://latex.codecogs.com/eqneditor/editor.php
