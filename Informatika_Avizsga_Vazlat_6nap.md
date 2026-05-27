# 🖥️ Informatika Ágazati Alapvizsga – 6 Napos Tanulási Vázlat

> **Hogyan használd ezt a vázlatot?**
> Minden nap olvasd el az adott részt, majd feddd le és mondd el fejből a főbb pontokat.
> A **félkövér** szavak a legfontosabb fogalmak – ezeket mindenképpen tudd!

---

# 📅 1. NAP – Alapfogalmak: Neumann-elvek, Hardver, Firmware, BIOS/UEFI

---

## 1.1 Neumann-elvek (a modern számítógépek alapja)

A mai számítógépek mind az úgynevezett **Neumann-architektúra** szerint épülnek fel.
Az elveket John von Neumann fektette le az 1940-es években.

**Az 5 Neumann-elv:**

1. **Teljesen elektronikus működés** – a számítógép elektronikus alkatrészekből áll, mechanikus elemek nélkül
2. **Kettes számrendszer (bináris)** – az adatokat és utasításokat 0-ás és 1-es jelekkel tárolja és dolgozza fel
3. **Belső programtárolás** – a program utasításai a memóriában vannak tárolva (nem kapcsolókon vagy lyukszalagon)
4. **Soros utasítás-végrehajtás** – az utasítások egymás után hajtódnak végre (sorban)
5. **Univerzálisság** – ugyanaz a gép különféle feladatokra képes, csak a programot kell cserélni

**A Neumann-architektúra fő egységei:**
- **CPU** (Central Processing Unit) – a számítógép „agya", feldolgozza az utasításokat
- **Memória (RAM)** – az adatok és programok ideiglenes tárolója
- **Beviteli egységek** – pl. billentyűzet, egér
- **Kiviteli egységek** – pl. monitor, nyomtató
- **Háttértár** – pl. merevlemez (tartós tárolás)

---

## 1.2 Hardver fogalma

**Hardver:** a számítógép fizikailag megfogható részei.

Egy személyi számítógép főbb hardverelemei:
- Ház és tápegység
- Alaplap, processzor, memória
- Bővítőkártyák (videokártya, hangkártya, hálózati kártya)
- Háttértárak (merevlemez, DVD-meghajtó)
- Külső perifériák

---

## 1.3 Firmware fogalma

**Firmware:** a hardverekbe gyártók által beépített szoftver.
- Olyan rögzített, kisméretű program, amely elektronikai eszközök vezérlését végzi
- Példák: távirányító, merevlemez, billentyűzet, mobiltelefonok, fényképezőgépek
- **Nincs éles határ** a firmware és a szoftver között
- Az alacsonyabb szintű firmware-ek **ROM**-ban vagy **PLA**-ban tárolódnak
- A magasabb szintű firmware-ek **flash memóriában** tárolódnak → frissíthetők
- Feladata: az eszköz alapvető működését biztosítja – nélküle az eszköz teljesen működésképtelen

---

## 1.4 BIOS és UEFI

### BIOS (Basic Input-Output System)

- A 70-es évek közepén vezették be
- **Alacsony szintű szoftver** az alaplapi chipen
- Felelős: hardverkomponensek ébresztéséért, megfelelő működéséért
- Indításkor a BIOS betöltődik és elindítja az operációs rendszert
- A 90-es évekig ROM-ban tárolták (nem volt módosítható), ma **EEPROM / flash memória**
- Beállításait a **CMOS RAM** tárolja (CR2032 gombelem táplálja)

**BIOS főbb beállításai:** hardverkonfiguráció, rendszeridő, rendszerindítási sorrend

**POST (Power-On Self Test):**
- Az operációs rendszer indítása előtt a BIOS elvégzi a POST-ot
- Ellenőrzi, hogy a hardver érvényes-e és megfelelően működik-e
- Ha hiba van: hibaüzenet vagy hangjelzéssorozat
- Utána a BIOS megkeresi a **Master Boot Record-ot (MBR)** a rendszerindító eszközön

**Miért elavult a BIOS?**
- Nem támogatja a 2,2 TB-nál nagyobb HDD-ket
- Nem támogatja a PCI-Express 3.0-t
- Billentyűzettel kell navigálni, alacsony felbontású menü
- Lassú indítás

### UEFI (Unified Extensible Firmware Interface)

- Az Intel 1998-ban kezdte fejleszteni EFI (Extensible Firmware Interface) névvel
- 2007-ben az Intel, AMD, Microsoft és más gyártók egységesítették → UEFI
- **A mai számítógépek túlnyomó többsége UEFI-t használ**

