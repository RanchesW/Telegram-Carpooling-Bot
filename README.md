# Telegram Carpooling Bot

This Telegram bot facilitates carpooling by connecting drivers and passengers. It allows drivers to create routes, passengers to join available routes, and administrators to manage users and monitor activity.

## Features

- **Driver Functionality**:
  - Create routes by sending current location or entering an address
  - Accept passenger requests to join routes
  - Receive optimized route suggestions using Google Maps API
  - Share live location to update estimated time of arrival (ETA) for passengers

- **Passenger Functionality**:
  - Join available routes by sending current location or entering an address
  - Receive notifications about driver's estimated arrival time
  - Contact support for assistance

- **Administrator Functionality**:
  - Manage users by adding or removing them from the whitelist
  - View and manage all active routes
  - Respond to support tickets and change their statuses
  - Broadcast messages to all users
  - Generate reports on tickets and routes

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Commands](#commands)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)
- [License](#license)

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/telegram-carpooling-bot.git
   cd telegram-carpooling-bot
   ```

2. **Create a virtual environment** (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install required packages**:

   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**:

   Create a `.env` file in the root directory of the project and add the following variables:

   ```env
   TELEGRAM_BOT_TOKEN=YOUR_TELEGRAM_BOT_TOKEN
   GOOGLE_MAPS_API_KEY=YOUR_GOOGLE_MAPS_API_KEY
   ```

   Replace `YOUR_TELEGRAM_BOT_TOKEN` and `YOUR_GOOGLE_MAPS_API_KEY` with your actual tokens.

   - **Telegram Bot Token**: Obtain by creating a new bot via [BotFather](https://telegram.me/BotFather) on Telegram
   - **Google Maps API Key**: Generate in [Google Cloud Console](https://console.cloud.google.com/). Make sure the following APIs are enabled:
     - Geocoding API
     - Distance Matrix API
     - Directions API

## Configuration

- **Set role passwords**:

  In the `main.py` file, configure the `ROLE_PASSWORDS` dictionary to set passwords for different user roles:

  ```python
  ROLE_PASSWORDS = {
      'administrator': 'YourAdminPassword',
      'driver': 'YourDriverPassword',
      'passenger': 'YourPassengerPassword'
  }
  ```

- **Set main administrator ID**:

  Replace `MAIN_ADMIN_ID` with your Telegram ID:

  ```python
  MAIN_ADMIN_ID = YOUR_TELEGRAM_ID
  ```

  You can find your Telegram ID using bots like [UserInfoBot](https://telegram.me/userinfobot).

- **Workplace location**:

  Set the coordinates of the destination point (workplace):

  ```python
  workplace_location = "latitude,longitude"
  ```

## Usage

Run the bot using the following command:

```bash
python main.py
```

The bot will start polling for updates. Users can interact with the bot through Telegram.

## Commands

### General Commands

- `/start` - Start interacting with the bot and select a role
- `/login` - Log in with a different role

### Driver Commands

- `/finish` - Finish collecting passengers and get optimized route
- `/show_eta` - Show estimated time of arrival to each passenger

### Administrator Commands

- `/help` - Show available administrator commands
- `/list_routes` - Show all current routes
- `/broadcast` - Send a message to all users
- `/add_user` - Add a user to the whitelist
- `/remove_user` - Remove a user from the whitelist
- `/view_tickets` - View support tickets
- `/reports` - Generate report on tickets and routes

## Project Structure

- **`main.py`**: Main script containing all bot logic and handlers
- **`bot_activity.log`**: Bot activity log file
- **`whitelist.json`**: JSON file storing whitelisted user IDs
- **`tickets.json`**: JSON file storing support tickets
- **`encryption_key.key`**: File storing encryption key for sensitive data

## Dependencies

- **Python 3.7+**
- **Libraries**:
  - `python-telegram-bot`: Telegram Bot API library
  - `googlemaps`: Google Maps API client
  - `python-dotenv`: Load environment variables from `.env`
  - `cryptography`: For encrypting sensitive data
  - `uuid`, `datetime`, `json`, `logging`: Standard Python libraries

Install dependencies using:

```bash
pip install -r requirements.txt
```

**Note**: Make sure you're using a `pip` version compatible with your Python version.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

**Disclaimer**: This bot is intended for educational purposes. Make sure to comply with all relevant laws and regulations when deploying and using this bot.
