# Global Goals Community gateway

Deze service dient als toegangspoort voor de [GGC website](./ggc-website.md) naar de microservices die deze nodig heeft. Middels deze service is het eenvoudig om de backend microservices af te schermen voor direct contact van buitenaf. Daarnaast kan er gemakkelijk authenticatie en andere middleware worden toegepast op alle requests van de GGC website.

## Technologie

De gateway is gebouwd in C# middels het Dotnet framework en de plugin [Ocelot(17.0.0)](https://github.com/ThreeMammals/Ocelot). Middels deze plugin kan een Dotnet API gemakkelijk worden gebruikt als API gateway door verschillende up- en downstream routes te definiëren.

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/GGCGateway.

## Advies

Voor de GGC Gateway hebben we Ocelot Framework gebruikt voor het maken van de gateway endpoints. Dit heeft een aantal limitaties qua development: Ocelot kan geen composite requests aan en heeft daarvoor aparte composition services nodig. Dit zorgt ervoor dat in microservice architectuur er veel meer aparte service-componenten erbij komen. Voor het overzetten van de applicatie naar een monoliet zal Ocelot en een hele gateway eigenlijk niet meer nodig zijn.
