# Cloud App - Aplikacja do zarządzania zadaniami

Projekt natywnej aplikacji chmurowej realizowany w architekturze 3-warstwowej.

**Autor:** Paweł Wojciechowski  
**Nr studenta:** 95030

## Deklaracja Architektury (Mapowanie Azure)

Ten projekt został zaplanowany z myślą o usługach PaaS (Platform as a Service).

| Warstwa | Komponent Lokalny | Usługa Azure |
| :--- | :--- | :--- |
| **Presentation** | React + Vite (Nginx) | Azure Static Web Apps |
| **Application** | .NET 9 (ASP.NET Core) | Azure App Service |
| **Data** | Azure SQL Edge (Docker) | Azure SQL Database |

## Uruchomienie lokalne
```bash
docker compose up -d --build
```

- Frontend: http://localhost:8080
- Backend (Swagger): http://localhost:8081/index.html
- Baza danych: localhost:1433

## Adresy produkcyjne (Azure)

- **Frontend:** https://cloud-task-manager-frontend-95030-fsaegzduczgufmh8.francecentral-01.azurewebsites.net
- **Backend API:** https://cloud-task-manager-api-95030-fchegzgqawg2ggh0.canadacentral-01.azurewebsites.net

## Status Projektu

* [x] **Artefakt 1:** Struktura projektu i konfiguracja środowiska lokalnego.
* [x] **Artefakt 2:** Planowanie architektury trójwarstwowej aplikacji chmurowej.
* [x] **Artefakt 3:** Działająca warstwa prezentacji (React + Vite + Nginx).
* [x] **Artefakt 4:** Działająca warstwa logiki backendu (.NET 9 + REST API + Docker).
* [x] **Artefakt 5:** System gotowy na chmurę (DTO, named volumes, EF Core migrations).
* [x] **Artefakt 6:** Wdrożenie aplikacji w Azure.

## Opis projektu

Aplikacja webowa do zarządzania zadaniami (Task Manager) zbudowana w architekturze
trójwarstwowej. Umożliwia dodawanie, przeglądanie i zarządzanie zadaniami przez
interfejs React. Backend oparty na .NET 9 z REST API i wzorcem DTO zapewnia
stabilny kontrakt API niezależny od struktury bazy danych. Dane przechowywane
są trwale dzięki Docker named volumes, co przygotowuje aplikację do migracji
do Azure SQL Database.

## Stack technologiczny

- **Frontend:** React, TypeScript, Vite, Axios, Nginx
- **Backend:** .NET 9, ASP.NET Core, Entity Framework Core
- **Baza danych:** Azure SQL Edge (lokalnie), Azure SQL Database (produkcja)
- **Infrastruktura:** Docker, Docker Compose

> **Informacja:** W kolejnych etapach dodamy wdrożenie do Azure App Service,
> Azure SQL Database oraz konfigurację RBAC i Firewall.