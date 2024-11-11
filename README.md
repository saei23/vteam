# VTEAM Project

> Detta är huvud-repot för VTeam-projektet som hanterar övergripande systeminställningar och körning med Docker Compose. Detta repo innehåller en docker-compose.yml-fil som startar frontend- och backend-tjänsterna och tillhandahåller grunden för att utveckla och testa projektet lokalt.

### Om Projektet

VTeam-projektet syftar till att skapa ett system för att hantera uthyrning av elsparkcyklar i en stad, med funktionalitet för att simulera tusentals cyklar i rörelse. Systemet består av en frontend, en backend och en eventuell cykelsimulator för att testa last och funktion.
Komma igång

För att köra projektet lokalt behöver du ha Docker och Docker Compose installerat. När dessa är installerade kan du starta hela systemet med ett enda kommando.
Förutsättningar

    Docker: Installera Docker
    Docker Compose: Installera Docker Compose

### Installation och Körning

Följ dessa steg för att klona repot och köra applikationen lokalt med Docker Compose.

Klona detta repo:

```bash
git clone https://github.com/yourusername/vteam.git
cd vteam
```

Starta tjänsterna med Docker Compose:

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
    Backend: http://localhost:5000
```

### Struktur och Tjänster

Docker Compose är inställt för att starta följande tjänster:

backend: Backend-tjänsten, byggs från elspark-backend mappen. Den lyssnar på port 5000.
frontend: Frontend-tjänsten, byggs från elspark-frontend mappen. Den lyssnar på port 3000.

    Notera: docker-compose.yml är konfigurerad för att köra frontend och backend lokalt utan extern databas i detta steg. En cykelsimulator och databas kommer att kunna integreras senare.

### Miljövariabler

För att styra systemets beteende använder vi miljövariabler i docker-compose.yml. Standardvariablerna som används är:

    NODE_ENV=development
    REACT_APP_BACKEND_URL=http://backend:5000

Om du behöver andra miljövariabler för att köra systemet, kan dessa läggas till direkt i docker-compose.yml-filen under respektive tjänst.
Utvecklingsanteckningar

    Utökning av systemet: Detta repo är byggt för att enkelt kunna integrera ytterligare tjänster, som en databas och cykelsimulator.
    Simulering och lasttest: En cykelsimulator kommer att byggas för att simulera tusentals cyklar som interagerar med backend-tjänsten. Simulatorn kan köras som en egen Docker-tjänst och behöver konfigureras för att skicka cykelsimuleringar till backend.
    Samarbete och kodhantering: Se till att alla ändringar i docker-compose.yml diskuteras och testas gemensamt för att undvika konflikter och säkerställa att hela teamet kan köra systemet konsekvent.
