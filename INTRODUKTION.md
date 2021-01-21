## Vad är Jupyter Notebook?
Börja med att skärmdela hemsidan jupyter.org.

Jupyter Notebook kan beroende på kontext avse två saker:

- En webapplikation implementerad i Python för att redigare dokument innehållandes livekod, interaktiva widgets, ekvationer, visualiseringar och generell markdown.
- De dokument som redigeras av ovanstående webapplikation.

För tydlighets skull kommer vi här använda begreppet `Notebook Server` för webapplikationen, och `Notebook dokument` för filer med det aktuella filformatet. Men i allmänhet, i artiklar och dokumentation på Internet, kan alltså `Jupyter` avse antingen applikationen eller dokumenten beroende på kontext.

`Jupyter` utvecklas av `Project Jupyter`, ett framgångsrikt open source projekt. Inom projektet (scrolla ner på hemsidan) finns ryms det också `JupyterLab`, vilket är "nästa generation av `Notebook Server` - ny backend, nytt gränssnitt och nya features, men grundläggande modell kommer vara kvar -  och `Voilá`, vilket är ett ramverk för att transformera en notebook till en webapplikation. Vi kommer inte gå in på dessa, men är man intresserad kan man läsa mer på hemsidan jupyter.org.

## Installera Notebook Server
(Växla skärmdelning till terminal)

För att installera Notebook server, se till att ha Python 3 installerad och kör:

```sh
pip3 install notebook
```

Vänta folk? Erbjud backup-länk: https://notebooks.gesis.org/binder/v2/gh/mejsla/vassare-jupyter/HEAD?filepath=empty.ipynb

## Skapa ett första Notebook dokument
Skapa och gå till en tom katalog:

```sh
mkdir ~/first-jupyter
cd ~/first-jupyter
```

Starta Notebook Server med: ```jupyter notebook```. Borde resultera i output som:

> Jupyter Notebook 6.2.0 is running at:
> http://localhost:8888/?token=...

Om webläsaren inte öppnats automatiskt, gå till `http://localhost:8888`. Borde se ut som nedan:

![Screenshot på Notebook Server i tom katalog](bilder/tom-notebook-server.png)

Det här är filhanterar-delen av Jupyter, även kallad Jupyter Dashboard. Eftersom vi startat servern i en tom katalog listas inga filer.

För att skapa ett första Notebook dokument, välj `New`-knappen uppe till höger, och sedan `Python 3` alternativet i den meny som fälls ut. Du redigerar nu ett Notebook dokument. Och skärmen bör se ut som nedan:

![Screenshot på nytt dokument](bilder/nytt-dokument.png)

Välj `File` > `Save as`, skriv in `firstnotebook` som filnamn och tryck `Save`.

Det resulterar i filen `firstnotebook.ipynb`, där `.ipynb` (från `IPython Notebook`) är file extensions för Jupyter Notebooks. Filformatet använder JSON, men det är mer av en implementationsdetalj än något de flesta använder sig av.

## Celler
Ett Notebook dokument består av celler, som kan vara av två typer:

- Celler innehållandes Markdown, som kan användas för formatterad text, bilder, videos och annat - i princip godtycklig HTML. 
- Celler inehållandes exekverbar python kod, där output (som kan vara exempelvis text, tabeller, bilder, grafer, ...) från koden hamnar precis under. Man kan se skillnad på markdown och kod-celler genom att de för kod innehåller labels (`In [...]` och `Out [...]` till vänster), och markdown inte gör det.

I det initiala dokument vi skapat finns initialt en tom kodcell. Fyll i python koden `2+1` i denna och tryck på `Play`-knappen (eller använd keyboard shortcut -  `Shift+Enter` på Windows+Linux, `Ctrl+Enter` på macOS) för att exekvera koden. Skärmen bör nu se ut som:

![Ett dokument där 2+1 precis körts](bilder/tva-plus-ett.png).

Notera följande:

- Medan koden körs markeras sektionen med `In [*]`.
- Output från koden syns sedan nedanför koden, i `Out`-sektionen.
- Det visas en exekveringsordning (`In/Out [1]` här, eftersom det var första koden som kördes). 
- Hade vi modifierat globalt scope, genom att t.ex. definiera top level variables eller importera beroenden, hade dessa varit gjorts tillgängliga för senare exekveringar.

En viktig aspekt är följande:

- Exekveringsordning spelar roll, och är inte nödvändigtvis i ordningen uppifrån och ner.
- Vid experiment hoppar man ofta runt.
- Bra praxis att avsluta att med kontroll att det går att köra i ordningen uppifrån och ner.

## Edit och Command mode
Editorn för en Notebook kan vara i två lägen:

- `Edit mode`, "textredigeringsläge", där text redigeras direkt.
- `Command mode`, där tangenter leder till kommandon.
 
 Likt vim editorn. Vilket läge som editorn är i markeras på två sätt:
 
 - Genom en ikon som ser ut som en penna.
![Penn-ikonen som indikerar edit mode](bilder/penna-i-edit.png)
- Genom att den markerade cellen är _grön_ vid edit, och _blå_ i command mode.
![Grön cell i Edit mode](bilder/gron-vid-edit.png)
![Blå cell i Command mode](bilder/bla-vid-command.png)

## Command palette
En trevlig funktionalitet för att lära sig editorn är Command palette - en dialog som listar alla kommandon, där fritext kan användas för att söka och sedan exekvera ett kommando. Lägg märke till att keyboard shortcuts visas i denna dialog, vilket gör det till bra verktyg för att lära sig keyboard shortcuts.

Aktivera detta genom att trycka på Keyboard-ikonen i Toolbar eller använda `Ctrl+Shift+P` / `Cmd+Shift+P`.

## Några keyboard shortcuts
I Command mode:

- Växla till Edit läge genom Enter (och sedan tillbaks till Command med Escape).
- `H` för att visa `Help`, lista över kommandon (stäng med `Escape`).
- Flytta fokus till nästa eller föregående cell med Up och Ner-piltangenterna (`J` och `K` fungerar också).
- `M` för att göra om kodcell till markdown, och `Y` för det omvända.
- `D+D` (`D` två gånger) för att ta bort cell.
- `Z` för att göra Undo efter att ha tagit bort cell av misstag.
- Håll inne `Shift` och använda piltangenter (eller J/K), eller mus, för att markera flera celler. `Shift+M` kan sen användas för att slå samman flera celler till en markdown-cell.
- `O` för att toggla ifall output för cellen ska visas.

## Snabb intro till markdown
Visa snabbt grundläggande markdown (heading, lista, kod, bild), för de som inte är bekväma med markdown, och visar också hur markdown kan redigeras i jupyter?

- Precis som `Shift+Enter` kör en kod-cell, så "kör" det en markdown cell genom att gå från redigeringsläge till renderat läge. Tryck `Enter` eller dubbelklicka i cellen för att redigera cellen igen.
  - Vid initial laddning av dokument kommer alla markdown-celler vara i renderat läge - dokumentet kommer inte komma ihåg vilka celler som är i Edit mode.
  
## Kernel
"Kärnan" i ett dokument innehåller state för dokumentet (deklarerade variabler och funktioner, importerade bibliotek). Gemensamt hela dokumentet, inte scope:at till celler.

Menyn `Kernel` har några användbare alternativ:

- `Interrupt` för att avbryta kod som körs.
  - Testa att lägga in `import time; time.sleep(1000)` och kör (`Shift+Enter`). Lägg märke till att den aktiva cellen markeras med `In [*]` medan den körs. Kärnan är nu upptagen, och andra kodceller som exekveras måste vänta. `Kernel > Interrupt` räddar den här situationen.
- `Restart` för att återställa kärnan till initialt läge (ta bort alla deklarerade variabler och funktioner osv).
  - Illustrera genom att ha en cell med `y=10`, och en andra med bara `y`. Köra dessa i följd och visa att `y`-cellen ger `10` som output. Gör en `Restart`, och kör om `y`-cellen. Vi får nu fel för att `y` inte är definierad.
- `Restart & Clear Output` - som `Restart`, men tar dessutom bort alla output-delar.
  - Visa.
- `Restart & Run All` - som ovanstående `Restart & Clear Output`, men kör dessutom alla kodceller en efter en 
  - Kör några celler, och sedan `Restart & Run All` för att visa vad som händer.
  - Bra för att kontrollera att dokumentet fungerar som förväntat och är reproducerbart, och inte beror på kod som inte längre finns (eller en exekveringsordning av celler som inte är från toppen till botten).
  
## Spara dokument
- Av default sparas dokument var 120:e sekund.
- `Ctrl+S` / `Cmd+S` för att spara explicit.
- Titta på `Last Checkpoint: a few seconds ago` raden högst upp för bekräftelse.
- `File` > `Revert to Checkpoint` för att gå tillbaks till sparad version.
- När dokument blir större, överväg versionshantering (git).

## Export av dokument
Via `File` > `Download as` menyn kan dokumentet exporteras.

- `AsciiDoc`/`HTML`/`LaTex`/`Markdown`/`PDF`/`reStructuredText`/`Reveal.js slides` för statisk export.
  - Beroende på publik kan det vara ett bättre alternativ att dela med sig av notebook direkt (vi kommer visa det inbyggda stödet i GitHub och Gists strax).