**UEFI előnyei a BIOS-szal szemben:**
1. **Könnyű kezelhetőség** – grafikus felület, egérrel navigálható, kezdő és haladó mód
2. **Átjárhatóság** – webes felületről is elérhető, mobilról is kezelhető
3. **Windows 8/10 támogatás** – Microsoft az UEFI-t helyezte előtérbe
4. **Gyorsabb végrehajtás** – akár 10 másodperc alatt bootol (SSD-vel)

**UEFI technikai adatok:**
- 2 TB-nál nagyobb meghajtókról is bootolható (elméleti korlát: 9,4 zettabájt)
- GPT partíciós rendszert használ (MBR helyett)
- 32 bites vagy 64 bites módban futtatható
- Támogatja a **Biztonságos rendszerindítást (Secure Boot)**

---

# 📅 2. NAP – Alaplap, Processzor, RAM, Hűtés

---

## 2.1 Az Alaplap

**Alaplap:** a számítógép elsődleges, központi áramköri lapkája.
- Többrétegű nyomtatott áramköri lap (NYÁK)
- Meghatározza: milyen processzor, RAM, bővítőkártyák illeszthetők be
- Szabvány: **ATX** (leggyakoribb)

**Az alaplap főbb komponensei:**

| Komponens | Funkció |
|-----------|---------|
| **Processzor foglalat (CPU socket)** | A CPU ide csatlakozik (LGA vagy PGA) |
| **RAM foglalatok (DIMM)** | A memóriamodulok helye |
| **Északi híd (North Bridge)** | Memóriavezérlés, PCI/PCIe kezelése (ma már a CPU-ban van) |
| **Déli híd (South Bridge)** | Tárolók (HDD/SSD), USB portok vezérlése |
| **ROM BIOS chip** | A BIOS/UEFI firmware tárolója |
| **CMOS RAM** | BIOS beállítások tárolója (gombelem táplálja) |
| **SATA portok** | Tárolóeszközök csatlakoztatása (3 Gbps vagy 6 Gbps) |
| **PCI Express foglalatok** | Videokártya, hangkártya, hálózati kártya helye |
| **24 tűs ATX tápcsatlakozó** | A tápegység fő csatlakozója (3,3V, 5V, 12V) |
| **Gombelem (CR2032)** | A CMOS RAM és az óra tápellátása kikapcsolt állapotban |
| **Órajel generátor** | Ütemezi a számítógép működését (mint egy metronóm) |

**Hátlapi csatlakozók (ATX szabvány):**
- PS/2 (lila: billentyűzet, zöld: egér)
- 2–4 USB port
- 3,5 mm-es jack hangcsatlakozók
- RJ-45 (hálózat)
- D-SUB, DVI, HDMI, DisplayPort (ha van integrált VGA)

---

## 2.2 Processzor (CPU)

**CPU (Central Processing Unit):** a számítógép „agya".
- A legtöbb számítási művelet itt megy végbe
- Gyártók: **Intel, AMD**

### Processzor tokozása és foglalata

- **PGA (Pin Grid Array):** az érintkezők a processzoron vannak → ZIF foglalatba illik
- **LGA (Land Grid Array):** az érintkezők a foglalatban vannak

### Működési elv

- A CPU végrehajtja a tárolt utasítások sorozatát (program)
- Minden processzornak van **utasításkészlete**
- Futtatás közben a szükséges adatok a **gyorsítótárban (cache)** tárolódnak

**Két alapvető CPU architektúra:**

| Típus | Leírás |
|-------|--------|
| **RISC** (Reduced Instruction Set Computer) | Kis utasításkészlet, de nagyon gyorsan hajtja végre |
| **CISC** (Complex Instruction Set Computer) | Nagy utasításkészlet, kevesebb lépés szükséges |

### Teljesítményt befolyásoló tényezők

- **Órajel frekvencia:** MHz vagy GHz (másodpercenkénti ciklusok száma)
- **Adatbusz szélessége:** 32 bites vagy 64 bites (egyidejűleg átvitt bitek száma)
- **Buszrendszer:** FSB (Front Side Bus) / rendszerbusz

### Magok száma (multicore)

| Típus | Leírás |
|-------|--------|
| Egymagos CPU | 1 mag végez minden feladatot |
| Kétmagos (Dual-core) | 2 mag egyszerre, külön-külön számít |
| Hárommagos | Valójában egy négymagos, ahol 1 mag ki van kapcsolva |
| Négymagos (Quad-core) | 4 mag egy chipen |
| Hat- és nyolcmagos | 6 ill. 8 mag egy chipen |

**Hyperthreading (Intel technológia):**
- Az OS számára 1 kétszálas processzor = 2 processzornak látszik
- Egyidejűleg több programrészletet hajt végre

---

## 2.3 RAM (Random Access Memory)

- **Véletlen elérésű, írható/olvasható** adattároló
- **Volatilis (felejtő):** kikapcsoláskor az adatok elvesznek
- Tárolja: a CPU által végrehajtandó programokat és feldolgozandó adatokat
- A **memóriarekesz** 1 bájtot tárol; sorszáma a **cím**
- 8 cella = 1 bájt, 1 cella = 1 bit

