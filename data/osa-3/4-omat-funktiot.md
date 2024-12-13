---
path: '/osa-3/4-omat-funktiot'
title: 'Omat funktiot'
hidden: false
---

<text-box variant='learningObjectives' name='Oppimistavoitteet'>

Tämän osion jälkeen

- Osaat luoda oman funktion ja kutsua sitä
- Ymmärrät, mikä on funktion parametri
- Osaat käyttää parametreja omissa funktioissa

</text-box>

Aikaisemmissa osissa on käytetty esimerkiksi funktioita `len`, `print` ja `input` eri tarkoituksiin. Nämä ovat Pythonin sisäänrakennettuja funktioita, mutta voimme myös määritellä omia funktioita.

## Funktion määrittely

Oma funktio määritellään avainsanalla `def` (lyhenne sanasta define). Funktiolle annetaan jokin _nimi_, jonka jälkeen on alku- ja loppusulku. Tämän jälkeen annetaan lohkossa funktioon kuuluva koodi.

Esimerkiksi seuraava koodi määrittelee funktion `viesti`:

```python
def viesti():
    print("Tämä on oma funktio!")
```

Jos yllä oleva ohjelma suoritetaan, se ei näytä tekevän mitään. Tämä johtuu siitä, että funktion sisältämä koodi suoritetaan vasta silloin, kun funktiota _kutsutaan_.

Funktion kutsuminen tapahtuu funktion nimellä. Esimerkiksi seuraava koodi kutsuu funktiota:

```python
def viesti():
    print("Tämä on oma funktio!")

viesti()
```

<sample-output>

Tämä on oma funktio!

</sample-output>

Samaa funktiota voidaan määrittelyn jälkeen kutsua useita kertoja.

```python
def viesti():
    print("Tämä on oma funktio!")

viesti()
viesti()
viesti()
```

<sample-output>

Tämä on oma funktio!
Tämä on oma funktio!
Tämä on oma funktio!

</sample-output>

<text-box variant='hint' name='Omien funktioiden testaaminen'>

Huom! Tästä eteenpäin valtaosassa kurssin tehtäviä pyydetään kirjoittamaan oma funktio (tai funktioita).

Kun ohjelma koostuu pelkästään funktiosta, ei sen suorittaminen näytä tekevän mitään. Esimerkiksi seuraava ohjelma ei tulosta mitään:

```python
def moikkaa():
    print("Moi!")
```

Funktion `moikkaa` sisällä oleva koodi suoritetaan vasta, kun funktiota kutsutaan.

Funktion alla olevaan "pääohjelmaan" kannattaa siis kirjoittaa sopivia funktiokutsuja ohjelman testaamiseksi, esimerkiksi:

```python
def moikkaa():
    print("Moi!")

# Pääohjelma on se ohjelman osa, joka ei ole minkään funktion sisällä
# Kutsutaan omaa funktiota

moikkaa()
```

**Tärkeä huomio**: kurssin tehtävien testit edellyttävät, että funktioita testaava pääohjelma tulee kirjoittaa seuraavasti määriteltyyn `if`-lohkoon:

```python
def moikkaa():
    print("Moi!")

# Kirjoita pääohjelma aina seuraavanlaisen lohkon sisälle
if __name__ == "__main__":
    moikkaa()
```

Lohkon ulkopuolelle jätetty testikoodi aiheuttaa seuraavan virheilmoituksen:

<img src="3_4_1.png">

Kannattaa myös huomata, että testit eivät suorita `if __name__ == "__main__"` -lohkon sisälle kirjoitettua koodia eikä sinne tule sijoittaa tehtävien edellyttämää koodia.

</text-box>

<in-browser-programming-exercise name="Seitsemän veljestä" tmcname="osa03-21_seitseman_veljesta">

Tee funktio `seitseman_veljesta` jonka kutsuminen tulostaa seitsemän veljeksen nimet aakkosjärjestyksessä:

<sample-output>

Aapo
Eero
Juhani
Lauri
Simeoni
Timo
Tuomas

</sample-output>

</in-browser-programming-exercise>

## Funktion parametri

Usein funktiolla on yksi tai useampi _parametri_, jolla sen toimintaan voi vaikuttaa. Esimerkiksi Pythonin valmiissa funktioissa `print` ja `input` parametrin avulla annetaan näytettävä teksti:

```python
print("Hei!")                     # parametrina merkkijono "Hei!"
nimi = input("Kerro nimesi: ")    # parametrina merkkijono "Kerro nimesi: "
print(nimi)                       # parametrina muuttujan nimi arvo
```

