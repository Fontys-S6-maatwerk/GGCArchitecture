# Authentication service

Deze authenticatie service verzorgt de authenticatie voor de GGC website en de RtR applicatie. 

Zodra een gebruiker registreert word de voor en achternaam en email adres doorgestuurd door middel van een RabbitMQ eventbus naar de queue van de user en comment service. Het email adres en wachtwoord worden door de authenticatie service opgeslagen. Als dit allemaal goed gaat word er een JWT token gegenereerd voor de gebruiker. Deze word terug gestuurd naar de front-end en lokaal opgeslagen.

## Technologie

De authenticatie service is gebouwd met behulp van C# en Entity Framework. Dit framework verzorgt de opslag in de database en worden de gebruikers gemanaged.

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/AuthenticationService.
