
import paho.mqtt.client as mqtt
# MQTT broker settings
broker_address = "mqtt.example.com"
port = 1883
topic = "restroom/sensor-data"
client = mqtt.Client()
client.connect(broker_address, port)
# Read sensor data (modify as per your sensor setup)
sensor_data = {
    "occupancy": True,
    "cleanliness": "good"
}
# Publish sensor data to the MQTT topic
client.publish(topic, json.dumps(sensor_data))
client.disconnect()
from flask import Flask, render_template, jsonify
import json

app = Flask(__name__)

# Mock restroom data (replace with data from the database)
restroom_data = {
    "occupancy": True,
    "cleanliness": "good"
}

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/api/restroom_data')
def get_restroom_data():
    return jsonify(restroom_data)

if __name__ == '__main__':
    app.run(debug=True)
