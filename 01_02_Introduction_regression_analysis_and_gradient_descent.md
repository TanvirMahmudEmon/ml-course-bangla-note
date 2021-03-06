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
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%20%7D%28x%29) 
    - হাইপোথিসিস হচ্ছে x এর একটি ফাংশন - হাউসের সাইজ কত সেটির ফাংশন 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29) 
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এর প্যারামিটারের একটি ফাংশন 
    - উদাহরণস্বরূপ:
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%201)
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29%20%3D%200) 
    - প্লট
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) বনাম ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29)
      - ডাটা 
        - ১.
          - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%201)
          - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29%20%3D%200) 
        - ২.
          - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%200.5)     
          - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29%20%3D%20%5Csim0.58)
        - ৩.
          - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%200)
          - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29%20%3D%20%5Csim%202.3)
- কিছু মান নিয়ে আমরা যদি প্লট করি 
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29) বনাম ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) আমরা একটি পলিনমিয়াল-polynomial পাই (দেখতে একটি কোয়াডরেটিক- quadratic এর মত)

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[13].png)

- লার্নিং এলগোরিদম অপ্টিমাইজেশনের উদ্দেশ্য হল ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এর মান বের করা, যে মানটি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29) কে মিনিমাইজ করে 
  - তাই এখানে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%201) হল ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এর সবচেয়ে ভাল মান (উপরের চিত্রটি দেখুন)
### কস্ট ফাংশনে আরো গভীর দৃষ্টি দিলে - সহজ-সরল কস্ট ফাংশন (cost function)
- ধরে নিচ্ছি আপনি কন্ট্যুর প্লট (contour plots) বা কন্ট্যুর ফিগার (contour figures) সম্পর্কে জানেন 
  - আগের মত একই কস্ট ফাংশন, হাইপোথিসিস ব্যবহার করে এবং একই উদ্দেশ্যে 
  - আপনি যদি কন্ট্যুর প্লট (cotour plots) না বুঝে থাকেন তবে এই অংশটি বাদ দিয়ে গেলেও কোন সমস্যা হবে না 
- দুটি ভ্যারিয়েবল বিশিষ্ট আমাদের মূল কমপ্লেক্স হাইপোথিসিসটি (complex hyothesis) ব্যবহার করি 
  - তাহলে কস্ট ফাংশন হচ্ছে 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%29)
- উদাহরণ 
  - ধরি 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D%20%3D%2050)
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%200.06)
  - একটু আগে আমরা কস্ট ফাংশনকে প্লট করেছিলাম এইভাবে 
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) বনাম ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B1%7D%29)
  - এখন আমাদের দুটি প্যারামিটার আছে 
    - তাই প্লট একটু দুর্বোধ্য হয়ে গেছে 
    - 3D সারফেস প্লট (3D surface plot) তৈরী হচ্ছে যার এক্সিস বা অক্ষ 
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20X%20%3D%20%5CTheta%20_%7B1%7D)  
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20Z%20%3D%20%5CTheta%20_%7B0%7D)
      - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20Y%20%3D%20J%28%5CTheta_%7B0%7D%2C%5CTheta_%7B1%7D%29)

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[14].png)

- আমরা দেখতে পাচ্ছি (y) কস্ট ফাংশনের মান নির্দেশ করছে, তাই বের করি y এর মান কোথায় সর্বনিম্ন 

- সারফেস প্লটের (surface plot) পরিবর্তে আমরা কন্ট্যুর ফিগার/প্লট (contour figures/plots) ব্যবহার করতে পারি 
  - এলিপসগুলোর (ellipses) সেট বিভিন্ন রংয়ে 
  - প্রত্যেকটি রং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta_%7B0%7D%2C%5CTheta_%7B1%7D%29) এর একই মান, কিন্তু বিভিন্ন স্থানে প্লট করা হচ্ছে কারণ ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta_%7B1%7D) ও ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta_%7B0%7D) পরিবর্তন হচ্ছে 
  - ভাবুন একটি গোলাকার বাটি বা বোলের মত (bowl shape) ফাংশন স্ক্রীন (screen) থেকে  বের হয়ে আসছে তাহলে কেন্দ্রটি হবে এককেন্দ্রিকবিশিষ্ট অনেকগুলো বৃত্ত (concentric circles)

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[15].png)

