Shell script feladatok:
 

Követelmények

A program működése feleljen meg a UNIX alapelveinek, amit kell, azt csinálja megbízhatóan, minden sallang nélkül. Ha nem tudja értelmezni argumentumait, akkor valami ehhez hasonló módon tájékoztasson:


$>ls -G
ls: Not a recognized flag: G
Usage: ls [-1ACFLNRabcdefgilmnopqrstux] [File...]
A *-gal jelölt feladatok kivételével minden feladatnak futnia kell UNIX és Debian alatt is. Használja a szabványos ki- és bemeneti fájlokat, a működésének ne legyenek mellékhatásai. (pl. ne hagyjon maga után szemetet, stb.). A programhoz szükséges minden inputot argumentumként adjon át, és a program ellenőrizze is le az összes megadott argumentumot. (darabszám, típus, stb.) A programhoz írjon rövid helpet (hívható legyen a programnév –h kapcsolóval), amirövid tájékoztatást ad a működésről, a szükséges argumentumokról, kapcsolókról, azok típusáról stb. Használjon „beszédes” változóneveket ésmegfelelő kommentárral lássa el a programot. (A megfelelő nem azt jelenti, hogy minden programsort 4 másikban magyaráz meg!) A próbák során ne vagy csak engedéllyel zavarjon másokat! Erre bizonyos feladatoknál külön is felhívjuk a figyelmet. Egyes feladatkiírások végén szerepel egy-egy példa arra, hogy a futó programnak milyen outputot kell produkálnia. Ha a feladatnév/feleadtszám után(... fo) szerepel, akkor a feladatot a megadott számú hallgatókból álló csoport is választhatja. (Ez nem kötelező, 1 hallgató is megoldhat 2-3 főre kiírt feladatot.)

1. HTML szintaktika ellenőrző
Írj egy html-szintaktika ellenőrző programot, mely ellenőrzi a nyitó illetve záró TAG-eket. A program próbálja megállapítani a hiba helyét! Ismerje a fontosabb TAG-eket, és ha hibás TAG-gel találkozik, kérdezze meg, hogy kijavítsa-e. Könnyen bővithető legyen új szintaktikai elemekkel. Ellenőrizze az argumentumban megadott file nevét is, és hogy létező, olvasható text file-e. pl.:


$>htmlell file
Hianyzik a </html>
Atnevezzem-e file.html -re?
I/N

2. C program szintaktika ellenőrző
Írj egy C program szintaktika ellenőrző programot, ami ellenőrzi az if, case stb. feltételek, elágazások szintaktikáját; továbbá a meghívott függvények meglévőségét; valamint a zárójelek ki illetve bezártságát. Az argumentumban megadott fájlnak létező, olvasható text-fájlnak kell lennie. Pl.:


$>cell file
Hibas a 25. sorban levo if

3. Filmfelirat konvertáló (3 fő)
Filmfelirat konvertáló és módosító program. Argumentumban megadott feliratfájl konverziót hajt végre, argumentumban megadott argumentum alapján. Képes legyen kétfajta felirat közül oda-vissza konvertálni (srt-sub), valamint a subot nyújtani-zsugorítani, tolni, valamint két tetszőlegesen megadott sor alapján (célszerűen az elejéről és a végéről) átszámolni az összes többi sort. Az fps-t (frame per secundum) kérje be. Az első argumentum a konverzió típusát határozza meg, utána a konvertálandó feliratfájlt adjuk meg, amit ellenőrizni kell (létező, olvasható textfájl legyen). A harmadik argumentum a módosítás mértéke (ha szükséges). Utolsó argumentum a kimeneti file legyen. Ez az argumentum opcionális, ha nincs megadva, akkor az output fájl neve legyen az input fájlnév egy "uj" szócskával kiegészítve. Ahol argumentumként számot vár ellenőrizzük, hogy valóban szám legyen. Pl1.:


$>felirat konv dune.srt
$>cat dune.srt

1
00:01:11,840 --> 00:01:13,280
Arrakis.

2
00:01:13,680 --> 00:01:14,800
Dűne.

$>cat dune.sub
{1796}{1832}Arrakis.
{1842}{1870}Dűne.
Pl2.:


$>felirat tol felirat.sub -2
2 sec tol viszafele (output file: feliratuj.sub)
Pl3.:


