# Rails-api-authentication-with-jwt


This example is starter template for all my [Ruby on Rails](https://github.com/rails/rails) applications.

This example use for authentication :
  * [Devise](https://github.com/plataformatec/devise)
  * [Jwt](https://github.com/jwt/ruby-jwt)


## Authentication example :

* Start the server :
        
        `rails s `

* Open another terminal and use cURL to test the API. First, try to authenticate without any email or password:
        
        `curl http://localhost:3000/home `

    The response should be `{"errors":["Not Authenticated"]} ` since we have not provided any credentials.



* Now authenticate against the API and receive a JWT which we will use for subsequent requests:

        
        `curl -X POST -d email="a@a.com" -d password="changeme" http://localhost:3000/auth_user `

* You’ll receive a successful response along with a JSON Web Token and additional user information. Like so:

        `{"auth_token":"your_token","user":{"id":1,"email":"a@a.com"}} `

    
* Use our fresh auth_token in the request to /home. Like so:

        `curl --header "Authorization: Bearer your_token" http://localhost:3000/home `

        
* We should receive a successful login response, like:

        `{"logged_in":true} `