- প্রত্যেকটি বিন্দু (উপরে ছবিতে লাল বিন্দুটির মত) ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B1%7D) এর জন্য এক জোড়া প্যারামিটারের মানকে উপস্থাপন করছে 
  - এখানে আমাদের উদাহরণে মানগুলোকে স্থাপন করছে 
    - ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B0%7D%20%3D%20%5Csim%20800) 
    - ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B1%7D%20%3D%20%5Csim%20-0.15)
  - ভালোভাবে ফিট হল না 
    - অর্থাৎ এই প্যারামিটারগুলো দিয়ে কন্ট্যুর প্লটে (contour plot) যে মান পাওয়া যাচ্ছে সেটি কেন্দ্র থেকে দূরে 
  - যদি 
    - ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B0%7D%20%3D%20%5Csim%20360)
    - ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B1%7D%20%3D%200)
    - এটা আরেকটু ভাল হাইপোথিসিস দিচ্ছে, তারপরেও খুব বেশি ভাল নয় - কন্ট্যুর প্লটের (contour plot) কেন্দ্রে নয় 
  - সবশেষে আমরা মিনিমামটি (minimum) পাচ্ছি, যা থেকে বেস্ট হাইপোথিসিসটি পাওয়া যায় 
- চোখে দেখে / হাত দিয়ে এই কাজ করা বিরক্তিকর 
  - ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B1%7D) এর মিনিমাম খোঁজার জন্য আসলে আমাদের একটি কার্যকর এলগোরিদম চাই 

### গ্রেডিয়েন্ট ডিসেন্ট এলগোরিদম (Gradient descent algorithm)
- কস্ট ফাংশন (cost function) J কে মিনিমাইজ করে 
- গ্রেডিয়েন্ট ডিসেন্ট 
  - মেশিন লার্নিংয়ের সর্বত্রই মিনিমাইজেশনের জন্য ব্যবহার করা হয় 
- সাধারণ J() ফাংশন দিয়ে শুরু করি 
- প্রবলেম হচ্ছে 
  - আমাদের কাছে আছে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%29)
  - আমরা বের করতে চাই min![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%29)
- আরো সাধারণ ফাংশনে গ্রেডিয়েন্ট ডিসেন্ট প্রয়োগ হয় 
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%2C%5CTheta%20_%7B2%7D....%5CTheta%20_%7Bn%7D%29)
  - min![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%2C%5CTheta%20_%7B2%7D....%5CTheta%20_%7Bn%7D%29)

**এটি কিভাবে কাজ করে ?**
- প্রথমেই কিছু অনুমান দিয়ে শুরু 
  - 0,0 থেকে শুরু (অথবা অন্য যেকোন মান থেকে)
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%29) কে কমানোর জন্য ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) কে পরিবর্তন করতে থাকি 
- প্রত্যেকবার যখন প্যারামিটার পরিবর্তন করছি, গ্রেডিয়েন্টকে বাছাই করছি যেটি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%29) কে যথাসম্ভব কমাচ্ছে 
- একই কাজ বারবার করি 
- লোকাল মিনিমামে একই বিন্দুতে এসে মিলিত (converge) না হওয়া পর্যন্ত এই কাজ করে যেতে হবে 
- মজার একটি বৈশিষ্ট্য আছে 
  - যেখান থেকে শুরু করছি সেখান থেকে নির্ধারণ করা যায় কোন মিনিমামে গিয়ে শেষ হবে 

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[16].png)

  - এখানে দেখা যাচ্ছে একটি ইনিশিয়ালাইজেশন পয়েন্ট (initialization point) থেকে একটি লোকাল মিনিমাম (local minimum) পাওয়া যাচ্ছে 
  - আরেকটি পয়েন্ট থেকে আরেকটি লোকাল মিনিমাম (local minimum) পাওয়া যাচ্ছে 

**আরো যথাযথ সংজ্ঞা(formal definition)**
- কনভারজেন্স (convergence) না হওয়া পর্যন্ত  

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[17].png)

- এগুগুলোর মানে কি বুঝাচ্ছে ?
  ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bj%7D) কে আপডেট করতে হবে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%28%5CTheta%20_%7Bj%7D%20-%20%5Calpha%29) সংখ্যক বার ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7Bj%7D) এর রেস্পেক্টে কস্ট ফাংশনের পার্শিয়াল ডেরিভেটিভ বের করে