Voimme määritellä parametreja myös omille funktioillemme. Parametrit määritellään funktion nimen jälkeen olevien sulkujen sisällä:

```python
def tervehdi(kohde):
    print("Hei", kohde)
```

Jos funktiota kutsutaan kaksi kertaa

```python
tervehdi("Emilia")
tervehdi("maailma!")
```

tulostaa se kaksi erilaista tervehdystä:

<sample-output>

Hei Emilia
Hei maailma!

</sample-output>

Katsotaan funktion määrittelyä vielä tarkemmin:

```python
def tervehdi(kohde):
    print("Hei", kohde)
```

Määrittelimme ensimmäisellä rivillä, että funktion parametri on nimeltään `kohde`. Toisella rivillä `print`-komento käyttää parametrissa `kohde` olevaa arvoa.

Kun funktiota kutsutaan, saa parametri _funktiokutsussa_ annettavan arvon. Esimerkiksi kun kutsutaan

```python
nimi = "Antti"
tervehdi(nimi)
```

niin parametrin `kohde` arvo funktiossa on merkkijono `Antti`.

Funktioiden ja parametrien nimeämistä koskevat samat periaatteet kuin mitä olemme jo aiemmin käsitelleet, eli nimien kannattaa olla kuvaavia ja käytössä ovat ensisijaisesti pienet kirjaimet sekä alaviiva.

<in-browser-programming-exercise name="Ensimmäinen merkki" tmcname="osa03-22_ensimmainen_merkki">

Täydennä koodipohjassa oleva funktio `ensimmainen` siten, että se tulostaa parametrinaan saamansa merkkijonon ensimmäisen merkin.

```python
def ensimmainen(merkkijono):
     # kirjoita koodia tähän

# kokeillaan funktiota:
if __name__ == "__main__":
    ensimmainen('python')
    ensimmainen('yhtälö')
    ensimmainen('tieto')
    ensimmainen('huominen')
    ensimmainen('omena')
    ensimmainen('nukkumaanmenoaika')
```

<sample-output>

p
y
t
h
o
n

</sample-output>

</in-browser-programming-exercise>

<text-box variant='hint' name='Omien funktioiden testaaminen: parametrit'>

Kun omassa funktiossa on määritelty yksi tai useampia parametreja, kannattaa funktiota testata usealla erilaisella parametrilla.

Kannattaa erityisesti miettiä, toimivatko myös "erikoistapaukset": mitä funktio esimerkiksi tekee, jos sille annetaan negatiivinen luku tai liukuluku kokonaisluvun sijasta.

Jos tehtävänannossa ei ole erityisesti käsketty kirjoittamaan tiettyjä funktiokutsuja, voit vapaasti lisätä omia kutsujasi pääohjelmaan ja testit jättävät nämä huomiotta.

</text-box>

## Lisää esimerkkejä

Katsotaan vielä pari muuta esimerkkiä parametrien käyttämisestä. Seuraavassa funktiossa parametri on luku:

```python
def nelio(x):
    print(f"Luvun {x} neliö on {x * x}")

nelio(2)
nelio(5)
```

<sample-output>

Luvun 2 neliö on 4
Luvun 5 neliö on 25

</sample-output>

Seuraavassa esimerkissä funktion sisällä on ehtorakenne:

```python
def tervehdi(nimi):
    if nimi == "Emilia":
        print("Heippa,", nimi)
    else:
        print("Moikka,", nimi)

tervehdi("Emilia")
tervehdi("Matti")
```

<sample-output>

Heippa, Emilia
Moikka, Matti

</sample-output>

Seuraavassa funktiossa puolestaan on kaksi parametria:

```python
def summa(x, y):
    tulos = x + y
    print(f"Parametrien {x} ja {y} summa on {tulos} ")

summa(1, 2)
summa(5, 24)
```

<sample-output>

Parametrien 1 ja 2 summa on 3
Parametrien 5 ja 24 summa on 29

</sample-output>

Funktio myös määrittelee "apumuuttujan" _tulos_, mihin se sijoittaa parametriensa summan.

Huomaa, että parametrien nimillä ei ole mitään tekemistä funktion ulkopuolella olevien muuttujien kanssa. Esimerkiksi jos kutsumme äskeistä funktiota

```python
x = 100
y = 30
summa(1, 2)
summa(x + y, 10)
```

niin tuloksena on:

<sample-output>

Parametrien 1 ja 2 summa on 3
Parametrien 130 ja 10 summa on 140

