# TechPlanner - Aplikacja do zarządzania zleceniami serwisowymi

Projekt natywnej aplikacji chmurowej realizowany w architekturze 3-warstwowej.

**Autor:** Paweł Wojciechowski
**Nr studenta:** 95030

## Deklaracja Architektury (Mapowanie Azure)

Ten projekt został zaplanowany z myślą o usługach PaaS (Platform as a Service) w regionie Poland Central.

| Warstwa | Komponent Lokalny | Usługa Azure |
| :--- | :--- | :--- |
| **Presentation** | React 19 (Vite) | Azure Static Web Apps |
| **Application** | Node.js 24 (Express) | Azure App Service |
| **Data** | PostgreSQL (Dev) | Azure SQL Database (Serverless) |

## Status Projektu

* [x] **Artefakt 1:** Zaplanowano strukturę folderów i diagram C4 (dostępny w `/docs`).
* [x] **Artefakt 2:** Konfiguracja środowiska Docker (w trakcie...).

## Opis projektu

Aplikacja webowa wspierająca techników serwisowych w organizacji codziennej pracy.
Pozwala na zarządzanie zleceniami (CRUD), przeglądanie kalendarza tygodniowego
oraz wizualizację trasy dnia na mapie. Dane przechowywane są w chmurze Azure,
co umożliwia dostęp z każdego miejsca.

> **Informacja:** Ten plik będzie ewoluował. W kolejnych etapach dodamy sekcje
> Quick Start, opis zmiennych środowiskowych oraz instrukcję wdrożenia (CI/CD).