# Cloud App - Aplikacja do zarządzania zadaniami

Projekt natywnej aplikacji chmurowej realizowany w architekturze 3-warstwowej.

**Autor:** Paweł Wojciechowski  
**Nr studenta:** 95030

---

## Status Projektu

* [x] **Artefakt 1:** Struktura projektu i konfiguracja środowiska lokalnego.
* [x] **Artefakt 2:** Planowanie architektury trójwarstwowej aplikacji chmurowej.
* [x] **Artefakt 3:** Działająca warstwa prezentacji (React + Vite + Nginx).
* [x] **Artefakt 4:** Działająca warstwa logiki backendu (.NET 9 + REST API + Docker).
* [x] **Artefakt 5:** System gotowy na chmurę (DTO, named volumes, EF Core migrations).
* [x] **Artefakt 6:** Wdrożenie aplikacji w Azure.
* [x] **Artefakt 7:** Zabezpieczona aplikacja – Azure Key Vault i Managed Identity.
* [x] **Artefakt 8:** Dokumentacja techniczna API (Swagger UI) dostępna publicznie.

## Adres aplikacji

- **Frontend:** https://cloud-task-manager-frontend-95030-fsaegzduczgufmh8.francecentral-01.azurewebsites.net
- **Backend API (Swagger):** https://cloud-task-manager-api-95030-fchegzgqawg2ggh0.canadacentral-01.azurewebsites.net

---

## 1. Architektura Systemu (High-Level Design)

Aplikacja zbudowana w architekturze trójwarstwowej:

- **Warstwa Prezentacji:** React 19 hostowany w Azure App Service
- **Warstwa Logiki:** .NET 9 zarządzające procesami
- **Warstwa Danych:** Azure SQL Database w modelu Serverless

| Warstwa | Komponent Lokalny | Usługa Azure |
| :--- | :--- | :--- |
| **Presentation** | React + Vite (Nginx) | Azure App Service |
| **Application** | .NET 9 (ASP.NET Core) | Azure App Service |
| **Data** | Azure SQL Edge (Docker) | Azure SQL Database |

---

## 2. Infrastruktura i Bezpieczeństwo Sieciowe

- **Managed Identity:** Kluczowy element architektury – eliminacja haseł w plikach konfiguracyjnych na rzecz tożsamości zarządzanej Azure
- **Key Vault (`kv-cloud-task-manager007`):** Miejsce, w którym przechowywany jest parametr połączenia (`DbConnectionString`), do których dostęp ma tylko Backend

---

## 3. Dokumentacja Wdrożeniowa (DevOps)

Opis procesu automatyzacji, który stworzyliśmy:

- **CI/CD:** Każdy `git push` wyzwala pipeline w GitHub Actions, który buduje kod i deployuje go w Azure
- **Swagger UI:** Dokumentacja API dostępna publicznie pod głównym adresem backendu

---

## 4. Monitoring i Utrzymanie (Observability)

- **Logowanie:** Wszystkie błędy z `Program.cs` trafiają do konsoli Azure Log Analytics
- **Self-Healing:** Opcja `EnableRetryOnFailure` w konfiguracji EF Core – aplikacja automatycznie "budzi" uśpioną bazę danych bez przerywania sesji użytkownika

---

## 5. Słownik Zasobów (Resource Inventory)

| Zasób (Service) | Rola w projekcie | Skala (Tier/SKU) |
| :--- | :--- | :--- |
| **Azure SQL** | Przechowywanie zadań użytkownika | Serverless (General Purpose) |
| **App Service (API)** | Skok aplikacji i logika biznesowa | Free / Basic (B1) |
| **App Service (Web)** | Interfejs użytkownika (React) | Free / Basic (B1) |
| **Key Vault** | Bezpieczny magazyn sekretów i haseł | Standard |

---

## Uruchomienie lokalne

```bash
docker compose up -d --build
```

- Frontend: http://localhost:8080
- Backend (Swagger): http://localhost:8081/index.html
- Baza danych: localhost:1433

---

## Stack technologiczny

- **Frontend:** React, TypeScript, Vite, Axios, Nginx
- **Backend:** .NET 9, ASP.NET Core, Entity Framework Core
- **Baza danych:** Azure SQL Edge (lokalnie), Azure SQL Database (produkcja)
- **Infrastruktura:** Docker, Docker Compose, GitHub Actions
- **Bezpieczeństwo:** Azure Key Vault, Managed Identity
