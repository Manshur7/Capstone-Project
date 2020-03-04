#TSL2591 imports
import time
import board
import busio
import neopixel
import adafruit_tsl2591

#Imports for DHT22_sensor & Delay
import Adafruit_DHT
from time import sleep

#Pin Assignment for TSL2591
i2c = busio.I2C(board.SCL,board.SDA)
sensor = adafruit_tsl2591.TSL2591(i2c)

#Assigning pin number and sensor type
DHT_SENSOR = Adafruit_DHT.DHT22
DHT_PIN = 4

#Main
print("     Starting Temperature & Humidity Sensing...")
print("Pulling Readings every 3 seconds")
while True:
    #3 seconds delay in between getting readings
    sleep(3)
    humidity, temperature = Adafruit_DHT.read_retry(DHT_SENSOR, DHT_PIN)

    if humidity is not None and temperature is not None:
        print("Temp={0:0.1f}*C  Humidity={1:0.1f}%".format(temperature, humidity))
    else:
        print("Failed to retrieve data from Sensor")
# You can optionally change the gain and integration time:
#sensor.gain = adafruit_tsl2591.GAIN_LOW (1x gain)
#sensor.gain = adafruit_tsl2591.GAIN_MED (25x gain, the default)
#sensor.gain = adafruit_tsl2591.GAIN_HIGH (428x gain)
#sensor.gain = adafruit_tsl2591.GAIN_MAX (9876x gain)
#sensor.integration_time = adafruit_tsl2591.INTEGRATIONTIME_100MS (100ms, default)
#sensor.integration_time = adafruit_tsl2591.INTEGRATIONTIME_200MS (200ms)
#sensor.integration_time = adafruit_tsl2591.INTEGRATIONTIME_300MS (300ms)
#sensor.integration_time = adafruit_tsl2591.INTEGRATIONTIME_400MS (400ms)
#sensor.integration_time = adafruit_tsl2591.INTEGRATIONTIME_500MS (500ms)
#sensor.integration_time = adafruit_tsl2591.INTEGRATIONTIME_600MS (600ms)


# Read the total lux, IR, and visible light levels and print it every second.
while True:
    # Read and calculate the light level in lux.
    lux = sensor.lux
    print('Total light: {0}lux'.format(lux))
    # You can also read the raw infrared and visible light levels.
    # These are unsigned, the higher the number the more light of that type.
    # There are no units like lux.
    # Infrared levels range from 0-65535 (16-bit)
    infrared = sensor.infrared
    print('Infrared light: {0}'.format(infrared))
    # Visible-only levels range from 0-2147483647 (32-bit)
    visible = sensor.visible

    print('Visible light: {0}'.format(visible))
    if(visible<200080000):
       pixels=neopixel.NeoPixel(board.D18,60)
       pixels.fill((255,0,255))
  #  elif(visible == 1):
   #    pixels=neopixel.NeoPixel(board.D18,60)
    #   pixels.fill((0,5,0))

     # Full spectrum (visible + IR) also range from 0-2147483647 (32-bit)
    full_spectrum = sensor.full_spectrum
    print('Full spectrum(IR + visible) light: {0}'.format(full_spectrum))
    time.sleep(1.0)
