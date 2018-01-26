## ClientApi REST
To get access token and set webhook url to receive, access:

    https://beta.omnize.com.br

Go to:

    Menu > Settings > Integrations > ClientSDK 
    
Click on 'Generate Token' to obtain a new one, after that set the 'Webhook URL' to receive the triggers events.  

#### Get Departments
Make HTTP request:

    POST http://clientapi.omnize.com:8080/client-gateway/api/rest/v1

With body:

    {"token": "TU3J0....", "type": "info", "content":"departments", "clientId": 123}
   
#### Start interaction
Make HTTP request:

    POST http://clientapi.omnize.com:8080/client-gateway/api/rest/v1

With body:

    {
      "token": "j4hl2kjh34kh2k3jh4...",
      "type": "info",
      "content": "init",
      "departmentId": "1",
      "clientId": "12",
      "customerName": "Joao",
      "customerEmail": "joao@example.com",
      "customerPhone": "11988776655",
      "customerCpf": "123.456.789-00"
    }

#### Send message
Make HTTP request:

    POST http://clientapi.omnize.com:8080/client-gateway/api/rest/v1

With body:

    {
      "type": "message",
      "token": "j23hk4j2h3kj4h...",
      "departmentId": "1",
      "content": "Message",
      "clientId": "12"
    }

#### Notify when client typing      
Make HTTP request:

    POST http://clientapi.omnize.com:8080/client-gateway/api/rest/v1

With body:

    {
      "type": "info",
      "token": "j23hk4j2h3kj4h...",
      "departmentId": "1",
      "content": "typing",
      "clientId": "12"
    }

#### Notify when client stop typing
Make HTTP request:

    POST http://clientapi.omnize.com:8080/client-gateway/api/rest/v1

With body:

    {
      "type": "info",
      "token": "j23hk4j2h3kj4h...",
      "departmentId": "1",
      "content": "cleared",
      "clientId": "12"
    }

#### Finish interaction
Make HTTP request:

    POST http://clientapi.omnize.com:8080/client-gateway/api/rest/v1

With body:

    {
      "type": "info",
      "token": "j23hk4j2h3kj4h...",
      "departmentId": "1",
      "content": "finish",
      "clientId": "12"
    }


## Triggers

#### Agent accepts interaction

    {
      "status": "accepted",
      "clientId": "12"
    }

#### In case of unavailable agents:

    {
      "status": "unavailable",
      "clientId": "12"
    }

####  Agent finish interaction:

    {
      "status": "finish",
      "clientId": "12"
    }

####  Agent typing:

    {
      "status": "typing",
      "clientId": "12"
    }

####  Agent stop typing:

    {
      "status": "cleared",
      "clientId": "12"
    }

#### Agent new message:

    {
      "message": "New agent message!",
      "clientId": "12"
    }