- `Notebook (.ipynb)` - laddar ner själva notebook-dokumentet.
- `Python (.py)` - slår ihop alla celler till en hel, med markdown-celler som kommentarer, och kodceller som kod i ordningen uppifrån och ner.

## Delning av dokument via GitHub och Gists
Gist är "snabb delning av kodsnippets" via en tjänst hos GitHub på https://gist.github.com/.

Visa hur read-only dokument kan delas snabbt via Gist:

- Använd `File` > `Download as` > `Notebook (.ipynb)` för att få en `.pynb` fil nedladdad.
- Gå till gist.github.com
- Dra filen till textarean - filnamn och filinnehåll populeras automatiskt.
- Spara och titta på skapada gist:en.
- Obs att det är versionshanterat och kan uppdateras som vanligt.

Nämn att det här läget finns också för `.pynb` filer incheckade i ett git-repo som finns på github.

Nämn att `.ipynb_checkpoints` filen bör läggas i `.gitignore` när man jobbar med notebooks och git.

## Magic commands
Magic commands i Jupyter tillåter en del spännande och användbar funktionalitet.

Det finns två typer av magiska kommandon:
- `Line magics` som påverkar en rad i en kodcell och startar med `%` (ett procenttecken).
- `Cell magics` som påverkar en hel kodcell och startar med `%%` (två procenttecken).

För att lista alla magics (både line och cell), skriv `%lsmagic` (självt ett line magic) i en cell och kör denna. Alla tillgängliga magic kommandon listas, bör se ut något som:

```
Available line magics:
%alias  %alias_magic  %autoawait  %autocall  %automagic  %autosave  %bookmark  %cat  %cd  %clear  %colors  %conda  %config  %connect_info  %cp  %debug  %dhist  %dirs  %doctest_mode  %ed  %edit  %env  %gui  %hist  %history  %killbgscripts  %ldir  %less  %lf  %lk  %ll  %load  %load_ext  %loadpy  %logoff  %logon  %logstart  %logstate  %logstop  %ls  %lsmagic  %lx  %macro  %magic  %man  %matplotlib  %mkdir  %more  %mv  %notebook  %page  %pastebin  %pdb  %pdef  %pdoc  %pfile  %pinfo  %pinfo2  %pip  %popd  %pprint  %precision  %prun  %psearch  %psource  %pushd  %pwd  %pycat  %pylab  %qtconsole  %quickref  %recall  %rehashx  %reload_ext  %rep  %rerun  %reset  %reset_selective  %rm  %rmdir  %run  %save  %sc  %set_env  %store  %sx  %system  %tb  %time  %timeit  %unalias  %unload_ext  %who  %who_ls  %whos  %xdel  %xmode

Available cell magics:
%%!  %%HTML  %%SVG  %%bash  %%capture  %%debug  %%file  %%html  %%javascript  %%js  %%latex  %%markdown  %%perl  %%prun  %%pypy  %%python  %%python2  %%python3  %%ruby  %%script  %%sh  %%svg  %%sx  %%system  %%time  %%timeit  %%writefile

Automagic is ON, % prefix IS NOT needed for line magics.
```

Exempel på några användbara magics:

- `%pip` - kör `pip`, pakethanteraren i python. Exempel (som bör ge `<Response [200]>` i output):

```python
%pip install requests
import requests
requests.get('https://example.com')
```

- `%%javascript` - kör cellen som javascript-kod i browsen. Exempel:

```
%%javascript
alert(navigator.userAgent)
```

- `%time` - skriv ut hur lång tid en rad tar att köra. Exempel:

```
import random
L = [random.random() for i in range(100000)]
print("sorting an unsorted list:")
%time L.sort()
```

- `%html` - inkludera godtycklig HTML. Exempel:

```
%%html
<a href="example.com#>Link</a>
```

- `%latex` - Inkludera LaTeX för formler. Exempel:

```
%%latex
Some important equations are $E = mc^2$ and $e^{i pi} = -1$
```

- `%pdb` - toggla om `pdb`, pythons debugger ska användas. Exempel:

```
map = {0: 10, 1: 20, 3: 30}
%pdb
# När pdb används kommer vi få en pdb-prompt vid exception, där vi kan inspektera variable som i:
for i in range(0,3): print(map[i])
```

## Shell kommandon
Som i generell Python kan externa program eller kommandon köras via [subprocess](https://docs.python.org/3/library/subprocess.html). Men det finns en genväg som är smidig, genom att inleda rader med utropstecken:

```
!ls -lha /
!uname -a
```

Python-variabler kan användas genom att använda ett dollartecken:

```
message = "Hello, world"
!echo $message
```
