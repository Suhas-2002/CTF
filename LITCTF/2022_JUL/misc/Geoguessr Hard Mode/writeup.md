# Geoguessr Hard Mode

## Description
Where am I now? The flag is LITCTF{latitude,longtitude} rounded to the third decimal place. (Example: LITCTF{42.444,-71.230})

`The challenge file is present in the same directory with the name challenge.png.`

## Solution

#### Method-1
1. Use this link -> https://yandex.com/ to find the name of the place given in the challenge file.
2. Once you find the name, map it on Google maps and take out the latitude and longitude.
3. [ latitude and longitude can be found in the address bar ]


#### Method-2
By looking at the image it is extremely likely that it is a current or former French colony in Africa, judging by the Pan-African colors being painted on both the tree and the power station to the left, the fact that "Hotel de Ville" is the French name for a town hall, the climate and vegetation and there being a Sub-Saharan African man visible in the background. You could approximate the country by sifting through "hotel de ville" + every African country with those colors in their flag, ending up with Senegal, but with the right crop Google Lens actually shows you several news articles confirming that this is in Tambacounda, Senegal. Find the location manually with street view, it's not a big place.

`flag format -> LITCTF{lattitude,longitude} and roundoff the lattitude and longitude to 3 decimal places.`

Challenge Link -> https://lit.lhsmathcs.org/ctfchal
