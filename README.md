# Mikroservisi RNAEP v1.0

## FastAPI Aplikacija sa Redis Streams integracijom

Ovaj repozitorijum sadrži kod sa IV časa vežbi na predmetu Razvoj naprednih aplikacija elektronskog poslovanja. Aplikacija je napisana u FastAPI Python web okviru i demonstrira integraciju sa Redis Streams, što je funkcionalnost Redis baze podataka koja omogućava obradu tokova podataka u realnom vremenu.

FastAPI je okvir koji se temelji na standardima kao što su OpenAPI i JSON Schema, što ga čini brzim i lakim za korišćenje. On automatski generiše dokumentaciju API-ja, što olakšava razvoj i testiranje. Redis, s druge strane, je brza baza podataka koja se često koristi za keširanje i obradu poruka. Redis Streams je specifična struktura podataka u Redis-u koja omogućava čuvanje i obradu sekvenci događaja, sličnih logovima ili redovima poruka, ali sa mogućnošću čitanja istorijskih podataka i paralelne obrade.

Projekat ilustruje kako se može koristiti FastAPI za kreiranje endpoint-a koji interaguju sa Redis Streams, omogućavajući slanje i primanje poruka u realnom vremenu. Ovo je korisno za scenarije kao što su notifikacije, obrada logova ili distribuirani sistemi.

## Instalacija

Da biste instalirali projekat, pratite ove korake:

1. **Klonirajte repozitorijum**: Preuzmite kod sa GitHub-a ili kopirajte datoteke u lokalni direktorijum.
   
2. **Instalirajte Python**: Osigurajte da imate Python verziju 3.7 ili noviju instaliranu na vašem sistemu. Python je programski jezik koji se koristi za izvršavanje ovog projekta.

3. **Kreirajte virtuelno okruženje**: Otvorite terminal i izvršite sledeće komande:
   ```
   python -m venv venv
   source venv/bin/activate  # Na Windows-u: venv\Scripts\activate
   ```
   Virtuelno okruženje je izolovani prostor gde se instaliraju zavisnosti projekta, kako ne bi uticale na druge projekte na vašem računaru.

4. **Instalirajte zavisnosti**: U aktiviranom virtuelnom okruženju, instalirajte potrebne biblioteke koristeći pip, upravljač paketima za Python:
   ```
   pip install fastapi uvicorn redis
   ```
   - FastAPI: Okvir za API.
   - Uvicorn: Server za pokretanje FastAPI aplikacija, zasnovan na ASGI standardu (asinhroni server gateway interface).
   - Redis: Klijent biblioteka za povezivanje sa Redis bazom podataka.

**Bitna napomena:** Za instalaciju zavisnosti se može koristiti i requirements.txt - komanda `pip install -r requirements.txt` (Virtuelno okruženje mora biti aktivno).

5. **Instalirajte Redis**: Preuzmite i instalirajte Redis server sa zvaničnog sajta (redis.io). Pokrenite Redis server na podrazumevanom portu 6379. Redis je baza podataka koja radi u memoriji i koristi se ovde za čuvanje tokova podataka.

**Bitna napomena:** U okviru termina vežbi, povezivali smo se na Redis Cloud platformu. Potrebno je da na platformi napravite vaš korisnički nalog, kreirate bazu podataka i da aplikaciji prosledite naziv servera, baze i lozinku radi konekcije na Redis Cloud.

## Pokretanje

1. **Pokrenite Redis server**: U terminalu izvršite `redis-server` da biste pokrenuli Redis bazu podataka (Ukoliko ne koristite Cloud distribuciju Redis baze).

2. **Pokrenite aplikaciju**: U virtuelnom okruženju, izvršite:
   ```
   uvicorn main:app --reload
   ```
   Ovo će pokrenuti FastAPI aplikaciju na adresi `http://127.0.0.1:8000`. Parametar `--reload` omogućava automatsko ponovno učitavanje koda prilikom promena, što je korisno tokom razvoja.

3. **Pristupite dokumentaciji**: Otvorite pregledač i idite na `http://127.0.0.1:8000/docs` da vidite automatski generisanu dokumentaciju API-ja, zasnovanu na OpenAPI standardu.

