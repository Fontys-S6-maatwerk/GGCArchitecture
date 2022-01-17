# Solution Service

Deze service bewaart en regelt alles rondom de belangrijkste entiteit: de oplossingen (solutions) die gebruikers aandragen voor de [Sustainable Development Goals](https://sdgs.un.org/goals) (SDG's). Deze service bevat de CRUD operaties voor solutions en SDG's.

De Solution Service een van de belangrijkste services in de applicatie omdat bijna elke andere service via gateway calls of via messaging communiceert met de Solution Service.

De Solution Service kan verschillende types solutions opslaan waaronder Artikelen en How-To Guides.

## Technologie

De gateway is gebouwd in C# middels het Dotnet framework. De Controller is opgebouwd op het niveau van Rest Level 2. Voor de communicatie tussen applicatie en database is Entity Framework gebruikt. De database die de Solution Service gebruikt is een containerised MSSQL database. Wanneer de applicatie runt wordt ook een swagger pagina gegenereerd waarin de endpoints en verwachte JSON objecten staan gedocumenteerd.

## Advies

Veel van de Solution Service werkt naar behoren. We raden het sterk aan om Entity Framework te blijven gebruiken voor database-communicatie. De security benefits hiervan zijn onder andere dat de SQL calls sanitised zijn en het spaart veel development tijd om alles code-first te doen. Voor het genereren van Database Schemas is een code-first approach aangeraden om development van code binnen een taal te houden. Er is nog geen koppeling gemaakt met een translation service voor de automatische vertaling van dynamische text in de gesubmitte Solutions: wel is er onderzoek gedaan over hoe deze worden gekoppeld. Deze is terug te lezen in het document onderzoek i18n (internationalisation) https://github.com/Fontys-S6-maatwerk/GGCArchitecture/blob/main/src/onderzoek%20i18n.docx

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/SolutionsService.
