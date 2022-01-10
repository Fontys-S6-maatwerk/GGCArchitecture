# Comment service

De Comment Service beheert de data van comments geplaatst onder solutions.

De Comment Service bevat API endpoints om comments aan te maken en op te halen. De Comment service luistert ook naar de rabbitmq message bus voor aangemaakte gebruikers. zo kan een geneste gebruiker bij een opgehaalde comment goevoegd worden.

## Technologie

De comment service is gebouwd met behulp van C# en het Dotnet- en Entity Framework. Dit laatste framework verzorgt de opslag in de database om zo de comments te beheren.

## Repository

De repository naar deze service is te vinden op https://github.com/Fontys-S6-maatwerk/CommentService.
