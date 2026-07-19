# Uticaj spektralnog tipa zvezde na klasifikaciju egzoplaneta u habitabilnoj zoni

![UBMATF](https://img.shields.io/badge/MASS--UBMATF-Astrostatistics_2026-slateblue)

## Kratak opis projekta

Ovaj projekat ispituje kako spektralni tip matične zvezde utiče na
klasifikaciju potvrđenih egzoplaneta u habitabilnoj zoni.

Podaci o planetama i njihovim matičnim zvezdama automatski se preuzimaju
iz tabele `pscomppars` baze NASA Exoplanet Archive.

Za svaku planetu računaju se granice konzervativne i optimistične
habitabilne zone prema modelu Kopparapu et al. Na osnovu položaja orbite
u odnosu na izračunate granice, planete se svrstavaju u odgovarajuće
kategorije habitabilne zone.

Posebno se ispituje da li se učestalost planeta u habitabilnoj zoni
razlikuje između zvezda spektralnih tipova M, K, G i F.

## Način klasifikacije planeta

Za računanje granica habitabilne zone koriste se:

- efektivna temperatura matične zvezde;
- luminoznost matične zvezde;
- velika poluosa orbite planete.

Najpre se za svaku granicu računa efektivni zvezdani fluks:

```text
S_eff = S_eff,Sun + aT* + bT*² + cT*³ + dT*⁴
```

gde je:

```text
T* = T_eff - 5780 K
```

Udaljenost odgovarajuće granice habitabilne zone zatim se računa kao:

```text
d = sqrt[(L / L_Sun) / S_eff]
```

U analizi se koriste četiri granice:

- `Recent Venus` — optimistična unutrašnja granica;
- `Runaway Greenhouse` — konzervativna unutrašnja granica;
- `Maximum Greenhouse` — konzervativna spoljašnja granica;
- `Early Mars` — optimistična spoljašnja granica.

Planeta pripada konzervativnoj habitabilnoj zoni kada se njena velika
poluosa nalazi između granica `Runaway Greenhouse` i
`Maximum Greenhouse`.

Optimistična habitabilna zona prostire se između granica
`Recent Venus` i `Early Mars`.

Planete izvan ovih granica dodatno se klasifikuju kao previše bliske
ili previše udaljene od matične zvezde.

## Procena nesigurnosti

U projektu se koriste dve statističke metode:

### Bootstrap metoda

Bootstrap uzorkovanje koristi se za procenu nesigurnosti udela planeta
u konzervativnoj i optimističnoj habitabilnoj zoni.

### Monte Carlo metoda

Monte Carlo simulacije koriste merne nesigurnosti efektivne temperature,
luminoznosti zvezde i velike poluose orbite.

Za svaku planetu generiše se veliki broj mogućih realizacija parametara,
nakon čega se računa verovatnoća da planeta pripada konzervativnoj ili
optimističnoj habitabilnoj zoni.

## Tok analize

1. Automatsko preuzimanje podataka iz NASA Exoplanet Archive.
2. Izbor potrebnih parametara planeta i njihovih zvezda.
3. Uklanjanje redova bez neophodnih podataka.
4. Računanje granica habitabilne zone prema Kopparapu modelu.
5. Klasifikacija planeta prema položaju njihove orbite.
6. Određivanje približnog spektralnog tipa matične zvezde.
7. Bootstrap procena udela planeta u habitabilnoj zoni.
8. Monte Carlo analiza uticaja mernih nesigurnosti.
9. Poređenje rezultata za spektralne tipove M, K, G i F.
10. Vizuelno prikazivanje rezultata.

## Struktura repozitorijuma

```text
.
├── projekat_proba.ipynb
├── requirements.txt
└── README.md
```

- `projekat_proba.ipynb` — glavni notebook sa kodom, analizom i rezultatima;
- `requirements.txt` — spisak Python paketa potrebnih za pokretanje;
- `README.md` — opis projekta i uputstvo za pokretanje.

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

1. otvoriti fajl `projekat_proba.ipynb`;
2. izabrati `Kernel`;
3. izabrati `Restart Kernel and Run All Cells`;
4. sačekati da se sve ćelije izvrše.

Za preuzimanje podataka potrebna je internet veza.

## Provera notebook-a

Provera da li se notebook izvršava od početka do kraja:

```bash
pytest --nbmake --nbmake-timeout=60 projekat_proba.ipynb
```

Provera kvaliteta koda:

```bash
nbqa pylint projekat_proba.ipynb
```

Notebook se uspešno izvršava od prve do poslednje ćelije, a ostvarena
Pylint ocena je 9.96/10 bez `E` poruka.

## Reproduktivnost

Svi importi nalaze se u prvoj kodnoj ćeliji.

Za slučajne simulacije koristi se fiksiran random seed kako bi se pri
ponovnom pokretanju dobijali reproduktivni rezultati.

Notebook ne zahteva unos korisnika niti ručnu intervenciju tokom
izvršavanja.

## Izvor podataka

Podaci se preuzimaju iz javne baze NASA Exoplanet Archive, iz tabele
`pscomppars`.

## Autor

Tamara Brujić  
Matematički fakultet, Univerzitet u Beogradu  
Astrostatistika, 2026.