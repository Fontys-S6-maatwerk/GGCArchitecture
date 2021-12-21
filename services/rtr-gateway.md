# Race to Resilience gateway

Deze service dient als toegangspoort voor de [Race to Resilience app](./rtr-website.md) naar de microservices die deze nodig heeft. Middels deze service is het eenvoudig om de backend microservices af te schermen voor direct contact van buitenaf. Daarnaast kan er gemakkelijk authenticatie en andere middleware worden toegepast op alle requests van de Race to Resilience app.

## Technologie

De gateway is gebouwd in C# middels het Dotnet framework en de plugin [Ocelot](https://github.com/ThreeMammals/Ocelot). Middels deze plugin kan een Dotnet API gemakkelijk worden gebruikt als API gateway door verschillende up- en downstream routes te definiëren.

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/RTRApp.