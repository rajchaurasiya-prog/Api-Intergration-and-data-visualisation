# Api-Intergration-and-data-visualisation
Name:Raj Chaurasiya

Intern Id:CT04DZ1762

Domain Name:Python programming

Duration:4 weeks

Mentor Name:Neela Santosh

Description:
Skip to content
Chat history


You said:
import requests
import matplotlib.pyplot as plt
import seaborn as sns
import datetime

# Set your OpenWeatherMap API key
API_KEY = 'your_api_key_here'
CITY = 'London'
UNITS = 'metric'  # Use 'imperial' for Fahrenheit

# Fetch weather forecast (5-day forecast at 3-hour intervals)
url = f'https://api.openweathermap.org/data/2.5/forecast?q={CITY}&appid={API_KEY}&units={UNITS}'
response = requests.get(url)
data = response.json()

# Extract needed information
times = []
temperatures = []
humidities = []
conditions = []

for entry in data['list']:
    dt = datetime.datetime.fromtimestamp(entry['dt'])
    temp = entry['main']['temp']
    humidity = entry['main']['humidity']
    condition = entry['weather'][0]['main']
    
    times.append(dt)
    temperatures.append(temp)
    humidities.append(humidity)
    conditions.append(condition)

# Set plot style
sns.set(style="darkgrid")

# Create a 2x1 dashboard
fig, ax = plt.subplots(2, 1, figsize=(12, 10))

# 1. Temperature Trend
sns.lineplot(x=times, y=temperatures, ax=ax[0], color='orange')
ax[0].set_title(f"Temperature Trend in {CITY}")
ax[0].set_xlabel("Date and Time")
ax[0].set_ylabel(f"Temperature (°{'C' if UNITS == 'metric' else 'F'})")
ax[0].tick_params(axis='x', rotation=45)

# 2. Humidity + Weather Condition
sns.lineplot(x=times, y=humidities, ax=ax[1], label='Humidity (%)', color='blue')
ax2 = ax[1].twinx()
sns.scatterplot(x=times, y=conditions, ax=ax2, label='Condition', color='red', marker='o')
ax[1].set_xlabel("Date and Time")
ax[1].set_ylabel("Humidity (%)")
ax2.set_ylabel("Weather Condition")
ax[1].tick_params(axis='x', rotation=45)
ax[1].set_title(f"Humidity & Conditions in {CITY}")

plt.tight_layout()
plt.show() give description and uses in 500 words
ChatGPT said:
Weather Forecast Visualization Using OpenWeatherMap API
This Python script demonstrates how to fetch, process, and visualize 5-day weather forecast data for a given city using the OpenWeatherMap API. It utilizes popular data visualization libraries like matplotlib and seaborn to create an informative and interactive weather dashboard.

Description
The primary objective of the script is to provide a graphical representation of future weather conditions in a specified city—in this case, London. It connects to the OpenWeatherMap API, retrieves forecast data, and visualizes two key metrics: temperature trends and humidity along with general weather conditions over time.

The script begins by setting necessary parameters such as the API key, city name, and the unit system (metric or imperial). It then constructs a URL for fetching the 5-day weather forecast. This forecast is divided into 3-hour intervals, offering detailed predictions for the near future.

Upon receiving the JSON response, the script extracts relevant fields:

Timestamps (converted into human-readable datetime format)

Temperature (°C or °F)

Humidity (%)

Weather conditions (e.g., Clear, Rain, Clouds)

These values are stored in respective lists which are later used for plotting.

Visualization
Using seaborn, the script creates a 2-row dashboard with the following plots:

Temperature Trend
A line chart is used to display how the temperature changes over the 5-day forecast period. The x-axis represents date and time, while the y-axis shows temperature. This helps users quickly understand heatwave patterns or cooling trends.

Humidity and Weather Conditions
The second subplot shows humidity percentage over time using a blue line. Overlaid on the same time scale, a scatter plot displays weather conditions (e.g., Rain, Clear) using red markers. A twin y-axis is used here to accommodate both numerical humidity data and categorical weather conditions. This plot offers a dual insight—how humid it will be and what kind of weather is expected (e.g., thunderstorms or clear skies).

Uses and Applications
Personal Use
Individuals can run this script to prepare for upcoming weather. It's especially helpful for planning travel, outdoor activities, or understanding weekly weather dynamics.

Business Planning
Businesses in sectors like logistics, agriculture, and tourism can use such visualizations to optimize operations. For instance, farmers can schedule irrigation or harvesting based on expected rain or humidity.

Educational Purposes
The code serves as a practical example for teaching API integration, JSON parsing, data visualization, and time-series analysis in data science or Python programming courses.

Weather Monitoring Applications
This can be embedded into larger systems or dashboards for real-time weather monitoring in smart cities or IoT applications.

Customization & Alerts
Developers can modify the script to send alerts when specific conditions are predicted, such as temperatures exceeding a threshold or the likelihood of storms.

Conclusion
Overall, this script is a powerful tool that bridges live meteorological data with human-readable visualizations. It demonstrates how public APIs, Python, and plotting libraries can work together to create meaningful insights from raw weather data. By adapting and expanding this code, users can develop comprehensive weather analysis tools tailored to personal or organizational needs.




Output:
![Image](https://github.com/user-attachments/assets/a560c6df-3d50-4258-bf7b-4e52bdc0a2b0)