$> felirat nyujt felirat.sub 1.18
nyujtja a feliratot 1.18 szorosára. (29.5/25) (output file: feliratuj.sub)
Pl4.:


$> felirat igazit felirat.sub modosit
$> cat felirat.sub

{1796}{1832}Arrakis.
{1842}{1870}Dűne.
....
{90012}{90045}Örömmel.

$> cat modosit
{1821}{1857}Arrakis.
{106239}{106278}Örömmel.

$> cat feliratuj.sub     	(úgy nyújtja és tolja, hogy a két sor megegyezzen, a többi)
{1821}{1857}Arrakis.    	(pedig hozzá igazodik)
{2189}{2231}Dűne.
....
{106239}{106278}Örömmel.

4. Bejelentkezési statisztika
Argumentumban adott felhasználó bejelentkezéseiről ad információt. Legutolsó bejelentkezése, mikor, honnan történt, összesen mennyi időt töltött bent, bejelentkezésenként átlagosan mennyi időt töltött bent, naponta átlag hányszor jelentkezik be, és naponta átlagosan mennyi időt tölt el azon a gépen. Írja ki azt a 10 gépet, ahonnan a legtöbb bejelentkezése történt. Ha dátumot adunk meg argumentumnak, akkor kiírja, hogy abban az időpontban kik voltak bejelentkezve (loginnév + teljes név formában).


Pl1.:

$>bejelent user1
$>Utolso bejelentkezés: Mar 05 15:45 - 15:49
gépnév: nec21.iit.uni-miskolc.hu

...
Pl2.:


$>bejelent 03:05:15:46

Marcius 5.-én 15 óra 46 perckor bent tartózkodott:

user1	Kis Miska
user2	Nagy Góliát

...

5. Naptár
Írj egy programot, ami emlékeztetőként kiírja az argumentumban megadott dátumon lévő névnapot, paraméter nélkül indítva az aktuális napra vonatkozik. Továbbá előre meghatározott napra előre szól, hogy valami fontos esemény lesz hh.nn dátumon. Célszerűen 12 fájlba szervezve, soronként megadni a napokat, az egyes mezőkben a névnapok, születésnapok, egyéb események felsorolása, amennyiben nem egy nappal előre kérjük az emlékeztetést, akkor speciális karakterek közé zárva, hogy hány napra előre. Példa az adatfájlra:


$>cat jun

1:Tunde
2:Kármen:Anita:Brigi szuletesnapja! {3} 
....
(3 nappal előre jelzi a 2.-ai születésnapot, és 2.-án a két névnapot is)

6. Tantárgynapló
Írj tantárgynapló programot, ami egyik fájlban a tantárgyakat tartja nyilván, a másik fájlban a nevet és tankört, valamint a tárgyak eredményeit az előző fájlban meghatározott sorrend szerint. A "rekordok" névsor szerint legyenek rendezve. Egy egyszerű menüvel lehessen lekérdezni, új adatot felvinni, törölni, ill. módosítani, valamint átlagot számolni. Így nézhet ki például az egyik adatfájl egy sora:


$> cat adatok
Kiss Janos:G-111:2:3:4:5:3:2:5:2:3:4:5

7. Sin – cos számítás
Írj programot, ami argumentumban megadott számnak kiszámolja a szinuszát, illetve koszinuszát, Taylor sorbafejtéssel. Harmadik argumentumban megadható legyen a sorbafejtésnél figyelembe vett tagok száma. Ez alapértelmezettként 3. Pl.:


$>szog sin 30 5
sin 30 fok = …

8. Arcsin –arccos számítás
Írj programot, ami argumentumban megadott számnak kiszámolja az arcus sinusat illetve arccosinusat, Taylor sorbafejtéssel Harmadik argumentumban megadható legyen a sorbafejtésnél figyelembe vett tagok száma. Ez alapértelmezettként 3. Pl.:


$>szog arcsin 0.5 5
arcsin 30 fok = …

9. Sh – ch számítás
Írj programot, ami argumentumban megadott számnak kiszámolja a sh-ját illetve ch -ját, Taylor sorbafejtéssel. Harmadik argumentumban megadható legyen a sorbafejtésnél figyelembe vett tagok száma. Ez alapértelmezettként 3. Pl.:


$>szog ch 30 5
ch 30 fok = x

