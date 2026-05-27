# Event Booking System

Rezervační systém pro kulturní akci konané dne 31.12.2027 od 19:00.

## Architektura

Projekt se skládá ze dvou částí:

- **Frontend**: React SPA (TypeScript + Vite + MUI)
- **Backend**: ASP.NET Core 9 REST API

## Požadavky

### Frontend
- Node.js 18+
- npm/yarn

### Backend
- .NET 9 SDK
- SQLite (zabudované)

## Instalace a spuštění

### 1. Frontend

```bash
cd frontend
npm install
npm run dev
```

Aplikace bude dostupná na http://localhost:5173

### 2. Backend

```bash
cd backend
dotnet restore
dotnet ef database update
dotnet run
```

API bude dostupné na http://localhost:5000

## Struktura projektu

```
event-booking-system/
├── frontend/                 # React + TypeScript + Vite
│   ├── src/
│   │   ├── components/      # React komponenty
│   │   ├── pages/           # Stránky
│   │   ├── services/        # API služby
│   │   ├── types/           # TypeScript typy
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── vite.config.ts
│   └── package.json
├── backend/                  # ASP.NET Core 9
│   ├── Controllers/
│   ├── Models/
│   ├── Services/
│   ├── Data/
│   ├── appsettings.json
│   ├── Program.cs
│   └── EventBooking.csproj
└── README.md
```

## Funkcionality

### Frontend
- ✅ Wizard pro rezervace (3 kroky)
- ✅ Vytvoření nové rezervace
- ✅ Editace rezervace přes kód
- ✅ Zrušení rezervace
- ✅ Validace polí (email, telefon, počet lístků)
- ✅ Responsivní design (MUI)

### Backend
- ✅ REST API pro správu rezervací
- ✅ SQLite databáze
- ✅ Audit logging (IP, User-Agent, čas, operace)
- ✅ IoC kontejner
- ✅ Konfigurace z env. proměnných
- ✅ Max. 100 lístků na akci
- ✅ Max. 10 lístků na rezervaci

## Konfigurace

### Frontend (.env.local)
```
VITE_API_URL=http://localhost:5000
```

### Backend (appsettings.json)
```json
{
  "EventSettings": {
    "MaxTicketsPerReservation": 10,
    "TotalAvailableTickets": 100,
    "EventDate": "2027-12-31T19:00:00Z"
  }
}
```

## API Endpoints

- `POST /api/reservations` - Vytvoření rezervace
- `GET /api/reservations/{code}` - Získání rezervace
- `PUT /api/reservations/{code}` - Aktualizace rezervace
- `DELETE /api/reservations/{code}` - Zrušení rezervace
- `GET /api/event/availability` - Dostupné lístky

## Bezpečnost

- Audit logging všech operací
- Zaznamenávání IP adresy a User-Agent
- Validace vstupních dat
- CORS konfigurován

## Poznámky

- Autentifikace není implementována (dle požadavků)
- Data se ukládají do SQLite
- Rezrevační kód je generován jako UUID

## Autor

PavJel

## Licence

MIT