- নোটেশন (Notation)
  - :=
    - এসাইনমেন্টকে নির্দেশ করছে (Denotes assignment)
    - নোট: a = b মানে ট্রুথ আসারশন (truth assertion)
  - α (alpha)
    - এটি একটি নাম্বার যাকে  বলে **লার্নিং রেট (learning rate)**
    - একটি স্টেপ কত বড় হবে সেটি নিয়ন্ত্রণ করে 
      - যদি α বড় হয় তবে গ্রেডিয়েন্ট ডিসেন্ট হবে এগ্রেসিভ (aggressive gradient descent)
      - যদি α ছোট হয় তবে ছোট স্টেপ নিবে 
- ডেরিভেটিভ টার্ম (Derivative term) 

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[18].png)

  - এটি নিয়ে এখন কথা বলব না, এটিকে পরে ডিরাইভ (derive) করব 
- গ্রেডিয়েন্ট ডিসেন্ট এলগোরিদম কিভাবে প্রয়োগ করা হবে তা নিয়ে একটি সুক্ষতা (subtly) রয়েছে 
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এটি করে দেখি 
  - যখন j = ০ এবং j = 1 এর মানে আমরা একই সাথে (simultaneously) উভয়কে আপডেট করছি 
  - এটি আমরা কিভাবে করছি ?
    - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এর ডান পাশের মান হিসাব করতে হবে 
      - কাজেই আমাদের একটি টেম্প ভ্যালু (temp value) লাগবে, সাময়িকভাবে মান রাখার জন্য 
    - তারপর ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) কে একই সাথে আপডেট করতে হবে 
    - নিচে এ নিয়ে চিত্র দেখানো হয়েছে 

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[19].png)

- যদি আপডেটের কাজটি একই সাথে না করেন তবে গ্রেডিয়েন্ট ডিসেন্ট হবে না, এবং অদ্ভুত আচরণ করবে 
  - তবে মনে হতে পারে যে ঠিকভাবেই কাজ করছে - তাই এটি মনে রাখা জরুরী 
**এলগোরিদম বুঝে নেই**
- গ্রেডিয়েন্ট ডিসেন্ট বুঝতে হলে আমরা একটি সহজ সরল ফাংশনে ফিরে যাব যেখানে আমরা একটি প্যারামিটারকে মিনিমাইজ করব 
যেন এলগোরিদমটিকে আরো ব্যাখ্যা করা যায় 
  - min ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7DJ%28%5CTheta%20_%7B1%7D%29) যেখানে ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) হচ্ছে বাস্তব সংখ্যা (real number)
- এলগোরিদমে দুটি গুরুত্বপূর্ণ টার্ম হল 
  - আলফা (Alpha)
  - ডেরিভেটিভ টার্ম (Derivative term)
- কিছু সুক্ষ পার্থক্য 
  - পার্শিয়াল ডেরিভেটিভ বনাম ডেরিভেটিভ (Partial derivative vs. derivative)
    - যখন আমাদের কাছে একাধিক ভ্যারিয়েবল থাকবে কিন্তু শুধুমাত্র একটি ভ্যারিয়েবলের সাপেক্ষে ডিরাইভ করব তখন পার্শিয়াল ডেরিভেটিভ ব্যবহার করব 
    - যখন সব ভ্যারিয়েবলের সাপেক্ষে ডিরাইভ করব তখন ডেরিভেটিভ ব্যবহার করব 
- ডেরিভেটিভ টার্ম 

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[20].png)

  - ডেরিভেটিভ থেকে 
    - বিন্দুটিতে tangent বা স্পর্শক নেই এবং লাইনের slope বা ঢালটি দেখি 
    - আর তাই মিনিমামের (down) দিকে যেতে থাকলে নেগেটিভ ডেরিভেটিভ তৈরী হবে, আলফা (alpha) সবসময় পজেটিভ, তাই ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20j%28%5CTheta%20_%7B1%7D%29) আরো ছোট মানে আপডেট হবে 
    - একইভাবে আমরা স্লোপকে (slope) উপরের দিকে নিচ্ছি ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20j%28%5CTheta%20_%7B1%7D%29) কে বড় করছি 
- আলফা টার্ম (α)
  - কি হবে যদি আলফা খুবই ছোট বা খুব বেশি বড় হয় 
  - খুবই ছোট 
    - বাচ্চাদের মত ছোট ছোট স্টেপ দিবে (baby steps)
    - সময় অনেক বেশি লাগবে 
  - খুব বেশি বড়
    - মিনিমাম থেকে বেশি দূরে চলে যেতে পারে (overshoot) এবং একই বিন্দুতে মিলিত হতে (converge) ব্যর্থ হবে 
