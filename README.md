# VTEAM Project

> Detta är huvud-repot för VTeam-projektet som hanterar övergripande systeminställningar och körning med Docker Compose. Detta repo innehåller en docker-compose.yml-fil som startar frontend- och backend-tjänsterna och tillhandahåller grunden för att utveckla och testa projektet lokalt.

### Om Projektet

VTeam-projektet syftar till att skapa ett system för att hantera uthyrning av elsparkcyklar i flera olika städer, med funktionalitet för att simulera tusentals cyklar i rörelse. Systemet består av en frontend (webb-app), en mobile-app, en backend och en cykelsimulator för att testa last och funktion.
Komma igång

För att köra projektet lokalt behöver du ha Docker och Docker Compose installerat. När dessa är installerade kan du starta hela systemet med ett enda kommando.
Förutsättningar

    Docker: Installera Docker
    Docker Compose: Installera Docker Compose

### Installation och Körning

Följ dessa steg för att klona repot och köra applikationen lokalt med Docker Compose.

Klona detta repo:

```bash
git clone https://github.com/saei23/vteam.git
cd vteam
```

Klona backend i vteam-mappen:
```bash
git clone https://github.com/Zlyde/backend.git
```

Klona frontend i vteam-mappen:
```bash
git clone https://github.com/Zlyde/frontend.git
```

Klona mobile-app i vteam-mappen:
```bash
git clone https://github.com/Zlyde/mobile-app.git
```

Klona bike-bimulator i vteam-mappen:
```bash
git clone https://github.com/saei23/bike-simulator.git
```

Starta tjänsterna med Docker Compose när du står i vteam-mappen:

```bash
docker-compose up --build
```

Detta kommando bygger och startar alla tjänster som definieras i docker-compose.yml.

Stoppa tjänsterna: För att stoppa och ta bort containrarna, använd:
```bash
    docker-compose down
```
Efter att tjänsterna startat kan du nå frontend och backend på följande URL:er:
``` bash
    Frontend: http://localhost:3000
    Mobile-app: http://localhost:5173
    Backend: http://localhost:5001
```

### Struktur och Tjänster

Docker Compose är inställt för att starta följande tjänster:

backend: Backend-tjänsten, byggs från backend mappen. Den lyssnar på port 5001.
frontend: Frontend-tjänsten, byggs från frontend mappen. Den lyssnar på port 3000.
mobile-app: Frontend-tjänst, byggs från mobile-app mappen. Den lyssnar på port 5173.
bike-simulator: Simulator, byggs från bike-simulator mappen. Den lyssnar på port 4000 och skickar data till port 5001, datan visas i port 3000.
mongo_database: MongoDB databas, byggs från senaste containern, lyssnar på port 27017.
Alla tjänster körs under samma nätverk, default.

### Miljövariabler

För att styra systemets beteende använder vi miljövariabler i docker-compose.yml. Standardvariablerna som används är:

    NODE_ENV=development
    REACT_APP_BACKEND_URL=http://backend:5001

Om du behöver andra miljövariabler för att köra systemet, kan dessa läggas till direkt i docker-compose.yml-filen under respektive tjänst.
Utvecklingsanteckningar

    Samarbete och kodhantering: Se till att alla ändringar i docker-compose.yml diskuteras och testas gemensamt för att undvika konflikter och säkerställa att hela teamet kan köra systemet konsekvent.