10. Családfa
Írj programot, amely családfát tart nyilván. Mindenkiről tartsa nyilván az alábbi adatait: születési idő/hely), halálozási idő, lakcím, anyja, apja, gyerekei neve, felesége(i)/férje(i) neve (többszöri házasságot is tudjon kezelni). Célszerűen minden személyt egyedi azonosítóval érdemes ellátni. Egyszerű menüvel lehessen nézegetni az adatokat. Egyszerre egy egyénről írjon ki minden információt. A program elindítása után a fájlban az első egyént listázza ki elsőnek. Különböző billentyűk lenyomására lehet a többi adatot megtekinteni. (pl.: "a" billentyű lenyomására az egyén anyja, "1" billentyű lenyomására az első gyermeke, "f" férj/feleség stb….). Ezekről az egyénekről is le lehessen kérni az összes meglévő adatot. A program tegye lehetővé a keresést az adatbázisban. Egyéni ötlet alapján több adatot is kezelhet. Pl.:


$>csalad

Név:Kiss János
Anyja neve:Nagy Borbala
Apja neve:Kiss Bela
Szuletett:1912.12.12. Kisnagyfalva
Lakcim:9876. Nagykisfalva, Kisvasut ut. 11
Felesége neve:Nagy Krisztina
1. gyereke neve: Kiss Krisztina
2. gyereke neve: Kiss Borbala
3. gyereke neve: Kiss Miklos
11. Egyszerű levelező kliens
Készítsen olyan shell programot, amely egy primitív levelező klienst valósít meg. A programban menün keresztül legyen lehetőség levelek olvasására, egy adott levél megválaszolására, és új levél írására. A program a levelek olvasásakor írja ki az összes kapott levél feladóját, és ez alapján legyen lehetőség a levelet elolvasni, illetve válaszolni a levélre. A levélküldésnél legyen lehetőség megadni a címzettet, a levél címét, csatolt fájlokat és természetesen a levél szövegét.

12. Figyelő-program
Készítsen olyan sh scriptet, amely a háttérben futva figyelni, hogy ki lépett be a rendszerbe. A program használjon egy fájlt, mely tartalmazza a figyelni kívánt felhasználók loginnevét. Ha az adott user belép, akkor egy pop-up ablakban jelenjen meg, hogy az illető belépett, ezen felül az is kerüljön kiírásra, hogy melyik gépre jelentkezett be, és az hogy mikor tette ezt pontosan.

13. Log fájl elemző
A sh program tudjon legalább 2 típusú log fájlt elemezni és olvashatóbb formában kiírni. Kapcsolón keresztül lehessen a típusok között választani. A két típus legyen például: apache.log és egy apache error.log.

14. Hírfeldolgozás
Az sh script legalább 3 weboldalról gyűjtse össze a hírek főcímét (linkjét) és írja ki a híreket olyan formában, hogy forrás : hír Lehetőség szerint a forrást más színnel jelenítse meg

15. C daraboló (2 fo)
A sh program adott C forrást tudjon feldarabolni a házi szabványnak megfelelően és készítsen hozzá Makefile-t is. A C forrás feldarabolásra vonatkozó szabályokat a házi szabványban lehet elolvasni. Tehát a függvények a main kivételével kerüljenek külön fájlba, és készüljön egy olyan Makefile is, ami gondoskodik a fordításról linkelésről stb.

16. Levél figyelő
Az sh alkalmazás a háttérben futva figyeli a felhasználó mailbox-át, és ha új levele érkezik egy pop-up window-ba (jelenjen meg) írja ki, hogy levele érkezett. Írja ki, hogy kitől és hogy mikor. Legyen lehetőség egy mail kliens indítására is.

17. Debian csomagok listája *
Debian alatt kérdezze le, mely csomagok vannak telepítve a gépre, írja ki ezen csomagok nevét formázottan, valamint azt is írja ki a program, hogy mely programokkal van függőségben egy adott csomag. Pl.


nparted : libc6, libnewt0, libparted1.4, libuuid1
nano	: libc6, libncurses5

18. Levél Script (2 fő)
A program háttérben futva figyelje a beérkező leveleket, ha a levél subject-je egy bizonyos előre (argumentumban) megadott szöveg, akkor a levél tartalmát az sh shell scriptnek veszi, azt végrehajtja, az outputját pedig elkapva visszaküldi a feladónak. A próbák során ne zavarjon másokat!

