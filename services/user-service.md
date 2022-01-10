# User service

De User Service beheert het opslaan van alle user data die niet gebonden is aan de authenticatie. Vooral persoonlijke informatie (NAW, leeftijd, bio)

De User Service bevat API endpoints voor accesses van de user data. Ook luistert de user service naar een rabitmq message voor het aanmaken van een user. Dit is een bericht dat de authentication service aanmaakt.

## Technologie

De user service is gebouwd met behulp van C# en het Dotnet- en Entity Framework. Dit laatste framework verzorgt de opslag in de database om zo de gebruikers te beheren.

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/UserService.
