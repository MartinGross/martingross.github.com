# Microservice Architecture

Viele heutige Softwarearchitekturen sind trotz interner Modularität nach aussen stark monolithisch aufgebaut.

Einer der interessantesten Vorträge auf der Baruco 2012 war der von Fred George über "Micro-Service Architecture". Im Gegensatz zu den üblichen SOA Ansätzen mit einigen wenigen Services, setzt die Mikroservice Architektur auf unzählige viele, kleinste Services, die jeweils nur aus relativ wenig Zeilen Code bestehen. 
Diese Micro-Services sind kurzlebig, lose gekoppelt und umfassen weniger als 100 Zeilen an Sourcecode. Beispielsweise kann man sich einen Service vorstellen, der nur auf einer einzigen Datenbank-Tabelle arbeitet.
Die Services sind erreichbar über einen Publish-Subscribe Mechanismus und liefern keine Rohdaten, sondern lediglich Erkenntnisse oder Auswertungen. Die Rohdaten können getrennt angefordert werden, falls nötig.
Jeder Programmteil kann die Auswertungen über einen Subscribe Mechanismus abonnieren. Prinzipiell veröffentlichen die Microservices alle ihre Erkenntnisse. Auch wenn es noch keinen Interessenten dazu gibt, da der Bedarf daran auch erst später entstehen kann.
Die Microservices können in verschiedenen Versionen parallel zueinander existieren und werden oft deployt. Dadurch können sie schnell und stetig erweitert werden. Wenn ein Service nicht mehr benötigt wird, sprich keine Abonnenten mehr hat, kann er entfernt werden. 

Überraschend war, dass Akzeptanztests durch Business Metriken ersetzt wurden. Fred's These dabei ist: Wenn ein Microservice nicht richtig funktioniert, wird das aus den Metriken ersichtlich. Umfangreiche Unit-Tests seien nicht notwendig, da der Microservice aus nur wenigen Zeilen Code besteht und daher sehr übersichtlich ist.

http://martinfowler.com/articles/microservices.html