@title[Automatiske metoder til kvalitetskontrol af vandløb]

<!-- Uggerby å - Fotograf: Søren Holm Pedersen, holmog.dk-->
## Automatiske metoder til kvalitetskontrol af vandløb

---?image="billeder/Field_of_Streams.jpg"

## Historien om en soldats spring

+++?image="billeder/National-Archives-and-Records-Administration---Bailey-bridge.jpg"
### Bro eller ej
<!-- Sort/hvid Kampvogn og bro -->


+++?image="https://upload.wikimedia.org/wikipedia/commons/d/d5/Stereoskop.jpg"
<!-- Fotogrammetri-bænk -->
### Fotogrammetrisk identificeret


+++?image="https://upload.wikimedia.org/wikipedia/commons/5/55/HARVEST.jpg"
<!-- Gammel datamat -->
### Hjælp fra datamater



<!-- SAMMENBINDING? -->

---
## Forudsætninger


+++?image="billeder/sdfe-hillshade-fot-vandloebsmidte-uggerby-aa.jpg"
## Data

+++?image="billeder/sdfe-kronekant.png"

Note:
Det ser jo nemt ud

+++?image="billeder/wonderwoman0731-signpost.jpg"


+++
### Nemt?

Note:
Hvis vi lige vender tilbage, så er det måske ikke så nemt


---
## Algoritmer


+++?image="billeder/gregers---skitse-sektioner.png"&size=auto 90%

Note:
Transekter langs vandløb

+++?image="billeder/gregers---transekter.png"

Note:
Transekter illustreret

+++?image="billeder/gregers---transekt-plot-skaering-Uggerby-aa.png"&size=auto 90%

Note:
Flere transekter plottet


+++
## Sekant

```python
#     b
#    /|
#   / |
# a --- c
#          |bc| = (|ac| * sin(a)) / sin(pi - a - pi/2)
#           Følger af at c er ret og sinusrelationerne
haeldning_rad = haeldning_grad * math.pi / 180.0
sek_under = (bucketwidth * math.sin(haeldning_rad)) 
            /math.sin(math.pi - haeldning_rad - math.pi/2.0)

idx = idx + inc
while (idx < len(b)-1 and idx > 0 and
        b[idx] - b[idx - inc] > sek_under):
    idx = idx + inc
```

Note:
increment er enten +1 eller -1 for "et step til venstre eller højre"

+++
## Den våde kant
```python
# maxstigning: hvor meget må Z stige mellem buckets i b
# maxtotal: hvor meget må Z stige fra den hidtil mindst sete
min = b[idx]
idx = idx + inc
while (idx < len(b)-1 and idx > 0 and 
       b[idx] - b[idx - inc] < maxstigning and 
       b[idx] < min + maxtotal ):
    idx = idx + inc
    if(b[idx] < min):
        min = b[idx]
```

+++?image="billeder/gregers---kronekant.jpg"

Note:
Kronekanten


+++?image="billeder/gregers---kronekant-og-vaadkant.jpg"

Note:
Kronekanten og "den våde kant"


---
## Æstetik og statistik



+++
### EWMA

$$s\_{i} = \lambda x\_{i} + (1-\lambda) s\_{i-1}$$


+++
```python
# Simple EWMA
# l = Lambda
for i in range(1,len(vec)):
    if np.isfinite(vec[i]):
        s[i] = l * vec[i] + (1-l) * s[i-1]
    else:
        s[i] = s[i-1]
return s

```

+++?image="billeder/gregers-kronekant-ewma.jpg"

---
## Resultater

[Video](file:///home/gregers/Git/GregersP_presentations/assets/finderskeepers_animation.html)

Note:
Videoen viser, hvordan vi bestemmer våd kant, og kronekant.

+++=image="billeder/gregers---bredder.jpg"


+++?image="billeder/gregers---output.jpg"


+++?image="billeder/azz-bad-harddrive.jpeg"
300GB data


---?image="" 
<!-- billeder/sdfe-sindal-hoeje-maaleborde.jpg-->
## Tak

Gregers Hedegaard Petersen

gregers@septima.dk

<p>
<span>
<img border="0" src="https://raw.githubusercontent.com/bjornharrtell/presentations/master/assets/images/twitter.png" alt="Twitter">
</span>
<span>
<a href="https://twitter.com/GregersP">@GregersP</a>
</span>
</p>


---?image=""
### Kilder

- Data fra SDFE

Billeder fortrinsvis af:
- Hans Gregers Hedegaard Petersen
- Cecilie Hedegaard Petersen
- Søren Holm Pedersen, holmog.dk

+++?image=""
### Andre billeder
- ["Bailey-bro" - National Archives and Records Administration](https://da.wikipedia.org/)
- ["Stereoskop" - Friman](https://commons.wikimedia.org/wiki/File:Stereoskop.jpg)
- [NSA's "Center for Cryptologic History" in Boone](https://commons.wikimedia.org/wiki/File:HARVEST.jpg)
- ["Field of Streams" - Jasonanaggie](https://commons.wikimedia.org/wiki/File:Field_of_Streams_(6997132076).jpg)
- ["School lost and confused signpost" - Wonder woman0731, cc-by-2.0](https://www.flickr.com/photos/wildrose115/23173416364)
- ["Harddrive" - Azz bad, CC0](https://www.pexels.com/photo/analogue-business-close-up-computer-117729/)




---
## Ekstra

+++?video=billeder/asger---moelleaaen.mp4
## Mølleåen

+++?video=billeder/asger---tryggevaelde-aa.mp4
## Tryggevælde å


+++?image="billeder/gregers---missing-data-mose-transekter.png"


+++?image="billeder/gregers---mose-transekter.png"

+++?image="billeder/gregers---transekt-bro.png"

+++?image="billeder/gregers---transekt-plot-Uggerby-aa.png"

+++?image="billeder/sdfe-sindal-hoeje-maaleborde.jpg"
