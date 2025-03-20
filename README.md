# DeliverUS - Simulation project

## DeliverUS

You can find DeliverUS documentation at: <https://github.com/IISSI2-IS-2025>

## Introduction

This repository includes the complete backend (`DeliverUS-Backend` folder) and the `owner` frontend (`DeliverUS-Frontend-Owner` folder).

## Pinned Restaurants. Description

After the initial launch of DeliverUS, investors have requested a new feature that allows owners to pin their restaurants. Each owner can pin as many restaurants as they wish.

An owner can pin restaurants in two different ways:

* In the restaurant creation form. By default, it will not be pinned, but the owner can choose to pin it. To do this, a `Switch` should be provided that works with a property called `pinned`. If the `Switch` is checked, the restaurant should be created as pinned. The backend expects the `pinned` property to be a boolean and optional. If the property is not present, it should be created as not pinned.

* On the "My Restaurants" screen, through an icon that will act as a button and will be displayed next to each restaurant. By clicking it, the restaurant will be pinned or unpinned. The application should ask for confirmation from the owner when the button is pressed: use the provided `ConfirmationModal` component, similar to the `DeleteModal` component used in class. The system will inform the user if the restaurant has been pinned or unpinned.

Finally, pinned restaurants will always appear at the top of the restaurant lists presented to their owner and will be ordered by the date they were pinned (oldest first), followed by the non-pinned ones.

### Tasks on backend

Make all the necessary changes in the backend project to implement the new requirement. The backend tests expect the route to be: `PATCH /restaurants/:restaurantId/togglePinned` and that restaurants have a new property called `pinnedAt`.

In the backend tests, note the body of `POST /restaurants/` includes a `pinned` property to be either true or false.  

Do not forget that controllers in charge of listings must be adapted to the new requirement. 

Remember that you can run the backend tests with:
```Bash
npm run test:backend
```

### Requirements summary

* RF1. Ability to create a pinned or unpinned restaurant.
* RF2. Ability to set an existing restaurant as pinned or unpinned. 
* RF3. List restaurants in the described order: first the pinned restaurants ordered by pin date (the oldest pinned restaurants must come first), and then the unpinned restaurants. 

## Environment Setup

### a) Windows

* Open a terminal and run the command:

    ```Bash
    npm run install:all:win
    ```

### b) Linux/MacOS

* Open a terminal and run the command:

    ```Bash
    npm run install:all:bash
    ```

## Execution

### Backend

* To **recreate migrations and seeders**, open a terminal and run the command:

    ```Bash
    npm run migrate:backend
    ```

* To **start the backend**, open a terminal and run the command:

    ```Bash
    npm run start:backend
    ```

### Frontend

* To **run the `customer` frontend application**, open a new terminal and run the command:

    ```Bash
    npm run start:frontend:customer
    ```

* To **run the `owner` frontend application**, open a new terminal and run the command:

    ```Bash
    npm run start:frontend:owner
    ```

## Debugging

* To **debug the backend**, make sure **NO** instance is running, click the `Run and Debug` button on the sidebar, select `Debug Backend` from the dropdown list, and press the *Play* button.

* To **debug the frontend**, make sure there **IS** a running instance of the frontend you want to debug, click the `Run and Debug` button on the sidebar, select `Debug Frontend` from the dropdown list, and press the *Play* button.

## Testing

* To verify the proper functioning of the backend, you can run the included test suite by executing the following command:

    ```Bash
    npm run test:backend
    ```

**Warning: Tests cannot be modified.**

## Port Issues

Sometimes, backend or frontend processes, with or without debugging, may get stuck without releasing the used ports, preventing other processes from running. It is recommended to close and restart VSC to close such processes.




COSAS A TENER EN CUENTA:
He hecho el examen anterior ese de Performances y si este examen también va a ser de crear un nuevo tipo, hay algunas cosas que me he enterado que está bien tenerlas en cuenta:

- Hay que meter el nuevo tipo en el archivo "models.js" (ahí están todos los demás así que para ponerlo hay que seguir la plantilla y ya)
- Posiblemente los tests requerirán que existan las propiedades "createdAt" y "updatedAt", aunque el enunciado no lo diga
- En el nuevo tipo lo más normal es que no haya que implementar todas las funciones CRUD (lo normal es que solo haya que hacer create)
- En los tests, 401/403/409 son códigos de errores de middleware, y 422 son de errores de validación
- Lo de hasMany/belongsTo/belongsToMany de los modelos hay que hacerlo bien o el ordenador explota
- Si vais a usar de plantilla los archivos que ya están hechos, atención a cuando los nombres estén en plural o singular (por ejemplo en el examen de performances, a veces hay que poner "Performances" y otras veces es "Performance", y si lo haces mal se joden algunas cosas)
* Si hay que validar que una propiedad sea una fecha, el método "isDate()" funciona regular. "isISO8601()" va mejor (con escribir el principio ya saldrá como sugerencia automáticamente)
- Prestarle atención a los imports, porque seguro que o en los archivos viejos o en los nuevos va a haber que importar cosas de los nuevos (los más comunes son los de "import {*nombres de los modelos*} from '../models/models.js'")

## Submission Procedure

1. Delete the **node_modules** folders from backend and frontend and the **.expo** folder from the frontend.
2. Create a ZIP that includes the entire project. **Important: Ensure that the ZIP is not the same as the one you downloaded and includes your solution**
3. Notify the instructor before submitting.
4. When the instructor gives the green light, you can upload the ZIP to the Virtual Teaching platform. Wait for the platform to show a link to the ZIP before clicking the accept button.
