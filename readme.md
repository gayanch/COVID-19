# COVID-19 Backend Services

## How to run
- install mysql server
- execute `covid19.sql` on server
- build project using `mvn clean install`
- run using: `mvn spring-boot:run`

### APIs 
GET ``http://localhost:8000/taskforce/message/<messageId>/<lang>``

options for lang: en, si, ta

Sample db entry:
``INSERT INTO `covid19_db`.`hpb_notification` (`id`, `title`, `subtitle`, `source`, `message_en`, `message_si`, `message_ta`) VALUES ('1', 'Test news item', 'test subtitle', 'MOH', 'This is a test message', 'මෙය පරීක්ෂණ පණිවිඩයකි', 'இது ஒரு சோதனை செய்தி');
``

### FCM-Backend

## Get started

- replace the `covid-19-lk-dev-firebase-adminsdk.json` file with the actual file
- replace the `token` in application.yml

## testing

* GET /notification – Trigger sample notification with default values sending 
- `curl -H "Content-Type: application/json" -X GET http://localhost:8000/notification`

* POST /notification/topic – Send a message to a specific topic
- `curl -d '{"title":"Hello", "message":"The message...", "topic":"contactTopic"}' -H "Content-Type: application/json" -X POST http://localhost:8000/notification/topic`

* POST /notification/token – Send a message to a specific device (with the token)
- `curl -d '{"title":"Hey you!", "message":"Watch out!", "token":"cct00ebz8eg:APA91bFcTkFE_0Qafj6nWv5yHxqCLTyxAaqi4QzwsFNLP5M9G78X8Z5UMZTW004q1PUux63Ut-1WMGVToMNTdB3ZfO8lCZlc4lGpxm7LBdWfkhaUxdbpQ5xIO5cAb-w9H2dBLNHT7i-U", "topic": ""}' -H "Content-Type: application/json" -X POST http://localhost:8080/notification/token`

* POST /notification/data – Send a message to a specific topic with additional payload data.
- `curl -d '{"title":"Hello", "message":"Data message", "topic":"contactTopic"}' -H "Content-Type: application/json" -X POST http://localhost:8000/notification/data`

*If succeeded you should receive following JSON response with code 200:

- `{
    "status": 200,
    "message": "Notification has been sent."
}`