**Miért lassabb a RAM, mint a CPU?**
→ Ezért van a CPU-ban **cache (gyorsítótár)** memória

**Késleltetés (Latency):** pl. 2-4-4-5 formában jelzik
- 1. szám: CAS (Column Address Strobe) késleltetés
- 2. szám: tRCD (sor és oszlop kiválasztás közötti idő)
- 3. szám: RP (RAS Precharge)
- 4. szám: sor és modul kiválasztás közötti szünet

**Dual Channel mód:** két egyforma modult kötnek be → nagyobb sávszélesség → gyorsabb teljesítmény

**RAM tokozási típusok:**
- **SIMM** (Single In-Line Memory Module) – régi, 286/386/486 korszak
- **DIMM** (Dual In-Line Memory Module) – mai standard
- **DDR2, DDR3, DDR4, DDR5** – generációk, egyre gyorsabbak

---

## 2.4 Hűtőrendszerek

**Miért kell hűteni?**
- Az elektromos áram áthaladása hőt termel
- Túl sok hő → lassabb működés, alkatrész károsodás

**CPU hűtése:**
- **Hűtőborda (heatsink):** elvezeti a hőt a processzor magjától
- **Ventilátor:** a hűtőbordán elhelyezve a hőt a házból kivezeti
- Hővezető paszta kerül a CPU és a hűtőborda közé

**GPU (videokártya) hűtése:**
- Terhelés alatt akár 100 Celsius fokra is melegedhet
- Saját ventilátorral van ellátva

**Vízhűtés:**
- Nagy teljesítményű CPU-khoz és GPU-khoz
- Fém lapka a processzoron → víz kering felette → hűtőtestbe kerül → levegő elvezeti a hőt → újrakerintetés

---

# 📅 3. NAP – Számítógépház, Tápegység, Bővítőkártyák, Feszültségvédelem

---

## 3.1 Számítógépház

**Funkciói:**
1. **Védelem:** megvédi a belső alkatrészeket
2. **Váz:** megtartja az alkatrészeket
3. **Hűtés:** ventilátorok mozgatják a levegőt az alkatrészek között
4. **Földelés:** az alkatrészek érintkeznek a házzal → elektrosztatikus védelmet nyújt

**Anyaga:** műanyag, acél vagy alumínium

**Ház kiválasztásánál figyelni kell:**
- Alaplap mérete (ATX, Micro-ATX, Mini-ITX)
- Külső és belső meghajtóhelyek száma
- Rendelkezésre álló hely

---

## 3.2 Tápegység

**Feladata:** a fali aljzatból érkező váltóáramot (AC) kisfeszültségű egyenárammá (DC) alakítja.

**Tápegység formátumok:**
- AT (Advanced Technology) – elavult
- ATX (AT Extended) – régebbi
- **ATX12V** – napjaink leggyakoribb típusa

**Feszültségszintek:**

| Feszültség | Szín | Felhasználás |
|------------|------|-------------|
| +12V | Sárga | Lemezmeghajtó motorok, ventilátorok |
| -12V | Kék | Soros port áramkörei, ROM |
| +5V | Piros | Alaplap, régebbi processzorok, egyéb alaplapi elemek |
| -5V | Fehér | ISA busz kártyák |
| +3,3V | Narancs | PCI grafikus kártyák, CPU |
| 0V | Fekete | Földelés |

**3 speciális ATX kivezetés:**
- **PWR-OK (szürke, 5V):** jelzi, hogy minden feszültség stabil → az alaplap csak ekkor lép működésbe
- **PS-ON (zöld, 5V):** szoftveres ki-/bekapcsolás (APM, ACPI funkciók)
- **5VSB (lila, 5V):** készenléti állapotban is aktív → lehetővé teszi a távolról való bekapcsolást (LAN, USB)

**Tápegység csatlakozók:**

| Csatlakozó | Felhasználás |
|-----------|-------------|
| **Molex** | Optikai meghajtók, régi merevlemezek |
| **Berg** | Hajlékonylemezes meghajtó (kisebb, mint a Molex) |
| **SATA** | Optikai meghajtók, SATA merevlemezek |
| **20/24 tűs ATX** | Az alaplap főtápcsatlakozója |
| **4-8 tűs kiegészítő** | Alaplap további területei |
| **6-8 tűs PCIe** | Videokártyák tápellátása |

---

## 3.3 Feszültségingadozás és Szünetmentes Tápegység (UPS)

**A feszültségingadozás típusai:**