- যখন একটি লোকাল মিনিমামে পৌঁছবেন 
  - tangent/derivative এর গ্রেডিয়েন্ট হবে 0
  - তাই derivative term = 0
  - alpha * 0 = 0
  - তাই ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D%20%3D%20%5CTheta%20_%7B1%7D%20-%200)
  - তাই ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এর মান একই থাকবে 
- গ্লোবাল মিনিমামের যত নিকটবর্তী হবে ডেরিভেটিভ টার্ম তত ছোট হতে থাকবে, তাই আপডেট ছোট হবে, আলফা নির্দিষ্ট থাকলেও 
  - অর্থাৎ এলগোরিদম যখন চলছে যত মিনিমামের কাছে যাবে তত ছোট স্টেপ নিবে 
  - তাই একটু পর পর আলফা কে পরিবর্তন করার দরকার নেই 

### গ্রেডিয়েন্ট ডিসেন্টের সাথে লিনিয়ার রিগ্রেশন (Linear regression with gradient descent)
- স্কয়ার্ড এরর কস্ট ফাংশন ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%29) কে মিনিমাইজ করতে গ্রেডিয়েন্ট ডিসেন্ট প্রয়োগ করতে হবে 
- এখন আমাদের কাছে আছে একটি পার্শিয়াল ডেরিভেটিভ 

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[21].png)

- এখানে শুধুমাত্র প্রথম এক্সপ্রেশনটিকে ব্যাখ্যা করছি 
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20J%28%5CTheta%20_%7B0%7D%2C%5CTheta%20_%7B1%7D%29%20%3D%201/2m....)
  - ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20h_%7B%5CTheta%20%7D%28x%29%3D%5CTheta%20_%7B0%7D&plus;%5CTheta%20_%7B1%7D*x)
- তাই প্রত্যেক প্যারামিটারের জন্য আমাদেরকে ডেরিভেটিভ নির্ধারণ করতে হবে 
  - যখন j = ০
  - যখন j = 1
- ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B0%7D) এবং ![](http://latex.codecogs.com/gif.latex?%5Cfn_cm%20%5CTheta%20_%7B1%7D) এর ক্ষেত্রে এই পার্শিয়াল ডেরিভেটিভ বের করি 
  - j = ০ এবং j = 1 এই শর্তে যখন আমরা এই এক্সপ্রেশনকে ডিরাইভ করি তখন আমরা পাই 

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[22].png)

- এটিকে পরীক্ষা করতে হলে মাল্টিভেরিয়েট ক্যালকুলাস (multivariate calculus) জানতে হবে 
  - যাতে গ্রেডিয়েন্ট ডিসেন্ট এলগোরিদমে আবার মানগুলো ব্যবহার করা যায়   
- এটি কিভাবে কাজ করে 
  - বিভিন্ন লোকাল অপটিমামে মিলিত হবার ঝুঁকি রয়েছে 
  - লিনিয়ার রিগ্রেশন কস্ট ফাংশন সবসময় একটি **কনভেক্স ফাংশন (convex function)** - সর্বদা মাত্র একটি মিনিমাম 
    - বোল বা বাটির আকৃতির 
    - একটি গ্লোবাল অপটিমা (global optima)
      - কাজেই গ্রেডিয়েন্ট ডিসেন্ট সর্বদা গ্লোবাল অপ্টিমাতে মিলিত (converge) হবে 
  - বাস্তবে 
    - মানগুলোকে ইনিশিয়ালাইজ করতে হয় 
      - ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B0%7D%20%3D%20900)
      - ![](http://latex.codecogs.com/gif.latex?%5CTheta%20_%7B1%7D%20%3D%20-0.1)

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[23].png)

- একটি গ্লোবাল মিনিমামে (global minimum) গিয়ে শেষ হয় 
- এটি আসলে **ব্যাচ গ্রেডিয়েন্ট ডিসেন্ট (Batch Gradient Descent)**
  - প্রতিটি ধাপে সব গুলো ট্রেনিং ডাটার উপর নজর রাখা হচ্ছে  
    - প্রতিটি ধাপে হিসাব করা হচ্ছে m সংখ্যক ট্রেনিং এক্সাম্পল (m training examples)
  - মাঝে মাঝে নন-ব্যাচও (non-batch) দেখা যায়, যা কিনা অল্প ডাটা সাবসেটগুলো (data subsets) নিয়ে কাজ করে 
    - আমরা অন্য ধরণের গ্রেডিয়েন্ট ডিসেন্ট (যখন m বেশ বড় হয় তখন ব্যবহার করার জন্য) পরবর্তীতে দেখব 
