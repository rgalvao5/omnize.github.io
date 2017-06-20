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
        email: 'test@example.com', // Email used to login
        name: 'Test Agent',
        password: 'j2hk2j3h4kj23h4kjh2k34', // Plain text signed as SHA256 hash
        account_id: 1111
      }
    }

Response, success:

    {
      status: 200,
      success: true,
      data: [Object] // Created agent
    }

In case of errors:

    {
      status: 200,
      success: false,
      errors: "Invalid token"
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
        password: 'j2hk2j3h4kj23h4kjh2k34' // Plain text signed as SHA256 hash
      }
    }

Response, success:

    {
      status: 200,
      success: true
    }

In case of errors:

    {
      status: 200,
      success: false,
      errors: "E-mail can be blank"
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

Response, success:

    {
      status: 200,
      success: true,
      data: [Object] // Created account
    }

In case of errors:

    {
      status: 200,
      success: false,
      errors: "Invalid token"
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

Response, success:

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

Response, success:

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

#### Update account licenses
Make HTTP request:

    PUT http://partner.omnize.com/api/v1/accounts/:id

With body:

    {
      token: 'hj4h2k3h4k23',
      license_quantity: 5
    }

Response, success:

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
      "username":"user@example.org", // Agent email
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