| Típus | Leírás |
|-------|--------|
| **Áramszünet (blackout)** | Az áram teljes megszűnése |
| **Feszültségesés (brownout)** | Feszültség a normál 80%-a alá esik |
| **Zaj** | Generátoroktól, villámlástól eredő zavar |
| **Tüske (spike)** | Rövid, hirtelen feszültségnövekedés (>100%) |
| **Áramlöket** | Nanoszekundumos hatalmas feszültségugrás |

**Védelmi eszközök:**
- **Túlfeszültségvédő:** áramlöketek és tüskék ellen; a többletfeszültséget a földelésre vezeti
- **UPS (Uninterruptible Power Supply – Szünetmentes tápegység):** folyamatos tápellátást biztosít; beépített akkumulátor folyamatosan töltődik

**UPS típusok:**
- **Készenléti UPS** (pl. APC Back-UPS): normálisan átengedi a hálózati áramot; csak probléma esetén kapcsol az akkumulátorra → lassabb átkapcsolás
- **Vonal interaktív UPS** (pl. APC Smart-UPS): automatikus feszültségszabályozó (AVR) korrigálja az ingadozásokat → jobb védelem

---

## 3.4 Illesztő- és Bővítőkártyák

**Illesztőkártya:** növeli a számítógép funkcionalitását; vezérlőegységet ad hozzá.

**Bővítőkártyák típusai:**

| Típus | Funkció |
|-------|---------|
| **NIC (Network Interface Card)** | Hálózati csatoló |
| **Wireless NIC** | Vezeték nélküli hálózat |
| **Hangkártya** | Audio szolgáltatások |
| **Videokártya (GPU)** | Grafikai feldolgozás |
| **TV tuner kártya** | TV-adás megtekintése, rögzítése |
| **Modem adapter** | Internet telefonvonalon |
| **SCSI vezérlő** | SCSI eszközök csatlakoztatása |
| **RAID vezérlő** | Több merevlemez kezelése |
| **USB csatoló** | Külső eszközök |

**Bővítőhelyek (slotok):**

| Bővítőhely | Leírás |
|------------|--------|
| **PCI** | Régebbi standard; egyszerű kommunikáció |
| **AGP** | Grafikus kártyákhoz; elavult |
| **PCIe (PCI Express)** | Az AGP utódja; van x1, x4, x8, x16 változat |
| **PCIx** | Akár 4× gyorsabb, mint PCI |
| **Mini PCI** | Laptopokban |
| **CNR** | Régi hálózati/hangkártya slot; már nem használják |

---

# 📅 4. NAP – Tárolóeszközök, Merevlemez-struktúra, RAID

---

## 4.1 Tárolóeszközök

**Tárolóeszköz:** olyan elektronikai eszköz, amely képes az információ tárolására; feszültség nélkül is megmaradnak az adatok.

**4 fő típus:**

### Hajlékony lemezes meghajtó (Floppy)
- 3,5 inch-es mágneslemez, max. **1,44 MB** kapacitás
- Általában az **A: meghajtóbetűjelet** kapja
- Mára teljesen elavult

### Merevlemez – HDD (Hard Disk Drive)
- Mágneses elven tárolja az adatokat
- Kapacitás: GB-tól TB-ig
- Sebesség: **RPM (fordulatszám)** → 5400, 7200, 10 000, 15 000 rpm
- Mozgó alkatrészek vannak → töredezetté válhat (defragmentálás szükséges)

### Merevlemez – SSD (Solid State Drive)
- **Nincsenek mozgó alkatrészek** → gyorsabb, megbízhatóbb, csendesebb
- Flash memória chipeken tárolja az adatokat
- Kevesebb energiafogyasztás
- ATA vagy SATA csatlakozóval rendelkeznek

### Optikai meghajtó

| Típus | Kapacitás |
|-------|-----------|
| CD | ~700 MB |
| DVD (egyrétegű) | ~4,7 GB |
| DVD (kétrétegű) | ~8,5 GB |
| Blu-ray (egyrétegű) | 25 GB |
| Blu-ray (kétrétegű) | 50 GB |

- Lézersugárral olvassa/írja az adatokat
- Lehetnek: csak olvasható (ROM), egyszer írható (R), újraírható (RW)

### Flash meghajtó (Pendrive)
- USB porthoz csatlakoztatható
- Nem felejtő (nemvolatilis) flash memória
- Nincs szüksége energiára az adatok megtartásához

**Csatlakozási típusok:**
- Belső tárolók: SATA, PATA (IDE) csatlakozók
- Külső tárolók: USB, FireWire (IEEE 1394), eSATA, SCSI

---

## 4.2 Merevlemezek adattárolási struktúrája

### Fizikai felépítés

- **Sáv (track):** koncentrikus körök a lemezfelületen
- **Szektor (sector):** a sávon belüli kisebb egységek
- **Cilinder (cylinder):** fizikailag egymás alatt elhelyezkedő sávok (több lemezfelület esetén)

### Formázás lépései