19. Deriválás (2 fő)
Írj programot, ami argumentumban megadott kifejezésnek kiszámolja a deriváltját. A program tudja kezelni az alábbi műveleteket, fogalmakat: osztás, szorzás, polinomok, sin, cos, zárójelezés. Pl:


     $>deriv sin^2((x^2-3x-5)/4)

     $>0.5*sin((x^2-3x-5)/4)*(2x-6)

     $>deriv sin^2((x^2-3x-5)/4)*cos(x^3-1)
     
20. Körlevélküldés
A program tegyen lehetővé egy egyszerű körlevélküldést. A címlistát egy (megfelelő szerkezetű) adatfájlból vegye a program. Az elküldendő levélben speciális karakterek jelölik a kiegészítendő részeket. A megfelelően megírt mintaállományba a program a felhasználói nevektől függően helyettesít be szövegrészeket. A próbák során ne zavarjon másokat!


$>cat
mintalevel.1

Kedves ##1##!

A …….. ##2##…..

….


$>cat lista.1
user1@valahol.van.hu    Szabo Pal    febr.24.
user2@……


$>korlev
mintalevel.1 lista.1

21. Fájlkereső
A program valósítson meg fájlkeresést. Mondja meg a keresett fájlról, hogy létezik-e, mi a típusa, mérete és ki a tulajdonosa. A program először egy adatbázisban keres, amennyiben ott nem találja a keresett fájlt, akkor a teljes fájlrendszert végignézi. (Az adatfájl elérési útvonalakat tartalmaz.) A keresés eredményének megfelelően bővítse az adatbázist. A program tegye lehetővé az adatbázis explicit bővítését is, például a script valamilyen (pl. –u) kapcsolóval való meghívásával.


$>fkeres myfile
$>A file eleresi utvonala:/etc/usr/bin/group1/valaki3/myfile
Tipusa: ascii text
Tulajdonosa: Buga Jakab
Merete: 4588 bytes


22. Számológép
A shell script valósítsa meg egy számológép funkcióit. Végre tudja hajtani az alábbi műveleteket: összeadás, kivonás, osztás, szorzás, hatványozás, gyökvonás (nem csak négyzetgyök!). Tudjon értelmezni zárójeles kifejezéseket, és jelezze, ha szintaktikai hiba van a megadott argumentumban. Pl.:


