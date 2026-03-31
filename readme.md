# Navodila za nastavitev osebne Hugo strani laboratorija

V tem dokumentu so navedena navodila, kako nastaviti in uporabljati svojo Hugo stran za laboratorij. Vsak član laboratorija bo imel svojo Hugo stran, ki bo gostovana pod domeno `sujt.fri.uni-lj.si/member_repository`.

## 1. Kopiranje predloga repozitorija

### 1.1. Kako uporabiti privzeti predlog

1. Prijavite se v GitHub in pojdite na GitHub organizacijo laboratorija.
2. Odprite [predlogo Hugo strani](https://github.com/sujtfri/member_template), ki je na voljo v repozitoriju.
3. Kliknite gumb `Use this template`.
4. Ustvarite novo ime za vaš osebni repozitorij. Priporočljivo je, da uporabite svoje osebno ime, na primer: `ime.priimek` ali  `ime-priimek`
5. Preverite, da je izbrana možnost Public repository, ter da je **owner sujtfri** in kliknite Create repository

### 1.2. Kako omogočiti drugim članom uporabo vašega repozitorija kot predloge

1. Prijavite se v GitHub in pojdite na GitHub organizacijo laboratorija.
2. Odprite vaš repozitorij, ki ga želite omogočiti kot predlogo.
3. Pojdite na **Settings** (nastavitve) vašega repozitorija.
4. Pomaknite se navzdol do razdelka **Template repository** in označite možnost **This repository is a template**.
5. Kliknite **Save changes**.

Po tem bo vaš repozitorij na voljo kot predloga za druge člane laboratorija.

### 1.3. Kako uporabiti repozitorij drugega člana kot predlogo

1. Prijavite se v GitHub in pojdite na GitHub organizacijo laboratorija.
2. Odprite repozitorij, ki ga želite uporabiti kot predlogo.
3. Kliknite gumb **Use this template**.
4. Ustvarite novo ime za vaš osebni repozitorij. Priporočljivo je, da uporabite svoje osebno ime, na primer: **ime.priimek** ali **ime-priimek**.
5. Preverite, da je izbrana možnost **Public repository**, ter da je **owner sujtfri**, in kliknite **Create repository**.


## 2. Kloniranje repozitorija

### 2.1. Odprite terminal ali ukazno vrstico in klonirajte svoj novoustvarjeni repozitorij na lokalni računalnik:

```bash
git clone https://github.com/sujtfri/ime.priimek.git
```

### 2.2. Premaknite se v imenik repozitorija:

```bash
cd ime.priimek
```

### 2.3. Omogočanje GitHub Pages in GitHub Actions

1. Pojdite na nastavitve vašega repozitorija v GitHub.
2. Izberite zavihek **Pages**.
3. V razdelku Source izberite **GitHub Actions** kot vir za GitHub Pages.

### 2.4. Inicializacija teme kot podmodula

Po kloniranju repozitorija in premiku v imenik, morate inicializirati podmodul teme:

```bash
git submodule update --init --recursive
```

Ta ukaz prenese temo, ki je potrebna za delovanje Hugo strani. Če v prihodnosti pride do posodobitev teme, lahko uporabite ukaz:

```bash
git submodule update --remote
```

### 2.5 Posodabljanje vašega repozitorija ob spremembah v predlogi

1. Dodajte repozitorij predloge kot upstream: 

```bash
git remote add upstream https://github.com/sujtfri/member_template.git

```
2. Ko želite posodobiti vaš repozitorij, povlečite najnovejše spremembe iz predloge (upstream):

```bash
git fetch upstream
```

3. Spojite spremembe z vašo glavno vejo:

```bash
git merge upstream/main
```

Če pride do konfliktov, jih ročno rešite in nato dokončajte združevanje.

4. Dodajte spremembe v vaš repozitorij na GitHub:

```bash
git push origin main
```

Po teh korakih bodo vse najnovejše spremembe iz predloge vključene v vaš repozitorij.

## 3. Urejanje osebne vsebine

Vse spremembe boste izvajali znotraj svojega repozitorija. Vaša osebna stran v Hugo je zasnovana tako, da omogoča preprosto upravljanje vsebin. Spodaj so podana navodila za pisanje objav in nastavitev strani. Pri urejanju vsebine v Markdownu lahko uporabite HTML v Markdown converter-ji, kot je npr. **[https://htmlmarkdown.com/](https://htmlmarkdown.com/)**, če imate vsebino v HTML obliki, ki jo želite pretvoriti.

### 3.1. Urejanje glavne biografije

Glavna biografija vsakega člana je v datoteki `content/\_index.md`. Ta datoteka predstavlja vašo domačo stran in vsebino, ki bo vidna ob obisku vašega profila.
V primeru **večjezične vsebine** se glavna biografija nahaja v datotekah, specifičnih za posamezen jezik. Na primer:

- Za angleško različico: `content/english/\_index.md`
- Za slovensko različico: `content/slovene/\_index.md`

#### Kako urediti biografijo:

1. Odprite datoteko `content/\_index.md` (ali ustrezno datoteko za vaš jezik).
2. Vnesite ali uredite svojo biografijo. Uporabite Markdown za formatiranje besedila.

Primer vsebine:

```markdown
+++
title = "Ime Priimek"
+++

# Dobrodošli

Sem Ime Priimek, raziskovalec v Laboratoriju za kognitivno modeliranje.
```

### 3.2. Ustvarjanje novih strani

Vsaka dodatna stran, ki jo želite imeti na svojem profilu, potrebuje svojo mapo in datoteko \_index.md.

#### Koraki za ustvarjanje nove strani:

1. Če želite ustvariti novo stran, na primer **"Lecturing"**, ustvarite naslednjo strukturo:
   - `content/lecturing/\_index.md` (ali ustrezno datoteko za vaš jezik, npr. `content/english/lecturing/\_index.md`)
2. Za vsako podstran znotraj te strani (npr. posamezni predmeti) lahko ustvarite dodatne datoteke, na primer:
   - `content/lecturing/subject1.md` (ali ustrezno datoteko za vaš jezik, npr. `content/english/lecturing/subject1.md`)

#### Primer nove strani **"Lecturing"**

```bash
hugo new content/lecturing/_index.md  // hugo new content/english/lecturing/_index.md
```

#### Vsebina `content/lecturing/_index.md`:

```markdown
+++
title = "Lecturing"
+++

# Moji predmeti

Tukaj so navedeni predmeti, ki jih predavam.

1. [Subject 1]({{< relref "subject1.md" >}})
2. [Subject 2]({{< relref "subject2.md" >}})
```

#### Vsebina `content/lecturing/subject1.md`:

```markdown
---
title = "Predmet 1"
---

# Opis predmeta 1

Podroben opis predmeta.
```

### 3.3. Dodajanje datotek in slik

Vsaka stran na vašem profilu naj vsebuje pripadajoče datoteke, kot so slike, v isti mapi, kjer se nahaja vsebina strani. Na ta način bodo slike in druge datoteke ustrezno povezane s posamezno stranjo.

#### Koraki za dodajanje slik na stran:

1. **Shranjevanje slik:**
   - Če je slika shranjena v isti mapi kot vsebina strani:
     - Primer: `content/lecturing/img.jpg`
     - V Markdown datoteki vključite sliko tako:
       ```markdown
       ![Opis slike](img.jpg)
       ```
   - Če je slika shranjena v podmapi:
     - Primer: `content/lecturing/images/img.jpg`
     - V Markdown datoteki vključite sliko tako:
       ```markdown
       ![Opis slike](images/img.jpg)
       ```

2. **Uporaba slik iz mape `static`:**
   - Če je slika shranjena v `static` mapi, uporabite absolutno pot:
     - Primer: `static/img/image.jpg`
     - V Markdown datoteki vključite sliko tako:
       ```markdown
       ![Opis slike](/ime.priimek/img/image.jpg)
       ```
   - Če je slika neposredno v `static` mapi, na primer `static/image.jpg`:
       ```markdown
       ![Opis slike](/ime.priimek/image.jpg)
       ```

3. **Dodajanje slik z uporabo HTML `img` elementa:**  
   Če želite imeti več nadzora nad slogom slike (velikost, margine, itd.), uporabite HTML `img` oznako. To je še posebej uporabno, če sliko uporabljate znotraj tabel ali drugih kompleksnih postavitev.

   - **Primer za osnovno sliko:**
     ```html
     <img src="img.jpg" alt="Opis slike" style="width: 100%; border-radius: 8px;">
     ```
   - **Primer za sliko iz `static` mape:**
     ```html
     <img src="/ime.priimek/img/image.jpg" alt="Opis slike" style="width: 50%; margin: 10px;">
     ```

4. **Uporaba slike znotraj Markdown tabele:**
   Če uporabljate tabele za dvo-stolpčno vsebino in želite imeti kontrolirane razmike ali sloge za slike:

   - **Primer Markdown tabele z HTML `img` oznako:**
     ```markdown
     |          |          |
     |----------|----------|
     | <img src="img.jpg" style="width: 80%; margin-right: 20px;"> | Besedilo, ki spremlja sliko v drugem stolpcu. Besedilo je lahko dolg opis ali le nekaj stavkov. |
     ```


#### Dodajanje datotek in slik neposredno iz OneDrive:

1. Če želite dodati slike ali datoteke iz OneDrive, pojdite na svojo datoteko v OneDrive in ustvarite `embed` link.
2. To storite tako, da v OneDrive izberete datoteko, ter na vrhu strani izberite **Embed**.
3. Kopirajte in prilepite povezavo v svojo markdown datoteko.

Primer:

```markdown
![FRI logo](https://1drv.ms/i/s!AnTtkNv__VGYgmWLhKoip-3jZL0j?embed=1&width=620&height=259)
```

![FRI logo](https://1drv.ms/i/s!AnTtkNv__VGYgmWLhKoip-3jZL0j?embed=1&width=620&height=259)

### 3.4. Pisanje vsebine v 2 stolpcih

1. **Odprite datoteko, kjer želite uporabiti stolpce**:

   - Na primer, `content/_index.md` ali drugo vsebinsko datoteko.

2. **Uporabite naslednjo strukturo**:

   - Lahko uporabite **Markdown tabelo** ali **shortcode** za ustvarjanje postavitve v dveh stolpcih.

#### Pristop 1: Uporaba tabele za dva stolpca

   Vsebine lahko razporedite v dva stolpca z uporabo Markdown tabele. To je preprost način, kako pridobiti postavitev, vendar morate biti previdni pri oblikovanju, da bo vsebina pravilno poravnana.

   - Primer:
     ```markdown
     | Stolpec 1                       | Stolpec 2                       |
     |----------------------------------|----------------------------------|
     | Prva vsebina gre sem.            | Druga vsebina gre sem.           |
     | Lahko dodate več besedila tukaj. | Lahko dodate še več besedila tu. |
     ```

#### Pristop 2: Uporaba shortcodov za stolpce

   Druga možnost je uporaba **shortcodov**, ki omogoča več nadzora nad postavitvijo in slogom. Ta pristop omogoča bolj prilagodljive razmike in širine stolpcev.

   - Za uporabo shortcode-a vstavite naslednjo kodo:

     ```markdown
     {{< columns alignment="center" >}}

     Prva vsebina gre sem. Ta bo prikazana v prvem stolpcu.

     {{< column alignment="end" >}}

     Druga vsebina gre sem. Ta bo prikazana v drugem stolpcu.

     {{< endcolumns >}}
     ```

3. **Kaj pomeni koda?**:

   - `{{< columns >}}`: Začetek dveh stolpcev. Ta shortcode aktivira način za razdelitev vsebine v dva stolpca.
   - `{{< column >}}`: Prehod iz prvega v drugi stolpec. Ta shortcode označuje začetek vsebine, ki bo prikazana v drugem stolpcu.
   - `{{< endcolumns >}}`: Konec stolpcev. Ta shortcode zaključi razdelitev vsebine v dva stolpca.
   - opcijski parameter `alignment` v **columns** in **column** določa poravnavanje teksta (center, start, end). 

### 3.5 Uporabo shortcode "content_row"
Shortcode **content_row** prikazuje vse strani znotraj določene sekcije kot kartice v vrsti. Ta shortcode deluje samo za najvišje ravni mape v mapi content, ki se obravnavajo kot sekcije. Na primer, če imate mapo content/blog in v tej mapi strani post1.md, post2.md itd., bo ta shortcode izpisal vse te strani.

#### Kako uporabljati content_row shortcode:
1. Ustvarjanje strukture mape in strani:
- Ustvarite sekcijo znotraj mape content, na primer content/blog/, kjer bodo vaše strani (npr. post1.md, post2.md). Ta shortcode bo izpisal vse te strani kot kartice.
2. Dodajanje vsebine na strani:
- V vsaki datoteki (npr. post1.md) lahko dodate naslov, povzetek in vsebino. V frontmatteru določite naslov in povzetek, ki se bosta prikazala na kartici.
3. Uporaba slik za strani:
- Če želite uporabiti slike na karticah, ustvarite mapo znotraj sekcije za vsako stran. Na primer, `content/blog/post1/index.md` in `content/blog/post1/cover_image.jpg`. V frontmatteru strani dodajte parameter `cover_image` z neposredno povezavo do slike:
```toml
cover_image = "blog/post1/cover_image.jpg"
```
To bo dodalo sliko kot naslovno sliko za kartico.

4. Povezava na zunanjo stran:
- Če želite, da kartica vodi na zunanjo povezavo (npr. zunanji blog), v frontmatteru dodajte parameter `external_url` z URL-jem, na katerega naj kartica vodi:

```yaml
external_url: "https://example.com/zunanja-stran"

```
To omogoča, da na kartico dodate povezavo do vsebine zunaj vaše strani, vendar bo vseeno prikazana v seznamu znotraj vaše strani.

#### Primer uporabe shortcode:
Ko želite uporabiti **content_row** na strani (npr. v `content/blog/_index.md`, kjer podate seznam vseh objav), vstavite naslednji shortcode:

```markdown
{{< content_row "ime_sekcije" >}} //  npr. {{< content_row "blog" >}}
```

Ta shortcode bo prikazal vse strani v `content/ime_sekcije/` kot kartice v seznamu. Kartice bodo vsebovale naslov in povzetek strani, skupaj z naslovno sliko (če je določena), in bodo povezane na ustrezne strani ali zunanje povezave, če je to določeno v frontmatteru.

#### Primer content/blog/post1/index.md
```markdown
+++
title = "This is my first post."
draft = true
cover_image = "blog/post1/cover_image.jpg"
summary = "This is the summary that will be visible in the card."
+++


# This is my first post.

An example of how to use the content_row shortcode.
```
### 3.6 Uporaba shortcode "cloakemail"

Shortcode `cloakemail` omogoča zakrivanje e-poštnih naslovov, telefonskih številk ali drugih komunikacijskih naslovov (npr. XMPP, Telegram) pred spletnimi roboti za preprečevanje neželene pošte. 

#### Uporaba:

```markdown
{{< cloakemail "jane.doe@example.com" >}}
```

ali preko poimenovanega parametra:

```markdown
{{< cloakemail address="jane.doe@example.com" >}}
```

### 3.7 Uporaba shortcode "align"

Shortcode **align** omogoča poravnavo besedila na levi, desni ali sredini.  
Uporabite ga, kadar želite del vsebine oblikovati z drugačno poravnavo od privzete.

#### Primer uporabe:
```markdown
{{< align center >}}
To besedilo bo centrirano.
{{< /align >}}
```

Možne vrednosti:
- start – poravnava levo 
- center – poravnava na sredino
- end – poravnava desno


### 3.8 Uporaba shortcode "benefits"
Shortcode benefits omogoča prikaz treh kartic v vrsti, ki vsebujejo ikono in besedilo. 

#### Primer uporabe:

```markdown
{{< benefits 
  card1="**Naš cilj**<br><br>Naš cilj je ustvarjati, izmenjevati in prenašati znanje na področju strojnega učenja in jezikovnih tehnologij."
  card2="**Projekti**<br><br>Vodilni smo pri številnih nacionalnih in mednarodnih projektih, tako aplikativnih kot teoretičnih."
  card3="**Naše delo**<br><br>Temelji na interdisciplinarnosti in multidisciplinarnosti ter spodbujanju sodelovanja na nacionalni in mednarodni ravni." 
>}}
```

Vsak parameter **card1**, **card2**, **card3** sprejme vsebino z Markdown oblikovanjem in < br> za prelome vrstic.
### 3.9 Uporaba shortcode "btn-primary/btn-secondary"

Shortcodi **btn-primary** in **btn-secondary** ustvarijo gumbe z različnimi stili (primarni ali sekundarni).
Primerni so za povezave na blog, projekte ali druge strani.

#### Primer uporabe:
```markdown
{{< btn-primary "/blog" "Preberi vse novice" >}}
{{< btn-secondary "/projects" "Poglej projekte" >}}
```
- Prvi parameter določa povezavo (/blog, /projects …).
- Drugi parameter določa besedilo gumba.
- Če je jezik strani nastavljen na **si**, se povezava samodejno prilagodi (si/...).

### 3.10 Uporaba shortcode "feature_cards"
Shortcode feature_cards prikazuje do tri kartice s krajšimi besedili. 
#### Primer uporabe:
```markdown
{{< feature_cards 
  card1="**Razvoj**<br><br>Razvijamo nove algoritme za modeliranje podatkov."
  card2="**Raziskave**<br><br>Sodelujemo z zdravniki, farmacevti, biologI, športnimi strokovnjaki in jezikoslovci."
  card3="**Področja raziskav**<br><br>Naše raziskave vključujejo modeliranje numeričnih, slikovnih, besedilnih in prostorskih podatkov ter jezikovne tehnologije." 
>}}
```
Vsaka kartica se prikaže v lastnem bloku. Parametri **card1**, **card2**, **card3** so opcijski – lahko uporabite samo enega, dva ali vse tri.

### 3.11 Uporaba shortcode "redline"
Shortcode **redline** omogoča poudarjanje besedila z rdečo črto na levi strani. Primeren je za poudarjene navedke, pomembna opozorila ali citate.
#### Primer upoabe:
```markdown
{< redline >}}
To je poudarjeno besedilo, ki bo prikazano z rdečo črto na levi strani.
{{< /redline >}}
```

### 3.12 Uporaba shortcode "content_row_small"

Shortcode **content_row_small** je različica shortcoda `content_row`, ki prikazuje strani določene sekcije kot kartice v manjšem, kompaktnejšem dizajnu. Kartice vključujejo naslovno sliko, kategorijo, datum, naslov in povzetek. Poleg tega omogoča omejitev števila prikazanih strani.

#### Parametri:
- `section` (obvezen) – ime sekcije v mapi `content` (npr. `blog`, `projects` …).  
- `limit` (neobvezen) – največje število kartic za prikaz. Če ni podan, se prikažejo vse strani sekcije.

#### Primer uporabe:
```markdown
{{< content_row_small "blog" 3 >}}
```
Ta primer prikaže zadnje 3 objave iz sekcije content/blog.

### 3.13 Urejanje datoteke hugo.toml

Vsakič, ko dodate novo stran, morate posodobiti datoteko hugo.toml, da se nova stran prikaže v meniju. Poleg tega morate prilagoditi naslov, baseURL, in meni.

#### Koraki za urejanje:

1. Odprite datoteko **hugo.toml** v korenu svojem repozitoriju.
2. Spremenite osnovne nastavitve strani:
   - **baseURL**: Tukaj vnesite URL vašega repozitorija. Nadomestite ime-priimek z imenom vašega repozitorija.
   - **title**: Vnesite naslov svoje strani.
   - **menu**: Dodajte nove strani v meni.

#### Dodajanje novega menija:

Če želite dodati novo stran v meni, na primer za "Raziskave", ki se nahaja v **content/research/\_index.md**, v datoteko hugo.toml dodajte nov vnos:

```toml
  [[menu.main]]
    name = "Raziskave"
    url = "/research/"
    weight = 4
```

#### Primer urejene datoteke **hugo.toml**:

```toml
baseURL = 'https://sujtfri.github.io/ime-priimek/'  # Spremenite ime repozitorija
languageCode = 'en-us'
title = 'Ime Priimek'
theme = "member-theme"

[menu]
  [[menu.main]]
    name = "Home"
    url = "/"
    weight = 1

  [[menu.main]]
    name = "Lecturing"
    url = "/lecturing/"
    weight = 2

  [[menu.main]]
    name = "Projekti"
    url = "/projects/"
    weight = 3

```

#### Urejanje datoteke hugo.toml za večjezično vsebino

Če želite omogočiti večjezično podporo za svojo stran, boste morali nastaviti jezike v datoteki hugo.toml. V spodnjem primeru so nastavljeni jeziki za angleščino (en) in slovenščino (si).

Primer za angleški in slovenski jezik:

```toml
baseURL = 'https://sujtfri.github.io/ime-priimek/'  # Spremenite ime repozitorija
title = 'Ime Priimek'
theme = "member-theme"
[languages]
  [languages.en]
    contentDir = 'content/english'
    languageName = 'English'
    weight = 10
    [languages.en.params]
      flag = "flag-icon-us"
    [languages.en.menus]
      [[languages.en.menus.main]]
        name = "About"
        url = "/"
        weight = 100
      [[languages.en.menus.main]]
        name = "Lecturing"
        url = "/lecturing/"
        weight = 200
      [[languages.en.menus.main]]
        name = "Projects"
        url = "/projects/"
        weight = 300

  [languages.si]
    contentDir = 'content/slovene'
    languageName = 'Slovene'
    weight = 10
    [languages.si.params]
      flag = "flag-icon-si"
    [languages.si.menus]
      [[languages.si.menus.main]]
        name = "O meni"
        url = "/si/"
        weight = 100
      [[languages.si.menus.main]]
        name = "Poučevanje"
        url = "/si/lecturing/"
        weight = 200
      [[languages.si.menus.main]]
        name = "Projekti"
        url = "/si/projects/"
        weight = 300
```

V tem primeru so nastavljeni jezikovni nastavitvi za angleščino in slovenščino z ustreznimi mapami za vsebino `content/english` in `content/slovene`. Vsak jezik ima svojo kodo zastave (npr. flag-icon-us za angleščino in flag-icon-si za slovenščino). Vsak jezik ima tudi svojo različico menija, kjer so se imena strani prevedena v ustrezni jezik.

Navodila za večjezične strani:

1. Ustvarite mapo za jezik: V glavni mapi content ustvarite mapo za vsak jezik, na primer `content/english` za angleščino in `content/slovene` za slovenščino.
2. Ustvarite vsebino za vsak jezik: Za vsako stran, ki jo želite prevesti, ustvarite različico v ustrezni jezikovni mapi. Na primer, stran about.md bo v `content/english/about.md` in `content/slovene/about.md.`
3. Dodajte ustrezne povezave: Prepričajte se, da so vsi meniji pravilno nastavljeni v hugo.toml za vsak jezik.

## 4. Testiranje lokalnih sprememb

Preden pošljete svoje spremembe v GitHub, je priporočljivo, da svojo stran preizkusite lokalno z ukazom Hugo, kar vam omogoča hitrejši pregled in odkrivanje morebitnih napak.

### 4.1. Uporaba "hugo server"

Ukaz **"hugo server"** vam omogoča, da zaženete lokalni strežnik, kjer lahko pregledate svojo stran, ne da bi jo objavili.

**Kako uporabiti hugo server:**

1. Odprite terminal ali ukazno vrstico v korenskem direktoriju vašega Hugo repozitorija.
2. Zaženite naslednji ukaz:

```bash
hugo server
```

Ta ukaz bo ustvaril lokalni strežnik, ki bo na voljo na naslovu http://localhost:1313/. Stran bo samodejno osvežena, če boste v datotekah izvedli spremembe. To vam omogoča hitrejše testiranje vsebine.

### 4.2. Uporaba "hugo server -D"

Ko razvijate novo vsebino, lahko želite testirati strani ali objave, ki še niso objavljene, ker so označene kot osnutki. V ta namen uporabite ukaz **"hugo server -D"**, ki omogoča prikaz osnutkov.

**Kako uporabiti "hugo server -D":**

1. Če imate osnutke, ki jih želite pregledati pred objavo, zaženite naslednji ukaz:

```bash
hugo server -D
```

S tem ukazom bodo vidne tudi vse strani ali objave, ki imajo v svojem frontmatter parametru draft = true.

### 4.3. Kaj pomeni parameter "draft"?

V vsaki objavi ali strani, ki jo ustvarite v Hugo, lahko uporabite parameter draft, ki določa, ali je stran pripravljena za objavo ali je še v fazi osnutka.

Primer parametra **draft** v frontmatter:

```markdown
+++
title = "Moj prvi projekt"
date = 2024-10-10
draft = true
+++
```

- Če je **draft = true**, bo stran skrita in ne bo objavljena na spletni strani.
- Če je **draft = false**, bo stran vidna in objavljena na vaši spletni strani.

Ko ste pripravljeni, da stran objavite, preprosto spremenite vrednost parametra **draft** na **false**, nato pa lahko svojo stran testirate lokalno z hugo server ali naložite spremembe na GitHub.

## 5. Dodajanje profila v glavni repozitorij

1. Pojdite na glavni repozitorij laboratorija **sujtfri.github.io**.
2. Poiščite datoteko **data/members.yaml**, kjer se hranijo podatki o vseh članih laboratorija.
3. Dodajte svoje podatke, kot v spodnjem primeru:

```yaml
staff_members:
  - name: "Ime Priimek"
    bio:
      en: "Vaša kratka biografija v angleščini"
      si: "Vaša kratka biografija v slovenščini"
    image: "img/people/vaša_slika.jpg"
    contact: "vaš_email@example.com"
    relurl: "ime.priimek/"
    phone: vaša telefonska številka
```

4. V datoteko **static/img/people/** dodajte svojo sliko profila. Prepričajte se, da ime slike ustreza tistemu, kar ste vnesli v **data/members.yaml**.

## 6. Urejanje **sujt_theme** in layout

### 6.1 Postavitev v Hugo

V Hugo so postavitve ("layouts") datoteke, ki določajo, kako je vsebina prikazana. To vključuje postavitve za glavne strani, seznam strani in posamezne strani z vsebino.

- **list.html**:
  - Uporablja se za vsebino v **_index.md**.
  - Primer: Glavna stran sekcije (npr. **content/lecturing/_index.md**), kjer se prikaže seznam vseh podstrani.

- **single.html**:
  - Uporablja se za posamezne vsebinske strani.
  - Primer: posamezne strani, kot je `content/lecturing/subject1.md`, kjer je prikazana vsebina ene strani.

#### Kje so shranjene postavitve?

1. **Osnovne postavitve**:
   - Nahajajo se v `sujt_theme/layouts/_default/`.
   - Primeri:
     - `list.html`: Za sezname strani.
     - `single.html`: Za posamezne strani.
   
2. **Prilagojene postavitve**:
   - Nahajajo se v podmapah v `sujt_theme/layouts/`, kot je `sujt_theme/layouts/members/` za sekcijo "members". Vsaka sekcija v tematski mapi ima lahko svoje posebne postavitve.

---

### 6.2 Urejanje in dodajanje lastnih postavitev

Če želite prilagoditi postavitev za specifično stran ali sekcijo na vašem spletnem mestu, imate dve možnosti:

#### 1. Uporaba privzetih postavitev (v `sujt_theme/layouts/_default/`):
   - Ta pristop je primeren, če želite spremeniti postavitev za vse strani, ki uporabljajo privzete postavitve.
   - Na primer, če želite spremeniti način prikaza vseh strani z **_index.md**, lahko uredite **list.html**.

#### 2. Uporaba lastnih prilagoditev v **layout** mapi vašega projekta:
   - Priporočeno je, da za spremembe postavitev, specifične za določeno stran ali sekcijo, uporabite **layout** mapi znotraj vašega projekta, ne pa urejate tematskih map (kot je `sujt_theme/layouts`), saj bodo te spremembe veljale le za vašo stran.
   
   - Na primer, če želite imeti posebno postavitev za stran "lecturing", vstavite datoteko z lastno postavitvijo v mapo `layouts/lecturing/`.
   

#### Primer:
   - Če želite ustvariti lastno postavitev za stran `content/lecturing/subject1.md`, ustvarite datoteko `layouts/lecturing/single.html`. Ta datoteka bo over-ridala **single.html** iz `sujt_theme/layouts/_default/` samo za stran v mapi **lecturing**.

---

### 6.3 Dodajanje in prilagoditev CSS

Če želite prilagoditi slog vaše strani, na primer, dodati lastne barve, pisave ali razmike, lahko spremenite CSS.

1. **Dodajanje CSS v vašo stran**:
   - Ustvarite datoteko `static/css/custom.css`.
   
   - Povežite to datoteko s svojo stranjo, na primer z dodajanjem naslednjega v **head** tag vašega layouta (npr. v `layouts/partials/head.html`):
     ```html
    <link rel="stylesheet" type="text/css" href="{{ "css/custom.css" | relURL}}" />
     ```

2. **Uporabite CSS za prilagoditev stilov**:
   - V datoteki **custom.css** lahko dodate svoje sloge, kot so:
     ```css
     body {
         background-color: #f0f0f0;
     }

     .custom-class {
         font-size: 16px;
         color: #333;
     }
     ```

3. **Ne spreminjajte neposredno tematskih datotek**:
   - Za posodobitve in enostavno vzdrževanje je najbolje, da vse prilagoditve CSS naredite v **static/css** mapi vašega projekta, kot je prikazano zgoraj.
   - Spremembe v datotekah znotraj teme (kot so `sujt_theme/static/css/`) bodo izgubljene ob naslednjih posodobitvah teme.

### 6.4 Uporaba CSS razredov znotraj Markdown vsebine

Če želite uporabiti svoje CSS razrede znotraj vsebine (npr. v tabelah ali slikah), lahko uporabite HTML znotraj Markdown.

- Primer: Dodajanje slike z lastnim razredom za stilizacijo:
  ```markdown
  <img src="/ime-priimek/img/placeholder.jpg" class="custom-class" style="width: 100%; margin-bottom: 20px;" />


## 7. GitHub Actions: Samodejna gradnja in objava

Ko naredite spremembe na svoji strani in jih naložite v GitHub, ni potrebno ročno graditi strani ali jih nalagati na strežnik. Za to skrbi datoteka z GitHub Actions, ki se nahaja v **.github/workflows/hugo.yaml**.

### Kaj dela ta datoteka:

- Ob vsakem "push" na glavno vejo (**main**) se vaša stran samodejno zgradi in objavi.

- Uporablja Hugo za gradnjo statične strani in jo nato objavi na GitHub Pages.

- Postopek zajema namestitev Hugo, sestavo statične strani in objavo na GitHub Pages, kjer bo vaša stran dostopna.

Zato vam ni treba skrbeti za ročno upravljanje strežnika ali nalaganje strani. Vse se dogaja samodejno ob vsaki spremembi, ki jo pošljete v svoj repozitorij.

## 8. Posodabljanje in objavljanje

Po urejanju datotek in ustvarjanju novih vsebin, zaženite naslednje ukaze, da pošljete spremembe v repozitorij:

```bash
git add .
git commit -m "Dodana nova stran in objava"
git push
```

To bo sprožilo postopek gradnje in objave preko GitHub Actions. Vaša stran bo posodobljena in dostopna na naslovu: https://sujt.fri.uni-lj.si/ime.priimek/.