**1. Alacsony szintű (fizikai) formázás (Low Level Format):**
- Felírja az azonosítókat a lemezre
- Beírja a szektor fejekbe: sáv száma, fej sorszáma, szektor száma
- **A gyárban végzik el** → a felhasználó nem kell/nem szabad megismételje

**2. Logikai formázás:**
- Kialakítja a **fájlrendszert**
- Alapegység: **klaszter** (több szektorból áll)
- Az OS csak klaszterenként tud írni/olvasni

### Particionálás

- Minden merevlemez 1 fizikai partícióból áll
- Feloszható **logikai partíciókra** (mintha külön merevlemezek lennének)
- Lehetővé teszi több operációs rendszer futtatását
- **MBR (Master Boot Record):** az első szektorban van; tartalmazza a partíciós táblát és az indító adatokat

### Fájlrendszerek

| Fájlrendszer | Operációs rendszer |
|-------------|-------------------|
| FAT16 | MS-DOS |
| FAT32 | Windows 95, 98 |
| NTFS | Windows NT, 2000, XP, Vista, 7, 10, 11 |
| ext2/ext3/ext4 | Linux |

---

## 4.3 RAID (Redundant Array of Independent Disks)

**Célja:**
- Nagyobb **megbízhatóság** (redundancia)
- Nagyobb **adatelérési sebesség**
- Az OS számára **egyetlen logikai meghajtóként** látszik

**RAID szintek:**

### RAID 0 – Csíkozás (Striping)
- Az adatokat **elosztja** a meghajtók között
- **Legjobb teljesítmény** az összes RAID közül
- **Nincs redundancia** → ha 1 lemez meghibásodik, minden adat elveszik
- Alkalmazás: ahol nem fontos az adatbiztonság, de fontos a sebesség

### RAID 1 – Tükrözés (Mirroring)
- Az adatokat **duplikáltan** tárolja 2 meghajtón
- **Kiváló hibavédelem** → bármelyik meghajtó meghibásodhat
- Olvasás: párhuzamosan, gyorsabb
- Írás: normál sebességgel, párhuzamosan
- **Hátránya:** kétszeres tárhelyfelhasználás

### RAID 5 – Csíkozás paritással
- Az adatokat **ÉS a paritásinformációt** osztja el egyenletesen az összes meghajtón
- **Körbeforgó paritás (rotating parity)** – nincs egyetlen kijelölt paritáslemez
- Párhuzamos írás és olvasás
- Minimum **3 meghajtó** szükséges

### RAID 01 (RAID 10 / RAID 1+0)
- **Hibrid:** RAID 0 sebessége + RAID 1 biztonsága
- Minimum **4 meghajtó** szükséges
- Összefűzés (RAID 0) + tükrözés (RAID 1)
- A teljes kapacitás felét lehet használni

---

# 📅 5. NAP – Megjelenítők, Nyomtatók

---

## 5.1 Megjelenítők (Monitorok)

**A legfontosabb kimeneti eszköz.**

### Monitorok típusai képmegjelenítés szerint

#### Katódsugárcsöves (CRT – Cathode Ray Tube)
- Régebben legelterjedtebb (pl. hagyományos TV)
- **Előnyök:** alacsony ár, legjobb képminőség a technológiák közül
- **Hátrányok:** nagy súly, nagy fogyasztás, káros kisugárzás, villogó kép
- **Működési elv:**
  1. Elektronágyú: monokróm = 1 sugár, színes = 3 sugár
  2. Mágneses eltérítő tekercsek mozgatják a sugarat
  3. Foszforporral bevont felület → a becsapódó elektron fényt kelt

#### Folyadékkristályos (LCD – Liquid Crystal Display)
- Először laptopokban, ma asztali változatok is
- **Előnyök:** vékony, kis energiafogyasztás, állandó (nem villogó) kép
- **Hátrányok:** magasabb ár, alacsony betekintési szög
- **Működési elv:**
  1. Két üveglap közé folyadékkristályt helyeznek
  2. Polárszűrők csak egy irányból engedik át a fényt
  3. Kristálymolekula elforgatja a fényt → világos pont
  4. Ha feszültséget kap a kristály: nem forgatja a fényt → fekete pont

#### Gázplazmás (PDP – Plasma Display Panel)
- 1964 óta létezik; kevésbé elterjedt
- Képminőség vetekedik a CRT-vel
- Mérete akár 100 inch felett is lehet
- **Működési elv:**
  - Minden képpont = 1 kis neoncső
  - Elektromos áram plazmává alakítja a gázt
  - A plazma UV fényt bocsát ki
  - Az UV fény látható fényt gerjeszt a foszforrétegen

#### LED megjelenítő (OLED – Organic Light-Emitting Diode)
- Pixelenként szabályozható a világítás
- **Hátránya:** nem elég nagy fényerő

---

### Monitorok főbb paraméterei

