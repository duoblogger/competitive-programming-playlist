---
mathjax: true
layout: post
title: BDOI Practice Contest-1 Analysis
mathjax: true
author: Ahnaf Shahriar Asif
Difficulty: Hard
tags: [Contest analysis]
ads_niche: 5
categories: [contest analysis, data structure, graph, math]
subtitle: কোডফোর্সেসে আমরা নিয়মিত প্রোগ্রামিং কন্টেস্ট নিয়ে থাকি। এরকমই একটা কন্টেস্টের এডিটোরিয়াল এটি। codeforces এর BDOI Practice Group থেকে কন্টেস্টি দেখে নাও। কন্টেস্টের টাইটলে "BDOI Practice Contest-1"। কন্টেস্টটি দেখে নাও। তারপর এডিটোরিয়াল দেখা শুরু করা যাক।  
permalink: /bdoi-practice-contest-1/
# background: '/img/somehow.png'
---

# Problems 

* [Problem 1](#problem1)
* [Problem 2](#problem2)
* [Problem 3](#problem3)
* [Problem 4](#problem4)

## <font color="green"><a name="problem1">Problem 1</a></font>

**Problem Description:** তোমাকে একটি সংখ্যা দেয়া হবে, তোমাকে "Welcome to BDOI Practice Contest-" এই স্ট্রিংয়ের সাথে সংখ্যাটি প্রিন্ট করতে হবে। সম্পূর্ন প্রব্লেমটি [এখানে]({{ "/assets/pdf/hello-world-r4-en.pdf" | relative_url}}) পাওয়া যাবে। 

**Problem Solution:** খুবই সহজ সমস্যা। এটার সলিউশন বলার মতো কিছু নেই। এটি দেয়া হয়েছে জাস্ট কয়জন পার্টিসিপেন্ট কন্টেস্ট করতে ঢুকেছে সেটা দেখার জন্য।  



## <font color="green"><a name="problem2">Problem 2</a></font>

**Problem Description:** তোমাকে $$n$$ টি সংখ্যা দেয়া আছে। তোমাকে সংখ্যাগুলোর সকল সাবসেট বেড় করে প্রত্যেকটা সাবসেটের Or Sum বেড় করে সেগুলো যোগ করে $$10^9+7$$ দিয়ে মড করে আউটপুট দিতে হবে। পুরো প্রব্লেমসেট [এখানে]({{ "/assets/pdf/simple-game-r7-en.pdf" | relative_url}}) পাওয়া যাবে। 

**Problem Solution:** আমরা ধাপে ধাপে সল্ভ করার চেষ্টা করবো। একটা একটা করে সাবটাস্ক দেখি। 

#### Subtask 1

$$n$$ এর মান এতই ছোট যে আমরা হাতে হাতে হিসাব করে বেড় করে ফেলতে পারি। সর্বোচ্চ $$2^3-1 = 7$$ টি সাবসেট থাকতে পারে। যেটা হাতে হাতে বেড় করাই যায়। 

#### Subtask 2

$$n \leq 10^5$$, যার মানে আমরা সবগুলো সাবসেট বেড় করতে পারবোনা। কিন্তু বলা আছে $$a_1 = a_2 = ...... = a_n$$। এবার আমরা চিন্তা করি। আমাদের সবগুলা সাবসেট বেড় করে ওগুলার Or Sum নিতে হবে। তবে আমরা কিন্তু Or এর একটা বৈশিষ্ট জানি, সেটা হলো $$a \lor a = a$$ . যার মানে এটাও সত্যি যে $$a \lor a \lor a \lor a ...... = a$$। তাহলে আমাদের প্রত্যেকটা সাবসেটের Or Sum হবে $$a_i$$। মোট সাবসেট থাকতে পারে $$2^n-1$$ টি।  যার মানে উত্তর দাঁড়াবে $$ \big\{ a_0 \times (2^n-1) \big\} \mod m$$। 

#### Subtask 3

$ n \leq 20$, অর্থাৎ, আমরা সহজেই ব্যাকট্র্যাক করে সল্ভ করতে পারি। আমরা সবগুলো সাবসেট বেড় করবো, সবগুলোর Or Sum বেড় করবো, তারপর সেগুলো যোগ করবো। তার মানে ঠিক প্রব্লেমে যা করতে বলা হয়েছে, সেটাই করে ফেলব ব্যাকট্র্যাক করে। কম্প্লেক্সিটি হবে $\mathcal O(n \times 2^n)$। যেহেতু $n \leq 20$, মোটামুটি $20 \times 2^{20} \approx 2 \times 10^7$। 

#### Subtask 5

আমরা Subtask 4 একটু পরে সল্ভ করবো। সাবটাস্ক 5 তুলনামূলক সহজ, আর Subtask 3 এর সাথে রিলেটেড। এখানে $n \leq 10^5$ কিন্তু $n-1$ টা সংখ্যা একই এবং কেবলমাত্র একটি সংখ্যা আলাদা থাকবে। তার মানে মাত্র $2$ টি আলাদা আলাদা সংখ্যা আছে। ধরে নিচ্ছি $a$ আর $b$। $a$ আছে $n-1$ বার আর $b$ আছে 1 বার। একটু খেয়াল করলে দেখা যাবে, আমরা $n-1$ টি সংখ্যা দিয়ে $2^{n-1}$ টি সাবসেট বানাতে পারবো, যেগুলোর প্রত্যেকটির Or Sum হবে $a$। আবার $b$ কে ব্যাবহার করে আরও $2^{n-1}$ টি সাবসেট বানানো যাবে যেগুলোর Or sum হওয়ার কথা $a \lor b$। আবার ওই $2^{n-1}$ টির মধ্যে একটা সাবসেটে শুধু b থাকবে। তাহলে আমাদের মূল উত্তর হবে $$ \big\{ a \times 2^{n-1} + (a \lor b) \times (2^{n-1}-1) + b \big\} \mod m $$। 

#### Subtask 6

আমরা Subtask 5 এর দিকে লক্ষ্য করি। সেখানে দুইটা আলাদা আলাদা সংখ্যা $a,b$ আছে। যেজন্য উত্তর হয়েছে $$ \big\{ a \times 2^{n-1} + (a \lor b) \times 2^{n-1} \big\} \mod m $$। এখন যদি দুইটার বদলে $a_0,a_1,a_2.....,a_{19}$ থাকে, আমরা কি সল্ভ করতে পারবো? 

এবার আমাদের 3 টা Subtask বাকি আছে। Subtask 4, Subtask 7, Subtask 8। এই তিনটা সাবটাস্ক সল্ভ করার জন্য আমাদেরকে আরেকটু গনিত নিয়ে চিন্তাভাবনা করতে হবে। 

#### <font color="#540eb5">Observation:</font>

আমরা আবার শুরুতে চলে যাই। মূলত Or বলতে কি বোঝায়? 

* $1 \lor 1 = 1$
* $1 \lor 0 = 1$
* $0 \lor 1 = 1$
* $0 \lor 0 = 0$

এবার ধরা যাক আমরা একটি সাবসেটের সবগুলো সংখ্যার Or বেড় করবো। তাহলে মূলত কী হচ্ছে ? নিচের 4 টি নাম্বারের Or বেড় করার চেষ্টা করে দেখ। 

* $5 = 0000101$
* $7 = 0000111$
* $8 = 0001000$
* $3 = 0000011$

একটু চিন্তা করলেই আমরা একটা ব্যাপার ধরতে পারবো। আমাদের যদি ডানদিক থেকে $ith$ ইন্ডেক্সে(0 based index) কোনো একটি বিট 1 থাকে তাহলে সেখানে $2^i$ পরিমান সংখ্যা যোগ হচ্ছে। অর্থাৎ, উপরের লিস্টে i = 3 এ একটি বিট অন আছে, যার মানে আমাদের Or sum এ $2^3$  য‌োগ হবে। যার মানে দাঁড়াচ্ছে, $5 \lor 7 \lor 8 \lor 3 = 2^0+2^1+2^2+2^3 = 15$ কারন ওই সাবসেটে $0,1,2,3$ তম ইন্ডেক্সগুলোতে অন্তত একটি করে বিট অন আছে। এটা তো গেল একটা সাবসেটের সাম। এবার চিন্তা করি, যদি $$[5,7,8,3 ]$$ একটি সেট হয়, আর এর সবগুলো সাবসেটের অর সাম বেড় করতে বলা হয় তাহলে কি করা যেতে পারে। 

উপরের লিস্টের দিকে আবার তাকাই। ধরি ডান থেকে $$0th$$ ইন্ডেক্সটা। ওখানে দেখা যাচ্ছে 3 টা বিট অন, আর 1 টা বিট অফ। যার মানে দাড়াচ্ছে সেটে কেবলমাত্র একটা সংখ্যা আছে, যার প্রথম বিট $1$ নয়। তার মানে এরকম $2^1-1$ টা সাবসেট পাওয়া যাবে যখন উত্তরের সাথে $2^0$ add হবেনা। বাকি সবগুলো সাবসেটে একবার করে $2^0$ add হবে। আবার $1st$ ইন্ডেক্সের দিকে তাকাই। সেখানে 2 টি সংখ্যার বিট অন, 2 টি সংখ্যার বিট অফ। যার মানে $2^2-1$ টি সাবসেট পাওয়া যাবে, যখন উত্তরের সাথে $2^1$ add হবেনা। আবার এরকম $2^2-1$ টি সাবসেট পাওয়া যাবে যখন উত্তরের সাথে $2^1$ add হবে। এভাবে প্রত্যেক বিটের জন্য কতটুকু করে উত্তরের সাথে যোগ হচ্ছে এটা বেড় করতে পারলেই হবে। আমাদের বিট থাকতে পারে সর্বোচ্চ $\mathcal \log(a_i)$ টি। যার মানে আমাদের মোট কম্প্লেক্সিটি হলো ‌$\mathcal O(n \times \log(max(a_0,a_1......,a_{n-1})))$ । মূলত এই অবজারভেশন দিয়ে Subtask 4,7,8 তিনটাই করে ফেলা যায়। যার মানে এটাই 100 পয়েন্ট তোলার সলিউশন। নিচে কোড দিয়ে দিচ্ছি। 

```c++
// check(a,b) is true if bth bit of a is on. Else, it's false. 
int n;
scanf("%lld",&n);
for(int i = 0; i < n;i++){
   scanf("%lld",&ara[i]);
}
int total = bigmod(2ll,n,mod); 
int ans = 0ll;
for(int x = 0; x < 39;x++){
    // loop till 31 is enough. I'm doing it for extra safety
    int cnt = 0;
    for(int i = 0; i < n;i++){
       if(!check(ara[i],x))cnt++;
    }
    int kaka = (total-bigmod(2,cnt,mod))%mod;
    ans = (ans+(kaka*bigmod(2,x,mod))%mod)%mod;
}
printf("%lld\n ",(ans+mod*2)%mod);
```



## <font color="green"><a name="problem3">Problem 3</a></font>

**প্রব্লেমটির জন্য [তাসমীম রেজা](https://www.facebook.com/profile.php?id=100008132494101&ref=br_rs) ভাইয়াকে ধন্যবাদ। প্রব্লেমটি ভাইয়ার কাছ থেকে নেয়া হয়েছে।**

**Problem Description:**  তোমাকে m টি তথ্য দেয়া থাকবে। প্রত্যেকবার একজোড়া সংখ্যা দেয়া থাকবে, ধরা যাক a আর b । যার মানে দাঁড়াবে Bob এর a তম ভাতিজা b তম ভাতিজার থেকে বড়। তোমাকে প্রত্যেকটা ইন্স্ট্রাকশন দেয়ার পড়ে বলতে হবে এখন পর্যন্ত পাওয়া তথ্য সত্যি কিনা।  পুরো প্রব্লেমটি [এখানে]({{ "/assets/pdf/bob-and-his-nephews-r3-en.pdf" | relative_url}}) পাওয়া যাবে। 

**Problem Solution:** এই প্রব্লেমটা সল্ভ করার জন্য আমরা একটু গ্রাফ থিওরির ধারনা ব্যাবহার করতে পারি। ধরা যাক Bob এর ভাতিজারা হচ্ছে একেকটা নোড আর একটা করে ইন্স্ট্রাকশন $<a,b>$ দেয়া মানে হলো a  থেকে b তে একটা এজ আছে। a থেকে b তে যাওয়া যাবে। এটার মানে এই না, যে b থেকেও a তে যাওয়া যাবে। তার মানে একটা Directed Graph বানাতে থাকবো আমরা। আর এই গ্রাফটি কখন Invalid হবে? যখন ওই ডিরেক্টেড গ্রাফে এক বা একাধিক সাইকেল থাকবে। কারন একটা সাইকেল থাকা মানে হলো ঘুরে ঘুরে নিজেই নিজের থেকে বড় হয়ে যাওয়া। না বুঝে থাকলে খাতায় এঁকে দেখলেই পরিষ্কার হবে। তাহলে গ্রাফে সাইকেল থাকলেই ডাটা ইনভ্যালিড হয়ে যাচ্ছে। আরও একটা কথা, একবার যদি ডাটা ইনভ্যালিড হয়ে যায়, সেটি কি আর কখনো ভ্যালিড হবে? কারন তোমাকে জিজ্ঞাস করা হয়েছে **এখন পর্যন্ত** দেয়া ডাটাগুলো ভ্যালিড কিনা। তাই তোমার ডাটা একবার ইনভ্যালিড হয়ে গেলে সেটি আর কখনো ভ্যালিড হবেনা। অর্থাৎ আমাদের উত্তর হবে অনেকটা এরকমঃ $.....Yes,Yes,Yes,......No,No,No...$

একবার No হয়ে গেলে পরের সবগুলোই No হবে। 

এবার আমরা একটা একটা করে সলভ করার চেষ্টা করি।  

#### Subtask 1

$n$ এর মান খুবই ছোট। আমরা একদম নেইভ ব্রুটফোর্স করে ফেলতে পারি। প্রত্যেকবার ইনপুট নেয়ার সময় $n$ বার DFS চালিয়ে চেক করে দেখব সব ঠিক আছে কিনা। এভাবে যতক্ষন একটা NO না পাচ্ছি ততক্ষন DFS করে দেখতে থাকবো। কম্প্লেক্সিটি $\mathcal O(n^2\times (n+m))$। 

#### Subtask 2

আমরা আগের সাবটাস্কের মতো করে চিন্তা করে কি কোনোভাবে কম্প্লেক্সিটি কমিয়ে $\mathcal O(n^2 + (n+m))$ করা যায় না? 

#### Subtask 3

 আমাদের সমস্যা কোথায় হচ্ছে? ডিরেক্টেড গ্রাফে $ \mathcal O(n+m)$ বা লিনিয়ার টাইমে সাইকেল বেড় করতে পারছি না। একবার সাইকেল বেড় করতেই $n$ বার DFS চালাতে হচ্ছে। যার কারনে সমস্যা হচ্ছে। আমরা চাইলে লিনিয়ার টাইমে সাইকেল বেড় করতে পারি। [এখান থেকে](<https://cp-algorithms.com/graph/finding-cycle.html>) দেখে নাও। তাহলে আমাদের Overall কম্প্লেক্সিটি হলো $\mathcal O(n \times (m))$ 

#### Subtask 4

যেহেতু সর্বোচ্চ একটা NO থাকতে পারে, এটা খুব সহজেই বলা যায় যে শুধুমাত্র শেষ ডাটাটিই হয় ভুল হবে, নাইলে সবগুলো সঠিক। তাহলে শুধুমাত্র শেষের বার DFS করলেই তো হয়। একদম নেইভ DFS করলেও $\mathcal O(n^2+nm)$ এ করা যায়। 

#### Subtask 5

এখানে একটি জিনিস লক্ষ্যনীয়। আমাদের উত্তরটিতে প্রথমে বেশ কিছু YES থাকবে, তারপর একবার NO হয়ে গেলে বাকি সব NO। তাহলে আমরা চাইলে সর্বপ্রথম NO খুঁজে বেড় করতে পারি। ব্যাপারটি হলো, ধরা যাক আমরা বেড় করেছি সর্বপ্রথম NO আছে $x$ তম ইন্ডেক্সে। তাহলে $1$ থেকে $x-1$ পর্যন্ত উত্তর হবে YES , আর $x$ থেকে $m$ পর্যন্ত উত্তর হবে NO। এই কাজটি আমরা চাইলে কি বাইনারি সার্চ করে বেড় করতে পারি না ? আমরা যদি অর্ধেক এজ নিয়ে একটা DFS চালাই আর দেখি সাইকেল পাওয়া গেছে তাহলে আর ডানে না গিয়ে বামে সাইকেল খুজঁবো। আর যদি দেখি সাইকেল পাওয়া যাচ্ছে না তাহলে ডানে খুঁজবো। তাহলে আমাদের সর্বোচ্চ $log(m)$ বার DFS করতে হচ্ছে। ওভারঅল কম্প্লেক্সিটি $\mathcal O((n+m) \times \log m)$

কোডটি দিয়ে দিচ্ছিঃ 

```c++
while(high - low >= 0){
    int mid = (high+low)/2;
    //cout << " # " <<  mid << endl;
    for(int i = 1; i <= mid; i++){
        adj[query[i].first-1].push_back(query[i].second-1);
    }
    if(find_cycle()){
        ans = mid;
        low = mid+1;
    }
    else high = mid-1;
    for(int i = 0; i <= n; i++){
        adj[i].clear();
    }
}
// we will print YES from 1...ans-1 and NO for rest of them. 
```



## <font color="green"><a name="problem4">Problem 4</a></font>

**এই প্রব্লেমটির জন্য [শাফিন আলমকে](<https://www.facebook.com/profile.php?id=100009412935900>) অসংখ্য ধন্যবাদ। প্রব্লেমটি তার বানানো।** 

**Problem Description:** একটি $n \times m$ গ্রিড দেয়া আছে, তোমাকে এমন দুটি পাথ বেড় করতে হবে, যেন পাথ দুটির মধ্যে কোনো কমন নোড না থাকে আর এদের পাথের sum যেন সর্বোচ্চ হয়। তবে প্রথম আর শেষ নোড তো কমন থাকবেই, ওটা আলাদা। সম্পূর্ন প্রব্লেম [এখানে]({{ "/assets/pdf/thinking-about-a-geometry-problem-r1-en.pdf" | relative_url}}) পাওয়া যাবে। 

**Problem Solution:** এটি দেখেই বোঝা যাচ্ছে একটি ডিপি প্রব্লেম। আমরা একটা একটা করে সাবটাস্ক সল্ভ করি। 

#### Subtask 1

$m = 2$, যার মানে মূলত এখানে সর্বোচ্চ দুটি পাথই পাওয়া যাবে, নিচের row আর উপরের row. যার মানে দাড়াচ্ছে গ্রিডের সবগুলো ভ্যালু যোগ করে দিলেই উত্তর হয়ে যাবে। 

#### Subtask 2

এখানে $n$ এর মান এতই কম যে শুধুমাত্র রিকার্শন দিয়ে সল্ভ করা সম্ভব। আমরা একবার গিয়ে আলাদা রাস্তায় ফিরে আসাকে ওভাবে কল্পনা না করে যদি চিন্তা করি, দুইবার উপর থেকে নিচে আলাদা রাস্তায় যাবো, তাহলেই হয়ে যাচ্ছে। আমরা রিকার্শন করে All possible solution বেড় করবো আর তার থেকে সবথেকে বড় sum টাকে নিব। যেহেতু $n,m \leq 9$, এটা কোনোমতে কাজ করবে। 

#### Subtask 3 

এখানে $n,m \leq 50$, তাই ডিপি না করে আর উপায় নেই। ডিপি খুবই সহজ। আমরা 4 টা স্টেট রাখবো ডিপিতে। $dp(x_1,y_1,x_2,y_2)$ । এবার জাস্ট আমরা একবার প্রথম পাথে ডানে/নিচে আর দ্বিতীয় পাথে ডানে/নিচে গিয়ে ডিপি করতে থাকবো। আর ম্যাক্সিমাম নিতে থাকবো। আর আমাদের পাথ intersect করলো কিনা সেটাও চেক করা লাগবে। টাইম কম্প্লেক্সিটি $\mathcal O(n^2*m^2) \approx O(n^4)$ আর মেমরি কম্প্লেক্সিটিও $\mathcal O(n^4)$। 

#### Subtask 4

$n,m \leq 100$, যার মানে আমাদের এখানেও $\mathcal O(n^4)$ টাইম কম্প্লেক্সিটিতেও কোনো সমস্যা হওয়ার কথা না। কিন্তু সমস্যা হলো মেমরি কম্প্লেক্সিটিতে। $10^8$ পরিমান মেমরি নেয়া আমাদের পক্ষে সম্ভব নয়। তাই আমাদের স্টেট কমাতে হবে। এখানে একটা লক্ষ্যনীয় ব্যাপার আছে। আমরা প্রত্যেকবার রিকার্শনে প্রথম পাথে এক ডানে বা এক নিচে যাচ্ছি, আবার দ্বিতীয় পাথে এক ডানে বা নিচে যাচ্ছি, যার মানে $x_1+y_1$ আর $x_2+y_2$ সর্বদা সমান। তাহলে আমাদের যদি $x_1,y_1,x_2$ দেয়া থাকে তাহলে আমরা বলতে পারি $y_2 = x_1+y_1-x_2$। তাহলে আমাদের মূলত ডিপিতে আর $y_2$ রাখতে হচ্ছেনা। তাহলে মেমরি কম্প্লেক্সিটি হয়ে গেল $\mathcal O(n^3)$ আর টাইম কম্প্লেক্সিটি $\mathcal O(n^3)$, যা 100 পয়েন্ট পাওয়ার জন্য যথেষ্ট। কোড দিয়ে দিচ্ছি। 

‍‍‍

```c++
// ll stands for [long long int] 
ll solve(ll i, ll r, ll x)
{
    ll y = i+r-x;// here we're calculating y from (i,r,x)
    if(i>=n || r >= m || x >=n || y >= m) return 0;
    if(i==x && r==y) return 0;// path intersected 
    if(dp[i][r][x]!=-1) return dp[i][r][x];
    ll ret = 0;
 
    ret = max(ret, solve(i+1, r, x+1));
    ret = max(ret, solve(i+1, r, x));
    ret = max(ret, solve(i, r+1, x+1));
    ret = max(ret, solve(i, r+1, x));
 
    return dp[i][r][x] = ret+arr[i][r]+arr[x][y];
}
```

সবাইকে ধন্যবাদ। 