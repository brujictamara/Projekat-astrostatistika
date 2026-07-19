# Uticaj spektralnog tipa zvezde i metode detekcije na klasifikaciju egzoplaneta u habitabilnoj zoni prema Kopparapu modelu

![UBMATF](https://img.shields.io/badge/MASS--UBMATF-Astrostatistics_2026-slateblue)

## Kratak opis projekta

Ovaj projekat analizira potvrđene egzoplanete iz baze _NASA Exoplanet
Archive_ i ispituje kako njihova klasifikacija u habitabilnoj zoni zavisi
od spektralnog tipa matične zvezde i metode detekcije.

Granice konzervativne i optimistične habitabilne zone određuju se prema
Kopparapu modelu, na osnovu efektivne temperature i luminoznosti zvezde,
a zatim se porede sa velikom poluosom orbite planete iz kataloga.

Stabilnost rezultata proverava se bootstrap metodom i Monte Carlo
propagacijom neodređenosti merenja. Rezultati se porede sa radom
_Jiang et al. (2024)_, ali se umesto klasifikacije prema procenjenoj
površinskoj temperaturi koriste fizički modelovane Kopparapu granice.

U analiziranom katalogu **M zvezde** imaju **najveći relativni udeo HZ
kandidata**, dok **metoda radijalnih brzina daje više kandidata od tranzitne
metode**. Rezultati se tumače uzimajući u obzir selekcione efekte metoda
detekcije i nereprezentativnost kataloga potvrđenih egzoplaneta.


## Struktura repozitorijuma

* `projekat.ipynb` — glavni notebook sa kodom, analizom i rezultatima;
* `requirements.txt` — spisak Python paketa potrebnih za pokretanje;
* `README.md` — opis projekta i uputstvo za pokretanje.
* `.gitignore` — spisak lokalno generisanih fajlova koji se ne postavljaju
  na GitHub.

Podaci nisu sačuvani kao poseban fajl jer se automatski preuzimaju iz
javne baze NASA Exoplanet Archive.

## Instalacija potrebnih paketa

Otvoriti terminal u folderu projekta i pokrenuti:

```bash
python -m pip install -r requirements.txt
```

## Pokretanje projekta

Pokrenuti Jupyter Notebook:

```bash
jupyter notebook
```

Zatim:

1. otvoriti fajl `projekat.ipynb`;
2. izabrati `Kernel`;
3. izabrati `Restart Kernel and Run All Cells`;
4. sačekati da se sve ćelije izvrše.

Za preuzimanje podataka potrebna je internet veza.