- মিনিমাম ফাংশনের সমাধান খোঁজার জন্য একটি নিউমেরিকাল সল্যুশন (numerical solution) রয়েছে 
  - নরমাল ইকুয়েশন (Normal equations) মেথড 
  - গ্রেডিয়েন্ট ডিসেন্ট যদিও বড় ডাটা সেটে ভাল কাজ (scales better) করে 
  - প্রাসঙ্গিক নানান ক্ষেত্রে এবং মেশিন লার্নিং এ ব্যবহার করা হয় 

**এরপর - গুরুত্বপূর্ণ এক্সটেনশন (extensions)**

এলগোরিদমের দুটি এক্সটেনশন 

- **১. নিউমেরিকাল সল্যুশনের নরমাল ইকুয়েশন**
  - মিনিমাইজেশন প্রবলেমটি সমাধান করার জন্য আমরা নিউমেরিক পদ্ধতি (numeric method) ব্যবহার করতে পারি যেটি গ্রেডিয়েন্ট ডিসেন্ট যে ইটারেটিভ এপ্রোচ (iterative approach) ব্যবহার করে সেটি এড়িয়ে চলে 
  - নরমাল ইকুয়েশন মেথড 
  - এর কিছু উপকারিতা ও অপকারিতা আছে 
    - উপকারিতা 
      - আলফা (alpha) আর থাকছে না 
      - কিছু ক্ষেত্রে আরো দ্রুত কাজ করতে পারে 
    - অপকারিতা 
      - আরো অধিক জটিল (complicated)
    - **লিনিয়ার রিগ্রেশনের সাথে একাধিক ফিচার (linear regression with multiple features)** অংশে নরমাল ইকুয়েশন নিয়ে আলোচনা করা হবে 
    - ২. আমরা অধিক সংখ্যক ফিচার দিয়েও শিখতে পারি 
  - অন্য আরো কিছু প্যারামিটার থাকতে পারে যা থেকে প্রাইস (price) জানা যায় 
  - হাউসের ক্ষেত্রে 
    - Size
    - Age
    - Number bedrooms
    - Number floors
  - x1, x2, x3, x4
- একাধিক ফিচার থাকলে প্লট করাটা কঠিন হয়ে যায় 
  - ত্রিমাত্রিক (3 dimensions) এর বেশি প্লট করা আসলে সম্ভব নয় 
  - নোটেশন (notation) গুলোও আরো জটিল হয়ে যায় 
      - এটি বুঝে নেয়ার সবচেয়ে উত্তম উপায় হচ্ছে লিনিয়ার এলজেব্রা (linear algebra)
      -  নোটেশন ও অন্য কাজগুলো ম্যাট্রিক্স এবং ভেক্টর দিয়ে করা যায় 
      - যেমন: ম্যাট্রিক্স 

![](http://www.holehouse.org/mlclass/01_02_Introduction_regression_analysis_and_gr_files/Image%20[24].png)

- এই ম্যাট্রিক্সে দেখতে পাচ্ছি 
  - Size
  - Number of bedrooms
  - Number floors
  - Age of home
- সবকিছু একটি ভ্যারিয়েবলের মধ্যে আছে 
  - নাম্বারের ব্লক, সব ডাটা একটি বড় ব্লকে গোছানো থাকে 
- ভেক্টর 
  - y হিসাবে দেখানো হয়েছে 
  - প্রাইসগুলো দেখাচ্ছে 
- আরো জটিল লিনিয়ার রিগ্রেশনের জন্য লিনিয়ার এলজেব্রা দরকার হবে 
- হিসাব নিকাশে কার্যকর মডেল (computationally efficient models) তৈরী করার জন্য লিনিয়ার এলজেব্রা ভাল (পরে এই বিষয়টি আরো দেখা যাবে)
  - বড় ডাটা সেট নিয়ে কাজ করতে সহায়তা করে 
  - কোন প্রবলেমকে ভেক্টরাইজেশন (vectorization) করা হচ্ছে সাধারণ একটি অপ্টিমাইজেশন টেকনিক (common optimization technique)

http://latex.codecogs.com/eqneditor/editor.php