| Paraméter | Leírás |
|-----------|--------|
| **Képátló** | Hüvelykben (inch) mérve (1 inch ≈ 2,54 cm); elterjedtek: 15–24+ inch |
| **Felbontás** | Megjeleníthető pixelek száma (sor × oszlop); pl. 1920×1080 = Full HD |
| **Képarány** | Pl. 4:3, 16:9, 16:10 |
| **Színmélység** | 1 bit (monokróm), 8 bit (VGA), 16 bit (High Color), 24 bit (True Color), 30–48 bit (Deep Color) |
| **Kontraszt** | Világos és sötét aránya egy képkockán (pl. 10 000:1) |
| **Képfrissítési frekvencia** | CRT-nél Hz-ben; LCD-nél válaszidő (ms) |
| **Színkeverés** | RGB (additív): R+G+B maximumon = fehér |

**Felbontások:**

| Jelölés | Felbontás |
|---------|-----------|
| SVGA | 800×600 |
| XGA | 1024×768 |
| HD | 1366×768 |
| Full HD | 1920×1080 |
| UHD 4K | 3840×2160 |
| UHD 8K | 7680×4320 |

### Csatlakozási típusok

| Csatlakozó | Leírás |
|-----------|--------|
| **D-Sub (VGA)** | Analóg; támogatja a Full HD-t |
| **DVI** | Digitális és analóg; típusai: DVI-A, DVI-D, DVI-I |
| **HDMI** | Digitális; 4K, 60fps; mini és micro változat is |
| **DisplayPort** | Digitális; akár 8K; akár 8 monitor Full HD-ban |

---

## 5.2 Nyomtatók

**Csoportosítás alkalmazott technika szerint:**
- **Kontakt nyomtatók** (fizikailag érinti a papírt)
- **Nem kontakt nyomtatók**

**Csoportosítás működési elv szerint:**

### Mátrixnyomtató (mechanikus/kontakt)
- Nyomtatófej tűi ütnek a festékszalagra → kép a papíron
- **9 vagy 24 tű** a fejen
- Leporelló papírt használ
- **Előnyök:** olcsó festék, egybefüggő papír, másolatkészítés
- **Hátrányok:** zajos, lassú, alacsony felbontás

### Tintasugaras nyomtató
- Festékpatronok apró lyukakon (fúvókákon) szórják a festéket
- **Előnyök:** alacsony bekerülési költség, nagy felbontás
- **Hátrányok:** fúvókák eltömődhetnek, drága patronok, lassan szárad a tinta
- Két technológia:
  - **Ink Jet:** piezo kristályok pumpálják a tintát
  - **Bubble Jet:** felmelegített tinta → gőzbuborék repíti ki a tintát

### Lézernyomtató
- Lézerfénnyel és festékporral (toner) dolgozik
- **Előnyök:** alacsony laponkénti költség, nagy sebesség, nagy terhelhetőség
- **Hátrányok:** magas bekerülési költség, drága toner, képzettséget igényel
- **Működési lépések (6 lépés):**
  1. **Kondicionálás** – látens kép eltávolítása a dobról
  2. **Írás** – a dobegységet lézerrel megvilágítják
  3. **Előhívás** – negatív töltésű festékszemcsék a pozitív töltésű dob részeire tapadnak
  4. **Felhordás** – a festék a papírra kerül
  5. **Beégetés** – felmelegített görgő rögzíti a festéket a papíron
  6. LED-es lézernyomtató: LED sor világítja meg a szelénhengert

### Hőpapíros nyomtató
- Főleg **pénztárgépekben** használják
- Hőpapír = vegyileg előkezelt, viaszos tapintású anyag; hő hatására megfeketedik
- **Előnyök:** hosszú élettartam, nincs festékköltség
- **Hátrányok:** drága a papír, hamar tönkremegy, gyenge minőség

### Szilárdtintás nyomtató
- Szilárd halmazállapotú műgyanta vagy viasz alapú festék
- **Előnyök:** viaszos felület (vízálló), fotóminőség, környezetbarát
- **Hátrányok:** lassú felmelegedés, magas energiafogyasztás, viaszos réteg miatt nem írható

### Festékszublimációs nyomtató
- Fotóminőségű grafikai nyomtatás
- Szilárd festék → gáznemű (szublimáció)
- **Előnyök:** kiváló képminőség, zsír- és nedvességálló
- **Hátrányok:** magas fenntartási költség

### 3D nyomtató
- CAD fájlt szeletel fel (~0,1 mm-es rétegek)
- Por alapanyaggal és ragasztóval dolgozik
- Képes pontos valós 3D modellek előállítására

### Nyomtatók főbb paraméterei

- **Felbontás:** DPI (dots per inch) – pl. 300, 600, 1200 DPI
- **Nyomtatási sebesség:**
  - CPS (characters per second) – karakternyomtatóknál
  - PPM (pages per minute) – lapnyomtatóknál

