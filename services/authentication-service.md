# Authentication service

Deze authenticatie service verzorgt de authenticatie voor de GGC website en de Race to Resilience applicatie. 

Zodra een gebruiker zich registreert, wordt de voornaam, achternaam en e-mailadres doorgestuurd door middel van een RabbitMQ eventbus naar de queue van de user- en comment service. Het e-mailadres en wachtwoord worden door de authenticatie service opgeslagen. Als dit allemaal goed gaat, wordt er een JWT gegenereerd voor de gebruiker. Deze wordt terug gestuurd naar de front-end en lokaal opgeslagen.

Bij het inloggen worden de credentials gecontroleerd. Als deze controle slaagt wordt er ook een JWT gegenereerd voor de gebruiker en terug gestuurd naar de front-end en lokaal opgeslagen.

## Technologie

De authenticatie service is gebouwd met behulp van C# en het Dotnet- en Entity Framework. Dit laatste framework verzorgt de opslag in de database om zo de gebruikers te beheren.

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/AuthenticationService.