</sample-output>

Ensimmäisessä kutsussa parametrien arvot funktion sisällä ovat `x = 1` ja `y = 2`, ja toisessa kutsussa arvot ovat `x = 130` ja `y = 10`.

Palaamme funktioihin ja parametrien määrittelyyn tarkemmin seuraavan osan alussa.

<!--vastaava varoitusteksti löytyy osioista 3-4, 4-6 ja 5-1, tsekkaa kaikki jos muokkaat tätä-->
## Varoitus: globaalin muuttujan käyttö funktion sisällä

Kuten olemme nähneet, funktioiden sisällä on mahdollista määritellä muuttujia. Kannattaa myös huomata se, että funktio näkee sen ulkopuolella eli pääohjelmassa määritellyt muuttujat. Tälläisia muuttujia sanotaan _globaaleiksi_ muuttujiksi.

Globaalien muuttujien käyttämistä funktioista käsin ei useimmiten pidetä hyvänä asiana muun muassa siksi, että ne saattavat johtaa ikäviin bugeihin.

Seuraavassa on esimerkki funktiosta, joka käyttää "vahingossa" globaalia muuttujaa:

```python
# globaali muuttuja
nimi = "Emilia"

def tervehdi(etunimi):
    # tulostetaan vahingossa parametrin sijaan globaalin muuttujan arvo
    print("Hei", nimi)

tervehdi("Antti")
tervehdi("Emilia")
```

<sample-output>

Hei Emilia
Hei Emilia

</sample-output>

Vaikka funktiota kutsutaan oikein, se tulostaa aina globaalissa muuttujassa olevan nimen _Emilia_.

<in-browser-programming-exercise name="Keskiarvo" tmcname="osa03-25_keskiarvo">

Tee funktio `keskiarvo`, joka saa parametrina kolme kokonaislukua. Funktio tulostaa parametriensa keskiarvon.

```python
keskiarvo(5, 3, 1)
keskiarvo(10, 1, 1)
```

<sample-output>

3.0
4.0

</sample-output>

</in-browser-programming-exercise>

<in-browser-programming-exercise name="Monta tulostusta" tmcname="osa03-24_monta_tulostusta">

Tee funktio `tulosta_monesti(merkkijono, kertaa)`, joka saa parametriksi merkkijonon sekä kokonaisluvun, joka kertoo, montako kertaa funktion tulee tulostaa parametrina saamansa merkkijono:

```python
tulosta_monesti("hei", 5)

print()

merkkijono = "Alussa olivat suo, kuokka ja Python"
kertaa = 3
tulosta_monesti(merkkijono, kertaa)
```
<sample-output>

hei
hei
hei
hei
hei

Alussa olivat suo, kuokka ja Python.
Alussa olivat suo, kuokka ja Python.
Alussa olivat suo, kuokka ja Python.

</sample-output>

</in-browser-programming-exercise>

<in-browser-programming-exercise name="Risuneliö" tmcname="osa03-23_risunelio">

Tee funktio `risunelio(pituus)` joka saa parametriksi kokonaisluvun, joka kertoo kuinka suuri risuneliö funktion pitää tulostaa:

```python
risunelio(3)
print()
risunelio(5)
```

<sample-output>

<pre>
###
###
###

#####
#####
#####
#####
#####
</pre>

</sample-output>

</in-browser-programming-exercise>

<in-browser-programming-exercise name="Shakkilauta" tmcname="osa03-26_shakkilauta">

Tee funktio `shakkilauta`, joka tulostaa shakkilaudan numeroista 0 ja 1 alla olevien esimerkkien mukaisesti.

```python
shakkilauta(3)
print()
shakkilauta(6)
```

<sample-output>

<pre>
101
010
101

101010
010101
101010
010101
101010
010101
</pre>

</sample-output>

</in-browser-programming-exercise>


<in-browser-programming-exercise name="Sananeliö" tmcname="osa03-27_sananelio">

Tee funktio `nelio`, joka tulostaa sananeliön alla olevien esimerkkien mukaisesti.

```python
nelio("ab", 3)
print()
nelio("aybabtu", 5)
```

<sample-output>

<pre>
aba
bab
aba

aybab
tuayb
abtua
ybabt
uayba
</pre>

</sample-output>

</in-browser-programming-exercise>

<quiz id="b5866baa-9190-5183-89ca-a27fc39768f8"></quiz>

Vastaa lopuksi osion loppukyselyyn:

<quiz id="ec2420d8-a5d7-5020-9d37-b6ff51f15319"></quiz>
