# Node CLI Weather App 🌤️ ⛈️ 😎

For this project you'll build a simple weather application in Node.js that allows a user to search for a location and view the current weather information for that location at the command line.

## Requirements

When it's complete, your application should be able to be run from the command line with the following command:

```sh
node weather.js <location>
```

In place of `<location>`, your user can type the name of a city, state, or zip code. For example:

```sh
node weather.js 27707

```

This command will output something like the following:

```sh
Current weather in Durham, NC
Partly cloudy
Temperature: 72.0 F (22.2 C)
Feels like: 72.0 F (22.2 C)
Humidity: 73%
```

If the user enters an invalid location, your program should output a message indicating that the location is invalid and exit.

```sh
node weather.js Constantinople

```

☝️ This command with an invalid location would output:

```sh

Invalid location. Please enter a valid location such as Durham, NC or 27707.
```

## Weather API

Use the [Weather API](https://www.weatherapi.com/docs/) to make requests from your Node program to retrieve weather information. You'll need to sign up for a free developer account to get an API key.

Read the documentation to learn how to make requests to the API. You'll need to use the [Current Weather API](https://www.weatherapi.com/docs/#current) to get the current weather information for a location.

### Making requests from Node

You can use the [node-fetch](https://www.npmjs.com/package/node-fetch) package to make requests from your Node program. This package is already installed for you in the `package.json` file. This allows you to make requests using [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), like you can from the front-end.

A simple example of making a request to the Weather API using `node-fetch`:

```js
require('node-fetch');
const location = '27707';

fetch(
  `http://api.weatherapi.com/v1/current.json?key=${process.env.WEATHER_API_KEY}&q=${location}`
)
  .then((response) => response.json())
  .then((data) => console.log(data))
```

### Securely handling API keys

You should not commit any API keys to GitHub. Instead, you should use environment variables to store your API key and reference it in your code.

Using the [`dotenv` package](https://www.npmjs.com/package/dotenv), which has been installed for you and included in the weather.js file, you can set environment variables in a file named `.env` and access them in your code as `process.env.VARIABLE_NAME`.

Copy the provided `env.sample` file to `.env` and add your API key to the `.env` file. Then, in your code, you can access the API key as `process.env.WEATHER_API_KEY`.

A [`.gitignore` file](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) is provided to prevent your `.env` file from being committed to GitHub. It also prevents the `node_modules` directory, where the `dotenv` package is installed, from being committed.

**❗ Do not commit your `.env` file or any file containing your API key to GitHub!** If you do, you will need to regenerate your API key.

## 🌶️ Spicy Options

If you finish the basic requirements, try adding one or more of the following features to your application:

- Customize the content and format of the weather information output. For example, the npm package [chalk](https://www.npmjs.com/package/chalk) will allow you to add color to your output, and [boxen](https://www.npmjs.com/package/boxen) will allow you to add a box around your output. You can also use [figlet](https://www.npmjs.com/package/figlet) to add ASCII art to your output.

- Add support for specifying the temperature unit (Fahrenheit or Celsius) as a command line argument.
- Allow the user to specify whether they want the current weather or the forecast for the next few days.
- Instead of using command line arguments, allow the user to answer questions about what options they want after the program is run, using the readline module or the [prompts npm package](https://www.npmjs.com/package/prompts).
- Explore the Weather APIs documentation to see what else you can request from the API. Add support for one or more additional features to your application based on the data available from the API.
