# Mobile Security Decompiled App
Given corrupted APK and the assignment was to fix the bugs.

## Pelimnery research
First of all I run the application in my private phone to test the features and the overall applcation. After playing with both the id selction screen and the "puzzle" screen I relized that when you input an inccored ID number (one that is shorter than 9 digits) the application crashed. With that knowlege I was focuesed to research more about the input avtivity in oder to find the bug and the puzzle acitivty in order to find the soultion to the problem


## Work steps

 - Analyzing the APK via android studio in order to see the strings.xml file and the overall structre of the application
 - Decompiled the APK with  JADX
 - Analyzing the logic of both the activites and finding the bug
 - Tried to figure out the logic behind the app and encoutered with this bug:
```java
  String state = data.split(",")[Integer.valueOf(String.valueOf(id.charAt(7))).intValue()];
  ```
 - Fix the bug with:
```java
if(id.length() != 9) {  
  runOnUiThread(() -> menu_EDT_id.setError("ID must be 9 characters long"));  
  return;  
}
```
 -  Create new project and transfer the Activities, layout  URL String value and the Manifest
 - Add internet permission to the application
## How to play the game
After inserting ID each digit represent a direction
digit % 4
 - `0` - Left
 - `1` - Right
 - `2` - Up
 - `3` - Down

After pressing the correct code you will get a toast message with the answered location you have been arrived. 
The location you get is by the 8th digit of your ID:

0.  `California`
1. `Texas`
2. `Florida`
3. `New York`
4. `Illinois`
5. `Pennsylvania`
6. `Ohio`
7. `Washington`
8. `Michigan`
9. `Arizona`

All the location are given from the url that in the strings.xml  
My location was California
