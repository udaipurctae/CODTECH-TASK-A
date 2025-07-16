import requests
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime

# Replace with your actual OpenWeatherMap API key
API_KEY = 'your_api_key_here'
CITY = 'London'
UNITS = 'metric'  # or 'imperial' for Fahrenheit
URL = f'http://api.openweathermap.org/data/2.5/forecast?q={CITY}&appid={API_KEY}&units={UNITS}'

# Fetch weather data
response = requests.get(URL)
data = response.json()

# Parse data
dates = []
temperatures = []
weather_descriptions = []

for entry in data['list']:
    dt = datetime.fromtimestamp(entry['dt'])
    temp = entry['main']['temp']
    desc = entry['weather'][0]['description']

    dates.append(dt)
    temperatures.append(temp)
    weather_descriptions.append(desc)

# Visualization using Seaborn and Matplotlib
sns.set(style="whitegrid")
plt.figure(figsize=(14, 6))
sns.lineplot(x=dates, y=temperatures, marker='o', color='skyblue')

plt.title(f'5-Day Temperature Forecast for {CITY}', fontsize=16)
plt.xlabel('Date and Time')
plt.ylabel(f'Temperature (°{"C" if UNITS == "metric" else "F"})')
plt.xticks(rotation=45)
plt.tight_layout()
plt.grid(True)
plt.show()
