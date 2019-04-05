## ClientApi V1
To get access token and set webhook url to receive, access:

    https://app.omnize.com.br

Go to:

    Menu > Settings > Integrations > ClientSDK

Click on 'Generate Token' to obtain a new one, after that set the 'Webhook URL' to receive the triggers events.

#### For homolog environment

    Omnize platform: https://homolog.app.omnize.com.br

    Api endpoint: https://homolog.services.omnize.com.br

#### Get Departments
Make HTTP request:

    GET https://services.omnize.com.br/api/v1/departments?token=jh2kj3k12j3hk1j

#### Start interaction
Make HTTP request:

    POST https://services.omnize.com.br/api/v1/interactions

With body:

    {
      "token": "j4hl2kjh34kh2k3jh4...",
      "media_type": "text",
      "department_id": "1",
      "customer": { // Optional
        "name": "Joao",
        "email": "joao@example.com",
        "phone": "11988776655",
        "cpf": "123.456.789-00"
      },
      "extra" : { // Optional, returned on webhook
        "clientId": "12",
        "botId": "1111"
      },
	  "external_history": "chathistory.example.org" // Optional
    }

Response:

    {
      "message": "Interaction created successfully",
      "data": {
        "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213"
      }
    }
    

#### External History
Endpoint that returns a JSON:

    {
      "messages":[
        {
          "time":"2019-03-14 09:49:11",
          "direction":"CLIENT",
          "content":"test"
        },{
          "time":"2019-03-14 09:49:01",
          "direction":"AGENT",
          "content":"test"
        }
      ]
    }

#### Send message
Make HTTP request:

    POST https://services.api.omnize.com.br/api/v1/interactions/:interaction_hash/messages

With body:

    {
      "token": "j23hk4j2h3kj4h...",
      "content": "Message",
      "type": "text", // "image/jpeg", "image/png", "video/mp4", "audio/ogg"
      "url": "https://images.com/image.png", // Optional
    }

Response:

    {
      "message": "Message created successfully",
      "data": {
        "message_hash": "3110a5da-87c7-4f6d-a4ab-2b1ed5edfd46"
      }
    }

#### Notify when client typing
Make HTTP request:

    PUT https://services.omnize.com.br/api/v1/interactions/:interaction_hash/typing

With body:

    {
      "token": "j23hk4j2h3kj4h..."
    }

#### Notify when client stop typing
Make HTTP request:

    PUT https://services.omnize.com.br/api/v1/interactions/:interaction_hash/cleared

With body:

    {
      "token": "j23hk4j2h3kj4h..."
    }

#### Finish interaction
Make HTTP request:

    PUT https://services.omnize.com.br/api/v1/interactions/:interaction_hash/finish

With body:

    {
      "token": "j23hk4j2h3kj4h..."
    }


## Triggers

#### Interaction added to queue

    {
      "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213",
      "state": "queued",
      "position": 1
      "extra": {}
    }

#### Agent accepts interaction

    {
      "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213",
      "state": "accepted",
      "extra": {}
    }

#### In case of unavailable agents:

    {
      "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213",
      "state": "unavailable",
      "extra": {}
    }

####  Agent finish interaction:

    {
      "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213",
      "state": "finished",
      "extra": {}
    }

####  Agent typing:

    {
      "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213",
      "state": "typing",
      "extra": {}
    }

####  Agent stop typing:

    {
      "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213",
      "state": "cleared",
      "extra": {}
    }

#### Agent new message:

    {
      "interaction_hash": "322e458c-540c-4c11-ab5c-d38d39f57213",
      "message": {
        "hash": "3110a5da-87c7-4f6d-a4ab-2b1ed5edfd46",
        "content": "Message",
        "type": "text"
      },
      "extra": {}
    }
