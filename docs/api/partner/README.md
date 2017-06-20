## Partner Portal
To get partner token, access:

    http://partner.omnize.com

For login/password contact suporte@omnize.com

## Partner API

#### Create Agent
Make HTTP request:

    POST http://partner.omnize.com/api/v1/agents

With body:

    {
      token: 'j423j42jn3kj4n',
      agent: {
        email: 'test@example.com',
        name: 'Test Agent',
        password: 'j2hk2j3h4kj23h4kjh2k34', // SHA256
        account_id: 1111
      }
    }

#### Update Agent
Make a HTTP request:

    PUT http://partner.omnize.com/api/v1/agents/:id

With body:

    {
      token: 'j423j42jn3kj4n',
      agent: {
        email: 'update@example.com',
        name: 'New Name',
        password: 'j2hk2j3h4kj23h4kjh2k34' // SHA256
      }
    }

#### Create Account
Make HTTP request:

    POST http://partner.omnize.com/api/v1/accounts

With body:

    {
      token: 'hj4h2k3h4k23',
      license_quantity: 10,
      password: 'j2hk2j3h4kj23h4kjh2k34', (Optional) // SHA256
      account: {
        email: 'test@example.com',
        main_contact: 'Account Owner Namer',
        telefone: '(11) 9345-0987',
        url: 'testwebpage.com.br'
      }
    }

#### Inactive Account
Make HTTP request:

    PUT http://partner.omnize.com/api/v1/accounts/:id

With body:

    {
      token: 'hj4h2k3h4k23',
      account: {
        ativo: 0
      }
    }

#### Active Account
Make HTTP request:

    PUT http://partner.omnize.com/api/v1/accounts/:id

With body:

    {
      token: 'hj4h2k3h4k23',
      account: {
        ativo: 1
      }
    }

#### Update account licenses
Make HTTP request:

    PUT http://partner.omnize.com/api/v1/accounts/:id

With body:

    {
      token: 'hj4h2k3h4k23',
      license_quantity: 5
    }

#### Response
If success, return body:

    {
      status: 200,
      success: true
    }

In case of errors:

    {
      status: 200,
      success: false,
      errors: "Invalid token"
    }

#### Widget
Widget-code, set proper account_id at 'wOmz.init({id:#{id}})':

    <!-- Início do script Omnize -->
      <script>
        document.addEventListener('DOMContentLoaded',function(){
          var JSLink=location.protocol+'//widget.omnize.com',JSElement=document.createElement('script');
          JSElement.async=!0;
          JSElement.src=JSLink;
          JSElement.onload=OnceLoaded;
          document.getElementsByTagName('body')[0].appendChild(JSElement);
          function OnceLoaded(){
            wOmz.init({id:#{id}});
          }
        },false);
      </script>
    <!-- Fim do script Omnize -->


#### Url login
Make a http request to generate auth_token:

    POST https://ca1vsqktff.execute-api.us-east-1.amazonaws.com/prod/authentication

Body:

    {
      "action": "loginPartner",
      "username":"r0302851@gmail.com", // Agent email
      "token":"B4cPxMMVteyoqCk6UUsK" // Partner token
    }

Response:

    {
      "message": "",
      "token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVaRp5D0e3",
      "status": 200
    }

Link to login, with returned token:

    https://login.beta.omnize.com.br/mirror?token=eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVaRp5D0e3
