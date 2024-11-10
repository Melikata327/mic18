نام ازمایش ###
نمایش اعداد با سون سگمنت
 ### هدف ازمایش
در این آزمایش می خواهیم بر روی ماژول سون سگمنت مجموعه اعداد صحیح یک رقمی را نمایش دهیم.
###  ابزارو وسایل
برد بورد،برد اردینو،سیم جامپر،مقاومت 220 اهمی هفت عدد،سون سگمنت 
### شرح ازمایش
. مانند ازمایش قبلی فقط با کد کمی متفاوت تر از قبلی و بستن ان در مدار که فرق دارد
   دانلود نموده و نصب می کنیمsevseg کد را از کتابخانه و کد را کپی می نماییم. 
برای اتصال به اردینو به این شکل عمل می کنیم :

 پایه ۲ به d
پایه ۳به com
پایه ۵ به  dp
پایه ۶ به b
پایه ۷ به a
پایه۸  به com
پایه ۹ به f  

### کد 


```cpp
#include "SevSeg.h"
SevSeg sevseg;

void setup()
{
    //Set to 1 for single digit display
    byte numDigits = 1;

    //defines common pins while using multi-digit display. Left empty as we have a single digit display
    byte digitPins[] = {};

    //Defines arduino pin connections in order: A, B, C, D, E, F, G, DP
    byte segmentPins[] = {3, 2, 8, 7, 6, 4, 5, 9};
    bool resistorsOnSegments = true;

    //Initialize sevseg object. Uncomment second line if you use common cathode 7 segment
    sevseg.begin(COMMON_ANODE, numDigits, digitPins, segmentPins, resistorsOnSegments);
    //sevseg.begin(COMMON_CATHODE, numDigits, digitPins, segmentPins, resistorsOnSegments);

    sevseg.setBrightness(90);
}

void loop()
{
   //Display numbers one by one with 2 seconds delay
   for(int i = 0; i < 10; i++)
   {
     sevseg.setNumber(i);
     sevseg.refreshDisplay();
     delay(2000);
   }
}
``` 
