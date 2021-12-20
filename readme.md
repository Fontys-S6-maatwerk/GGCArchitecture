# GGC architectuur

Deze repository bevat uitleg en diagrammen over de architectuur van het Global Goals Community project. Dit project bevat:

- De website globalgoalscommunity.eu (GGC website), waar gebruikers oplossingen voor [Sustainable Development Goals (SDG) van de VN](https://sdgs.un.org/goals) kunnen delen met anderen;
- [De Race to resilience app](https://github.com/Fontys-S6-maatwerk/RTRApp) (RtR), waar oplossingen specifiek voor [SDG 13 (klimaatactie)](https://sdgs.un.org/goals/goal13) gedeeld kunnen worden. Deze oplossingen worden gesynchroniseerd met de website.
- Ecohome Bob twitterbot, een AI die op basis van data uit weer API's wereldwijd, nieuws over klimaat en de live sensordata uit [EcoDorp Boekel](https://www.ecodorpboekel.nl/) mensen informeert over klimaatverandering;
- Information dashboard, waar politieke leiders uit de gehele EU een overzicht hebben van klimaatverandering en (de kosten van) verschillende weersextremen kunnen zien.

EcoDorp Boekel is de opdrachtgever van dit project. Zij hebben Ad Vissers naar voren geschoven als Product Owner (PO), en alle communicatie tussen de vier scrumteams en EcoDorp Boekel verlopen via hem.

## Microservices

De PO heeft aangegeven dat het uitgangspunt voor het project is dat het voor geheel Europa wordt uitgerold en dat het veel bezoekers aankan. Voor de beeldvorming werd in de openingspresentatie een bezoekersaantal van 4.000.000.000 (vier miljard) bezoekers genoemd voor de Race to Resilience app alleen. Op basis van deze specificaties is het architecture board — een groep van ontwikkelaars uit alle vier scrumteams — tot de conclusie gekomen dat een microservice architectuur benodigd is om de benodigde verticale schaalbaarheid te behalen.

Het project is opgedeeld in 20 verschillende services, waarvan twee frontends (GGC website en RtR web app), twee bijbehorende gateways en zestien backend microservices. Deze communiceren voornamelijk via het HTTPS protocol en een message queue (zie kopje 'technologiekeuze'). Daarnaast zijn er vijf externe API's waar enkele van deze services mee communiceren.Onderstaand diagram toont hoe deze services aan elkaar gekoppeld zijn.

[![C2 diagram met de verschillende microservices binnen de architectuur](./GGC_c2.svg "a title")](./GGC_c2.pdf)

Onderstaande lijst verwijst naar een beschrijving van elke microservice:

| Service                | Type         | Beschrijving                                         | Repository                                                                |
-------------------------|--------------|------------------------------------------------------|---------------------------------------------------------------------------|
| RtR website            | Frontend     | [Beschrijving](./services/rtr-website.md)            | [Repository](https://github.com/Fontys-S6-maatwerk/RTRApp)                |
| RtR gateway            | Gateway      | [Beschrijving](./services/rtr-gateway.md)            | [Repository](https://github.com/Fontys-S6-maatwerk/RTRGateway)            |
| GGC website            | Frontend     | [Beschrijving](./services/ggc-website.md)            | [Repository](https://github.com/Fontys-S6-maatwerk/GgcWebsite)            |
| GGC gateway            | Gateway      | [Beschrijving](./services/ggc-gateway.md)            | [Repository](https://github.com/Fontys-S6-maatwerk/GGCGateway)            |
| Blog Service           | Microservice | [Beschrijving](./services/blog-service.md)           | Niet geïmplementeerd                                                      |
| Comment Service        | Microservice | [Beschrijving](./services/comment-service.md)        | [Repository](https://github.com/Fontys-S6-maatwerk/CommentService)        |
| Achievement Service    | Microservice | [Beschrijving](./services/achievement-service.md)    | [Repository](https://github.com/Fontys-S6-maatwerk/AchievementService)    |
| Authentication Service | Microservice | [Beschrijving](./services/authentication-service.md) | [Repository](https://github.com/Fontys-S6-maatwerk/AuthenticationService) |
| User Service           | Microservice | [Beschrijving](./services/user-service.md)           | [Repository](https://github.com/Fontys-S6-maatwerk/UserService)           |
| Follower service       | Microservice | [Beschrijving](./services/follower-service.md)       | [Repository](https://github.com/Fontys-S6-maatwerk/FollowerService)       |
| Solution service      | Microservice | [Beschrijving](./services/solution-service.md)      | [Repository](https://github.com/Fontys-S6-maatwerk/SolutionsService)      |
| Notification service   | Microservice | [Beschrijving](./services/notification-service.md)   | [Repository](https://github.com/Fontys-S6-maatwerk/NotificationService)   |
| Poll service           | Microservice | [Beschrijving](./services/poll-service.md)           | Niet geïmplementeerd                                                      |
| Impact service         | Microservice | [Beschrijving](./services/impact-service.md)         | [Repository](https://github.com/Fontys-S6-maatwerk/ImpactCalcService)     |
| Achmea data service    | Microservice | [Beschrijving](./services/achmea-data-service.md)    | [Repository](https://github.com/Fontys-S6-maatwerk/AchmeaDataService)     |
| TwitterBot service     | Microservice | [Beschrijving](./services/twitterbot-service.md)     | [Repository](https://github.com/Fontys-S6-maatwerk/TwitterbotService)     |
| Tweet service          | Microservice | [Beschrijving](./services/tweet-service.md)          | Niet geïmplementeerd                                                      |
| Ecodorp data service   | Microservice | [Beschrijving](./services/ecodorp-data-service.md)   | Niet geïmplementeerd                                                      |
| Weather data service   | Microservice | [Beschrijving](./services/weather-data-service.md)   | [Repository](https://github.com/Fontys-S6-maatwerk/WeatherDataService)    |
| Twitter data service   | Microservice | [Beschrijving](./services/twitter-data-service.md)   | [Repository](https://github.com/Fontys-S6-maatwerk/TwitterDataService)    |

## Technologiekeuze

Hieronder worden de gebruikte talen, frameworks, communicatieprotocollen en standaarden genoemd die zijn gebruikt. Deze worden vergezeld door een beknopte uitleg over de keuze.

### Talen

De standaard programmeertaal voor de microservices is **[C#](https://docs.microsoft.com/en-us/dotnet/csharp/)**. Alle backend services en gateways worden zodoende gebouwd met behulp van het [dotnet framework](https://docs.microsoft.com/en-us/dotnet/). Hier is voor gekozen omdat de requirements voor het project vragen om enterprise ready architectuur die stabiel, bewezen en universeel is. De keuze tussen [Java](https://dev.java/) en C# is daarbij in het voordeel van C# uitgevallen omdat het merendeel van de ontwikkelaars daar meer ervaring en een sterke voorkeur voor had. Het is een van de grote talen waar ook een volgend projectteam gemakkelijk mee kan doorontwikkelen.

Voor sommige services geldt een uitzondering van deze standaard. Zo werkt de TwitterBot veel met artificial intelligence, waarmee enkele services beter bedient kunnen worden met bijvoorbeeld **[Python](https://www.python.org/)** en bijbehorende tools en frameworks als [Flask](https://www.fullstackpython.com/flask.html), [pandas](https://pandas.pydata.org/) en [Tweepy](https://www.tweepy.org/).

De frontend applicaties (GGC website en RtR app) zijn gebouwd met behulp van **[Vue.js](https://vuejs.org/)**, [JavaScript](https://www.ecma-international.org/publications-and-standards/standards/ecma-262/) en [TypeScript](https://www.typescriptlang.org/). Hiervoor is gekozen omdat de frontends soepel moeten aanvoelen voor de gebruiker, zonder te veel page reloads. Frontend frameworks zijn hier erg geschikt voor. Functietechnisch is er niet veel verschil tussen bekende frameworks als Vue,js, [React](https://reactjs.org/) en [Angular](https://angular.io/), al is die laatste afgevallen omdat het te veel ingebouwde features bevat en niet lightweight is. Vue.js is hier wederom gekozen vanwege de bekendheid onder ontwikkelaars wereldwijd en de voorkeur van een meerderheid van het projectteam.

### Communicatie

De communicatie tussen microservices is grotendeels gebaseerd op **RESTful API**'s. Het HTTPS protocol wordt gebruikt in combinatie met de REST standaard van minimaal [level 2](https://www.martinfowler.com/articles/richardsonMaturityModel.html#level2). Veel voorkomende use cases zijn het ophalen van data door de frontends van een van de microservices (via de gateway), en synchrone communicatie tussen verschillende microservices. Die laatste categorie wordt zo veel mogelijk beperkt door data van andere domeinen (die eigenlijk tot de core van een andere service behoort) ook op te slaan in de service die deze data vaak gebruikt. Dit in verband met de bijbehorende vertraging die extra synchrone calls zouden opleveren en de afhankelijkheid die services zo van elkaar hebben.

Alle RESTful API's in dit project worden gedocumenteerd middels de [OpenAPI](https://www.openapis.org/) standaard, en alle services worden vergezeld met een [Swagger](https://swagger.io/) implementatie waardoor de documentatie gemakkelijk bekeken en de endpoints eenvoudig getest kunnen worden.

Voor asynchrone communicatie wordt een message bus gebruikt. Microservices pushen daar belangrijke informatie zoals een wijziging van data naartoe. Andere services kunnen zich bij de message bus abonneren op de informatie waar zij geïnteresseerd in zijn. Zo is de User service geabonneerd op data van nieuw geregistreerde gebruikers, die door de Authentication service wordt gegenereerd. Door de message bus is deze koppeling echter niet expliciet, hoeven beide services niet van elkaars bestaan of implementatie af te weten en zijn beide services ervan onafhankelijk of de andere service draait of offline is.

Voor de message queue is **[RabbitMQ](https://www.rabbitmq.com/)** gekozen. Deze behoort samen met [Kafka](https://kafka.apache.org/) tot de grootste messaging queues, maar heeft als voordeel dat het toegankelijker en meer lightweight is. Daarnaast heeft het een hogere performance, is het acknowledge based en is er geen payload size limiet.

Er is gekozen om _geen_ gebruik te maken van het [gRPC protocol](https://grpc.io/). Het protocol is door het projectteam onderzocht, maar hoewel veel gebruikt in microservices als ongeschikt bevonden voor dit project. Reden is dat het definiëren van protocol buffers extra overhead en ontwikkeltijd kost, terwijl de tijdwinst die dit protocol oplevert beperkt is bij het soort data dat gebruikt wordt in dit project. Het gaat daarbij vaak om kleine stukjes data. Daarnaast is de hoeveelheid gebruikers die in eerste instantie gebruik zullen maken van het GGC platform naar schatting beperkt.