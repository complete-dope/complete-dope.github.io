---
layout : post
date : 2025-04-13
title : A bit about F & O
---

Random learning 

Nifty 50 :
Index h , joh ki top 50 indian companies ko track krta h .. 

Ye apne aap m khuch nhi hota toh isko khareed bech nhi skte

nifty m trading krne ka matlab hota h , ki nifty k futures m trade krna 



FUTURES 
paperwork hota h 
3 month in future , last thrusday of each month ka dekha jata h 

near future and far-away future 

Lot m kaam krta h ,multi-day kr skte ho and isme short kr skte ho 


Last thrusday of that month ko expire hoga mtlb agar aapne apna balance khtm nhi kiya uss din tk toh apka broker automatically apko uss din nikal dega .. 

Futures m you can go either go long or go short 

already leveraged prodcut h ... 
 

spot price : abhi ka kya price h stock ka 
future price : future jispe trade ho rha h uska kya price h 

if future price > spot price : toh bolte h premium m chal rha h 
if future price < spot price : toh bolte h discount m chal rha h 


Swing trade : iska matlba hota h ki stock ko ek 2 weeks ya 1-2 months tk hold krna 

Future ka mtlb ki ha hm isko badme ( fixed date ) ko buy ya sell krenge 

Agar you think ki haa ye contract ka price expiry se pehle he acha mil rha toh bech ke nikal jao .. ab woh uss buyer ki headache h ki expiry p kya hoga .. 


WHY IS CALLED RISKY ? 

Future m entry li tune , 

lot size = 50 
no of lots buyed = 20
price per lot = 10000 

TOTAL POSITION VALUE = 50 * 20 * 10000 = 1Cr
Margin paid = 1.5 lakh 

Tune li long position ( ki bhai ye toh badega ) 
price per lot gya : 9500
TERA LOSS = 500 * 50 * 20 = 5 lakh 

Tune trade li : 1.5 lakh p loss ho gya 5 lakh 
tera broker bola ki bhai ya toh 3.5 lkah accout m daal ya mai margin-call maar rha hu ( mtlb forced selling / mai loss m bech rha hu ) 

Agar margin call lg gyi toh 3.5 lakh ka loss aab tujhe broken ko dena h.. woh recovery team , legal ways sb lga dega ye paisa nikalne m tujhse!!

Agar SL k bina trade li toh, unlimited loss ho skta h 

Interface se dekhna h abhi dhang se !! 





--- OPTIONS --- 
Index ke options hr week expire hote h 
Stock ke index hr month expire hote h 

Instrument of trade

CE : Matlab Upar 
PE : Matlab Neeche 

Strike price : 
Nifty ka spot price h 18500

In the money : 18400 CE isko read kro ki kya nifty 18400 ke upar h ? Yes toh ye in the money order h 

Out of the money : 18600 CE isko read kro ki kya nifty 18600 ke upar h ?No toh ye out of the money order h 
--> rate km hota h usually  

At the money : Joh strike price k bilkul pass hota h ..  
 

types of Trader :
Option buyer (CE) : small capital se ek decent amount profit krna chahata h , risk factor jyada h , loss k bhi chances hote h 

Option seller (Put) : good capital se small returns banana chahta h with low risk 
 

5 min, 15 min ka time frame: 
call option / call european ( CE ) : market badegi toh CE badega wrna loss hoga 

PE : market giregi toh PE badega .. 


Spot chart always study 

Option : 100 
Intrinsic value : 
Extrinsic value : 





===> ACTUAL BUYING AND SELLING 
Lets make some option calling and execute some orders now !!

DELTA : Option kitna move krega agar underlying 1 rupee move kare toh

**nifty bank** 
APRIL MARKET ANALYSIS (TRADE DAY = 1ST APRIL ) 

support : 47900
delta = -7.31 

** Delta diff between -15 to +15 is considered good !! 

resistance 1 : 52019 
resistance 2 : 53900 , delta = -7.74

*Call option = 53900 ka 
*Put option = 47900 ka 

To make this an Iron Flag Strategy 

47650 ka PE buy karunga 
54000 ka CE buy karunga 


STEPS FOR DOING DELTA NEUTRAL STRATEGY !! 

CE Selling = you are a seller 
PE Selling = you are a buyer

This strategy works for OPTION SELLING 
1. Make strong support and strong resistance for last months (dont consider the current month in action) 
2. Here you assume the market will remain in a sideways motion and you sell a CE at resistance and PE at support 
3. And make sure the delta difference is in between , -15 to +15 in this case   
4. This requires large capital and arnd 4% of avg benefits 
5. Market moves sideways / less volatile from 11AM to 2PM , so this is where this trade works 
6. The side / tail losses in this can be minimised using IRON FLY Strategy where you buy CE above resistance and you buy PE above support.

ETF : exchange traded funds , basket of differnet underlying to diversify the portfolio, these replicate an index and are cheap to buy with the same exposure as of an index 

Option greeks : 
What are these and who made them and why do they exist ? --> These are in market to favous buyers and seller . We have multiple greeks and they all work differently some favour buyers other favour sellers 


*Theta*: 
This favours the seller.. and this is a time based factor in a premium and constitutes avg of 30% of premium value. The role of theta is to become zero at the expiration day (premium doesn't become zero, theta becomes zero) reduces the value of the premium

*Delta*: 
This tells how much the premium will move if the underlying spot price moves by 1 pts .. 
range = 0 to 1 for calls
range = 0 to -1 for puts
This is the most important value that reduces / makes up the premium 

For ATM calls -> 0.5 
FOR ITM calls -> 1 
For deep OTM calls -> 0 


*Vega*:
Implied Volatility index 
Its a market forecast of a likely movement in a security's price. 


*Gamma*: 
Rate of change of delta for every unit change in the underlying asset's price
IV = implied volatility  
IV jumps from 20 to 25 , but price stays at 100. 
Vega = 0.05
new price = 2 + (0.05 x 5) => 2.25 
cause you are betting on fear 


Example: 
underlying stock = 100 
ATM call strike = 100 
Time to expiry = 5 days
IV = 20% 
Option price = let's say 2 
delta = 0.5 ATM 
gamma = 0.1 
vega = 0.05 

delta = 0.5 + (0.1 x 2) => 0.7 
So, its more like owning 70 shares of stock instead of 50. That's gamma , the position just got more directional .. 

## Credit spread aka bear call spread 
Ek option ko sell krna and doosre option ko buy krte ho dono same expiry date ke hote hain, lekin alag strike price k saath. 

Spot price = 100 
sell put @ 95 -> premium milta hai 3 
buy put @ 90 -> premium dena padta hai 1 

3-1 = 2 * 100 ( 1 lot m 100 shares )
$200 ka paisa directly mil gya jeb m 
ab mai wish krunga ki price 95 se upar he rhe 
and agar neeche bhi aa gya toh mera 90 wala buy cap kr lenge
95 - 90 =  5
max loss = 5 -2 = 3 * 100 = $300 

This is good , agar lgta h market neeche ya sideways rahegi  

## Iron Condor 



























