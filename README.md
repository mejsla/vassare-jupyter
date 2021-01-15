# vassare-jupyter
Vässardag om Jupyter notebooks

> Föreslå ett ämne eller tema.

Introduktion till Jupyter Notebook och hur python används med det verktyget.

> Fundera över syfte och mål. Vad vill du förmedla? Vad ska publiken få med sig?

- Ge en kunskap om vad Jupyter Notebook är.
- Ge en liten hands-on erfarenhet över att sätta upp en Jupyter Notebook och använda det.
- Ge introduktion till relaterade verktyg - NumPy, Pandas, något plot-verktyg, något om ML?
- Göra deltagarna intresserade av kommande studiecirkel.

> Önska hur lång tid du vill ha för din tapas.

Tror vi oss kunna fylla tre timmar? To be decided shortly perhaps. Med lite hands-on kan ju tiden dra iväg (och hellre säga för lång tid och avsluta i förtid än tvärtom).

## Vad är Jupyter Notebook?
Jupyter Notebook kan beroende på kontext avse två saker:

- En webapplikation implementerad i Python för att redigare dokument innehållandes livekod, interaktiva widgets, ekvationer, visualiseringar och generell markdown.
- De dokument som redigeras av ovanstående webapplikation.

För tydlighets skull kommer vi här använda begreppet `Notebook Server` för webapplikationen, och `Notebook dokument` för filer med det aktuella filformatet.

## Installera Notebook Server?
TODO: Ska vi göra det här? Kommer vara problem med folks python-miljöer. Men personligen tycker jag det är trevligt att börja i den änden.

För att installera Notebook server, se till att ha Python 3 installerad och kör:

```sh
pip3 install notebook
```

TODO: Vänta in och hjälp folk här? Me

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

För att skapa ett första Notebook dokument, välj `New`-knappen uppe till höger, och sedan `Python 3` alternativet i den meny som fälls ut.

Du redigerar nu ett Notebook dokument. Välj `File` > `Save as`, skriv in `firstnotebook` som filnamn och tryck `Save`.

Det resulterar i filen `firstnotebook.ipynb`.

