## Short documentation

Project deployment:
- Clone the githab repository.
- copy the .env.example file as .env
- download composer install dependencies (or docker-compose run app composer install).
- in some cases it is necessary to generate the key APP_KEY (php artisan key: generate or docker-compose run app php artisan key: generate) if the composer does not do it automatically
- Start the project using docker (docker-compose up -d).
- Start migrations (docker-compose run app php artisan migrate
  ).
- Docker-compose run app php artisan db: seed
  )
  -Open the web application in the browser http://localhost: 8000

Ps (if the hit noticed some points in red, do not pay attention to these points must be performed)

## Small documentation
The basic logic of registration and authorization is in the folder app\Http\Controller\Auth

Almost all links between models are in the Traits\HasAccountAndPermission folder

The @permission () @endpermission directives check if the user has a role

The @account () directive checks to see if the logged-in user has an account, its code is at: Providers \ AcountServiceProvider.php

When a user registers through the main form, he automatically creates an account with his unique id. A user who has an account can create new users who have certain roles. When a new user with a role is created, you can log in through the authorization form on the site. The user with the employer role will see the report section, and the user with the admin role will see the config section. At the same time, users with roles will not see the form of adding new users because they did not register independently through the form, but were added by a user who has registered and has an account.
