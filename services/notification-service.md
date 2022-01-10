# Notification service

De Notification service beheerd de notificaties die gebruikers kunnen hebben. Services binnen het systeem kunnen gebruik maken van deze service om notificaties voor gebruikers aan te maken. De notification service slaat deze Notificaties per gebruiker op. Nadat deze bekeken zijn door gebruiker kunnen deze verwijdered worden.

Het toevoegen van notificaties zal vooral doormiddel van de messagebus plaats vinden. terwijl het verwijderen vooral via een http request vanuit de frontend gebeurd.

## Technologie

De authenticatie service is gebouwd met behulp van C# en het Dotnet- en Entity Framework. Dit laatste framework verzorgt de opslag in de database om zo de gebruikers te beheren.

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/NotificationService.

De notification service is opgezet maar nog niet volledig geïmplementeerd.