### Színkeverés – CMYK (nyomtatóknál)
- **Kivonó (szubtraktív)** színkeverés
- C = Cyan, M = Magenta, Y = Yellow, K = Black (Key)
- A fehér fényből bizonyos színeket elnyel → a visszavert maradék adja a képet
- **Fehér szín nem nyomtatható** (a papír fehér)
- Fekete szín külön szükséges

---

# 📅 6. NAP – Big Data, Virtualizáció, CAD/CAM, Elektronika alapjai

---

## 6.1 Big Data

**Mi a Big Data?**
Big Data-ról akkor beszélünk, ha:
- **Nagy mennyiségű** adat
- **Nagy sebességű** (valós idejű, folyamatosan érkező) adat
- **Nagy változatosságú** (sokféle tartalmú és formátumú) adat

A fogalmat **Roger Mougalas (O'Reilly Media)** használta először 2005-ben.
Ugyanebben az évben hozta létre a **Yahoo! a Hadoop**-ot (nagy adathalmaz kezelő rendszer).

**Mire használjuk a Big Data-t?**
- Költségek, feldolgozási idők csökkentése
- Új termékek, szolgáltatások fejlesztése
- Jobb döntéshozatal
- Prediktív elemzés (előrejelzés)
- Viselkedéselemzés (marketing, orvostudomány, rendészet stb.)

**Kihívások:**
- **Adatvédelem** (GDPR – EU szabályozás)
- **Hatékonyság** – nehéz kezelni a hatalmas adatmennyiséget
- Szükséges: **gépi tanulás, üzleti intelligencia (BI), felhőalapú számítástechnika**

**Szükséges hardver:**
- **Felhőalapú tárolórendszerek** – helytől független adatfeldolgozás
- **Fog (köd) farmok** – logikailag a helyi szerverek felett, fizikailag közelben

**Big Data alkalmazásai:**
- **BKK Futár** – GPS-adatok alapján forgalomelemzés, menetrendszámítás
- **Google App Engine** – alkalmazások futtatása felhőben
- **Amazon EC2** – virtuális számítógép-kölcsönzés
- **Tinder** – komplex egyeztetési algoritmus nagy felhasználói adatbázison

---

## 6.2 Virtualizáció

**Virtualizáció:** fizikai helyett **szimulált (virtuális) számítási környezet** létrehozása.

- Egyetlen fizikai számítógép → több virtuális gép
- Minden virtuális gép egymástól független; különféle OS-t és alkalmazásokat futtathat
- Közös gazdagép-erőforrásokon osztoznak

**Előnyök:**
- Jobb erőforrás-kihasználás
- Kevesebb szerver szükséges
- Kevesebb energiafogyasztás
- Alacsonyabb infrastruktúra- és karbantartási költség

**A virtualizáció 4 kategóriája:**

| Típus | Leírás |
|-------|--------|
| **Asztali virtualizáció** | Egyetlen szerver egyedi asztali rendszereket tesz elérhetővé |
| **Hálózati virtualizáció** | Sávszélességet független csatornákra osztja fel |
| **Szoftver-virtualizáció** | Alkalmazásokat elkülöníti a hardvertől és OS-től |
| **Tárolási virtualizáció** | Több hálózati tárolót egyesít egyetlen tárolóeszközzé |

---

## 6.3 CAD/CAM Munkaállomások

**CAD** – Computer-Aided Design (számítógéppel segített tervezés)
**CAM** – Computer-Aided Manufacturing (számítógéppel segített gyártás)

Felhasználás: modellek, lakások, autók, repülők, alkatrészek tervezése.

**Szükséges hardver CAD/CAM munkaállomáshoz:**
- **Nagy teljesítményű processzor** – rengeteg számítás
- **Csúcsminőségű videokártya** – 3D renderelés, több monitor, nagy felbontás
- **Nagy RAM** – sok adatot kezel egyszerre; minél több, annál jobb

---

## 6.4 Elektronika alapjai (Kristálytiszta Elektronika anyag)

### Kapcsolási rajzok alapjai

**Kapcsolási rajz:** „térkép", amellyel ki lehet igazodni egy áramkör felépítésében.
- Két szabvány létezik: **IEC** és **ANSI**
- **Csomópont:** ahol több vezetékszakasz összekapcsolódik (ponttal jelölik)
- **Rövidzár:** az áram útját rövidre zárjuk (0 Ohm ellenállás)
- **Szakadás:** nincs vezető az adott szakaszon (végtelen ellenállás)

### Alkatrészek csoportosítása

- **Aktív elemek:** külső vezérlő jel hatására megváltoztatják elektromos tulajdonságukat (pl. tranzisztor, MOSFET, processzor, memória)
- **Passzív elemek:** minden más (pl. ellenállás, kondenzátor, dióda, tekercs)

### Főbb alkatrészek

**Ellenállás (R):**
- Mértékegység: **Ohm (Ω)**
- Az áram áthaladáskor hő keletkezik
- Soros kapcsolásnál: R_e = R1 + R2 + R3 (összeg)
- Párhuzamos kapcsolásnál: 1/R_e = 1/R1 + 1/R2 + ... (reciprok összeg)
- Teljesítmény: P = U × I = U²/R = R × I²

**Kondenzátor (C):**
- Mértékegység: **Farad (F)**
- Két vezető réteg (fegyverzet) közt szigetelő (dielektrikum)
- Polarizált (elektrolit, tantál): figyelni kell a polaritásra!
- Nem polarizált (kerámia, fólia): mindegy az irány

**Dióda:**
- Csak egyik irányban engedi át az áramot (anód → katód)
- **Nyitóirányú feszültség:** ~0,7V (szilícium diódánál)
- Speciális típusok: LED (fényt bocsát ki), Zéner-dióda (túlfeszültségvédelem), Schottky-dióda

**Multiméter:**
- Feszültség, áramerősség, ellenállás mérésére
- Feszültségmérés: **párhuzamosan** kötjük be
- Áramerősségmérés: **sorosan** kötjük be (vigyázat: tönkretehetjük a műszert!)
- Ellenállásmérés: az alkatrészt kivesszük az áramkörből

### Ohm-törvény

**R [Ω] = U [V] / I [A]**

### Breadboard
- Áramkörök prototípus-összeépítésére
- Lyukakba nyomjuk az alkatrészek lábait
- Oszlopok: függőlegesen összekötött lyukak
- Tápsínek: a hosszabb széleken futó párhuzamos sínek (+/-)

### Laboratóriumi tápegység
- Váltóáramot (AC) egyenárammá (DC) alakítja
- Szabályozható kimenet: feszültség és áramkorlát
- **C.V. (Constant Voltage):** feszültséggenerátoros üzemmód
- **C.C. (Constant Current):** áramgenerátoros üzemmód (az áramkorlát életbe lépett)

---

# 📋 ÖSSZEFOGLALÓ TÁBLÁZAT – Legfontosabb fogalmak

| Fogalom | Egyszerű magyarázat |
|---------|---------------------|
| **CPU** | Processzor, a számítógép agya |
| **RAM** | Ideiglenes memória, kikapcsoláskor elvész |
| **ROM** | Csak olvasható memória, maradandó |
| **BIOS** | Alapszoftver az alaplapon; POST, boot |
| **UEFI** | BIOS utódja; gyorsabb, grafikus felület |
| **CMOS** | BIOS beállítások tárolója (gombelem táplálja) |
| **POST** | Önellenőrzés indításkor |
| **MBR** | Első szektor, operációs rendszer betöltő |
| **HDD** | Mágneses merevlemez (mozgó alkatrészek) |
| **SSD** | Flash alapú meghajtó (nincs mozgó rész) |
| **RAID 0** | Gyors, nincs redundancia |
| **RAID 1** | Tükrözés, dupla tárhely, jó biztonság |
| **RAID 5** | Paritásos, minimum 3 lemez |
| **ATX** | Tápegység/alaplap szabvány |
| **PCIe** | Bővítőhely szabvány (x1, x4, x8, x16) |
| **DPI** | Nyomtatási felbontás (pont/hüvelyk) |
| **CMYK** | Nyomtatók színkeverési módja |
| **RGB** | Monitorok additív színkeverése |
| **UPS** | Szünetmentes tápegység |
| **Big Data** | Nagy, gyors, sokféle adathalmaz |
| **Virtualizáció** | Egy fizikai gép → több virtuális gép |
| **CAD/CAM** | Számítógépes tervezés és gyártás |

---

# 🎯 Tanulási tippek a 6 napra

- **1. nap:** Neumann-elvek + Hardver/Firmware + BIOS/UEFI → olvasd el, majd csukd be és mondj el mindent
- **2. nap:** Alaplap komponensei + CPU + RAM + Hűtés → rajzolj alaplap-vázlatot memóriából
- **3. nap:** Ház + Tápegység (feszültségszínek!) + Bővítőkártyák + UPS
- **4. nap:** Tárolóeszközök + Merevlemez-struktúra + RAID szintek (táblázattal)
- **5. nap:** Monitorok (típusok + paraméterek + csatlakozók) + Nyomtatók (típusok + működési elvek)
- **6. nap:** Big Data + Virtualizáció + CAD/CAM + Elektronika alapjai + **Teljes ismétlés**

> 💡 **Tipp:** A szín-kábel párosításokat (tápegység), a RAID szinteket és a nyomtató 6 lépéses lézer-folyamatot írd ki egy külön papírra és ragaszd ki!