$>calc
(33.45/(78*(12.5))
Zarojelezesi hiba! Kerem ellenorizze a nyito es zaro zarojeleket!

$>calc
(33.45^3-(57-3.2)/(78*(12.5^(-1.2))))
37413

23. Bejelentkezési statisztika 2.
A shell script szűrje a last parancs eredményét, és írja ki hallgatókat csökkenő/növekvő sorrendben az alapján, hogy hányszor jelentkeztek be. Egy másik kapcsolóval azt írja ki, hogy mennyi időt töltöttek el összesen az adott gépen (szintén növekvő/csökkenő sorrendben listázva). Meg lehessen adni, hogy hány darab felhasználót listázzon ki. Pl.:


$>gepido -p n 2
user1    Kiss Jozsef	25    login
user2    Nagy Pal     	23    login

$>gepido -t cs 2
login    name           day:hour:min    min
user2    Nagy Pal     	01:22:18        3778
user1    Kiss Jozsef    01:12:36        3296


24. Levelezőlista
A shell script automatikusan továbbítsa a beérkező leveleket a levelezési listára feliratkozott felhasználóknak. Valósítsa meg az automatikus fel- és leiratkozásokat is. A próbák során ne zavarjon másokat!

25. Szamrendszerek kozotti konvertalas
A parameterkent kapott szamot valtsa at 2-es, 8-as, 10-es vagy 16-os szamrendszerbe. A forras es cel szamrendszert kapcsolokkal lehessen megadni. Jelezze ha ervenytelen a megadott szam az adott szamrendszerben. A hibakat jelezze, pl. nem megfelelo parameterezes, stb. Legyen alapertelmezett forras es cel szamrendszer. Pl.:


&./szamvalt.sh -f 2 -c 10 1001
9
&./szamvalt.sh -f 16 -c 10 FF
255
&./szamvalt.sh -f 10 -c 16 127
7F

26. Felhasznalo menedzsment
A shell script az argumentumkent kapott parancs alapjan ertelmezze a tobbi parameteret. A parancs lehet listazas, hozzaadas, torles, zarolas, engedelyezes, jelszovaltas, shellvaltas. A felhasznalokat egy fileban tarolja, olyan strukturaban, mint az /etc/passwd file UNIX rendszereken. Hozzadaskor a szukseges adatok: felhasznalonev, valos nev, homedir, shell, jelszo. Ha valamit nem adott meg argumentumkent, akkor azt kerje be a script. A jelszo-t hashelni kell (DES vagy MD5)! A felhasznaloi (uid) es csoport azonositokat (gid) 1000-tol kezdve ossza ki mindenkinek egy egyedit. Torleshez a felhasznalonevet kelljen megadni. Zarolasnal a jelszo hash ele egy * keruljon. Minden tranzakciot naplozzon egy kulon fileba! pl: felhasznalok.db file egy sora:


kamm:$1$9ZiP3z2a$U5Tbm7l.2Rn2ZlnCeK1Ma0:1000:1000:kamm,,,:/home/kamm:/bin/bash


27. Menetrend
Mondja meg a script, hogy mikor indul a legkozelebbi harom 22-es illetve 31-es busz az egyetemrol. Parameterkent lehessen megadni tetszoleges idopontot, olyankor ahhoz viszonyitson ne az aktualis idohoz. Kezelje le azt az esetet is ha mar csak masnap hajnalban indul busz. Illetve adjon tanacsot, hogy elerjuk-e a buszt, attol fuggoen, hogy hol vagyunk. A tartozkodasi helyunket is parameterkent kapja a szkript, legalabb a kovektezo heylszineket ismerje a program: "infoban", "rockyban", "menzan", "rockybanittasan", "koliban". Ha idopontnak "frissites"-t adunk meg, akkor a menetrend frissuljon webrol (mvkzrt.hu)!

28. Kozos koltseg nyilvantarto
Kepzeld magad Vagasi Feri helyebe es irj Kutya ur szamara egy olyan shell scriptet, ami segiti ot kozos koltseg nyilvtantartasaban. A shell script az argumentumkent kapott parancs alapjan ertelmezze a tobbi parameteret. A parancs lehet listazas, hozzaadas, torles, modositas, ujhonap. A neveketfelhasznalokat egy fileban tarolja, olyan strukturaban, mint az /etc/passwd file UNIX rendszereken. Hozzadaskor a szukseges adatok: nev, lakas szama, melyik honap, egyenleg. Modositani lehessen barmelyik adatot, es a lakas szam alapjan lehessen hivatkozni a bejegyzesekre. Torles hasonlokeppen. Listanal irja ki a lakok adatait es, hogy az eddigi honapokban mennyi volt a kozos koltseg, befizettek-e, van-e tartozasuk. "ujhonap" parancsnal lehet hozzadni minden lakonak az uj havi kozos koltseg osszeget.

28. APEH-szimulator
Keszits shell scriptet maganszemelyek adojanak kiszamitasahoz. Kerje be a rendszeres brutto havi jovedelmet, egyeb brutto jovedelmet, es az esetleges osztondijat/szoctam-ot. Ezek alapjan szamitsa, ki, hogy mennyi jarulekot es adot kell fizetnie. Az SZJA 18%, ha az eves brutto jovedelem 1.700.000 HUF felett van akkor 1.700.000-nek a 18% es a fele eso resz 36%-a az SZJA. Az osztondij/szoctam/stb. adomentes, de az adoalapot noveli (gyk. az 1.700.000-be beleszamit). A munkavallaloi jarulek: 1.5%, a magannyugdijpenztar: 8%, penzbeli eu jarulek: 2%, egeszsegbiztositai jarulek: 4%, nyugdij jarulek: 1.5%. A maradek a netto. Evi 1.400.000 HUF jovedelem alatt adojovairas veheto igenybe, ennek osszege havi (ezt kerje be szinten) max 9000 HUF, tehat -9000 HUF/ho SZJA ha teljesul a feltetel.
Ugyanezt forditva is tudja, hogy netto jovedelmet adunk meg, es abbol kiszamolja mennyi a brutto (osztondijat nyilvan nem) es az egyeb jarulekokat/adokat. Ezt a viselkedest a -n kapcsoloval lehessen elohozni.
