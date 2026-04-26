# FastAPI Aplikacija sa Redis Streams

## Opis Projekta

Ovaj projekat predstavlja jednostavnu veb aplikaciju izgrađenu koristeći FastAPI, moderan okvir za izgradnju API-ja u programskom jeziku Python. Aplikacija demonstrira integraciju sa Redis Streams, što je funkcionalnost Redis baze podataka koja omogućava obradu tokova podataka u realnom vremenu. Projekat je namenjen studentima koji žele da nauče osnove razvoja veb servisa, sa posebnim fokusom na asinhrono programiranje i obradu događaja.

FastAPI je okvir koji se temelji na standardima kao što su OpenAPI i JSON Schema, što ga čini brzim i lakim za korišćenje. On automatski generiše dokumentaciju API-ja, što olakšava razvoj i testiranje. Redis, s druge strane, je brza baza podataka u memoriji koja se često koristi za keširanje i obradu poruka. Redis Streams je specifična struktura podataka u Redis-u koja omogućava čuvanje i obradu sekvenci događaja, sličnih logovima ili redovima poruka, ali sa mogućnošću čitanja istorijskih podataka i paralelne obrade.

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
   Virtuelno okruženje je izolovano prostor gde se instaliraju zavisnosti projekta, kako ne bi uticale na druge projekte na vašem računaru.

4. **Instalirajte zavisnosti**: U aktiviranom virtuelnom okruženju, instalirajte potrebne biblioteke koristeći pip, upravljač paketima za Python:
   ```
   pip install fastapi uvicorn redis
   ```
   - FastAPI: Okvir za API.
   - Uvicorn: Server za pokretanje FastAPI aplikacija, zasnovan na ASGI standardu (asinhroni server gateway interface).
   - Redis: Klijent biblioteka za povezivanje sa Redis bazom podataka.

5. **Instalirajte Redis**: Preuzmite i instalirajte Redis server sa zvaničnog sajta (redis.io). Pokrenite Redis server na podrazumevanom portu 6379. Redis je baza podataka koja radi u memoriji i koristi se ovde za čuvanje tokova podataka.

## Pokretanje

1. **Pokrenite Redis server**: U terminalu izvršite `redis-server` da biste pokrenuli Redis bazu podataka.

2. **Pokrenite aplikaciju**: U virtuelnom okruženju, izvršite:
   ```
   uvicorn main:app --reload
   ```
   Ovo će pokrenuti FastAPI aplikaciju na adresi `http://127.0.0.1:8000`. Parametar `--reload` omogućava automatsko ponovno učitavanje koda prilikom promena, što je korisno tokom razvoja.

3. **Pristupite dokumentaciji**: Otvorite pregledač i idite na `http://127.0.0.1:8000/docs` da vidite automatski generisanu dokumentaciju API-ja, zasnovanu na OpenAPI standardu.

## Korišćenje

Aplikacija pruža endpoint-e za interakciju sa Redis Streams. Na primer:

- **POST /publish**: Šalje poruku u stream. Ovo dodaje novi događaj u Redis Stream, koji se može obraditi asinhrono.

- **GET /consume**: Čita poruke iz stream-a. Ovo demonstrira kako se mogu konzumirati događaji iz Redis Streams, što je korisno za obradu u realnom vremenu.

Testirajte endpoint-e koristeći alatke kao što je Postman ili direktno u pregledaču za GET zahteve.

## Ključne Komponente

### FastAPI

FastAPI je moderan, brz okvir za izgradnju API-ja u Python-u, inspirisan Flask-om i Starlette-om. On koristi tipizaciju (type hints) za automatsku validaciju podataka i generisanje dokumentacije. Asinhrono programiranje, koje FastAPI podržava, omogućava efikasnu obradu više zahteva istovremeno, što je ključno za aplikacije u realnom vremenu. U ovom projektu, FastAPI se koristi za definisanje ruta (endpoint-a) koje interaguju sa Redis-om, pružajući RESTful API interfejs.

### Redis Streams

Redis Streams je struktura podataka uvedena u Redis 5.0, dizajnirana za obradu tokova događaja. Za razliku od tradicionalnih redova poruka, streams omogućavaju čuvanje istorije poruka i paralelnu obradu od strane više konzumenata (consumer-a). Svaki događaj u stream-u ima jedinstveni ID i može sadržati više polja podataka. U ovom projektu, Redis Streams se koriste za slanje i primanje poruka, demonstrirajući koncepte kao što su publisher-subscriber model i obrada u realnom vremenu. Ovo je posebno korisno za aplikacije koje zahtevaju skalabilnu obradu događaja, kao što su sistemi za monitoring ili distribuirane aplikacije.

Za dalje učenje, preporučuje se proučavanje zvanične dokumentacije FastAPI-ja i Redis-a, kao i eksperimentisanje sa kodom ovog projekta.