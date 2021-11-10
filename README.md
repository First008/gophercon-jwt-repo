# gophercon-jwt-repo

First things first this project is a clone of [this](https://github.com/victorsteven/gophercon-jwt-repo) project. I added some new features (i think?) on it.

## So what this project is doing?

 - It's a really basic example of authentication with a JWT (Json Web Token). It uses Redis which is an in memory database. 

## Simple Explanation:

 - ### /register

 - Of course you have to register. So you should pass parameters as json to it.
 - These are the parameters:

 - ```
    {
        "id": <"your id. example: Social security number">,
        "username": <"Your username">,
        "password": <"Your password">
    }

    ```
 - This will return you a access token and a refresh token. And it will automaticly log you in.

 - ### /login

 - If you created an account and than you logged out or your token expired than you have to log in again.

 - For that you should exact same parameters as register again in json format.

 - That will log you in.

 - ### /todo

 - This is just an example for validation of token and doing something with an authorized account. 

 - In this example you can create basic todos with these parameters:

 - ``` 
    {
        "title": <"title of todo">,
        "body": <"todo">
    }

   ```
 - Before post that dont forget that you should give your token as a parameter.

 - What curl looks like:

 - ```go
    curl --location --request POST 'http://localhost:4000/todo' \
    --header 'Authorization: Bearer <token>' \
    --header 'Content-Type: text/plain' \
    --data-raw '{
        "title": "title",
        "body": "body"
    }' 
    ```

 - ### /refresh

 - that will give you new tokens. You should give your refresh token as parameter ``` {"refresh_token": "<token>"} ``` and of course your access token as Bearer.

 - ### /whoami

 - This will return you your identity. Just post with Token.

 - ### /logout

 - As you can understand, it will log you out.

 # How to build?

 1. ``` go mod init jwt-app ```

 2. ``` go mod tidy && go mod vendor ```

 3. ``` go run main.go ``` or ``` go build . ``` 