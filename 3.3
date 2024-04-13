#include <PubSubClient.h>
#include <WiFiNINA.h>

char ssid[] = "Roji";         // Your Wi-Fi network SSID
char password[] = "12345678"; // Your Wi-Fi network password

const int echo = 3;
const int trig = 2;
const int LED1 = 7;

int duration = 0;
int distance = 0;

const char* mqttServer = "broker.emqx.io";
const int mqttPort = 1883;
const char* mqttClientId = "mqttx_dfef299d"; // Unique client ID for your Arduino
const char* mqttTopic = "SIT210/wave";
const char* mqttPayload = "MOTION DETECTEDDDD";

WiFiClient wifiClient; // Use WiFiClient for Wi-Fi connectivity
PubSubClient mqttClient(wifiClient);

void connectToWiFi() {
  Serial.print("Connecting to Wi-Fi...");
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.print(".");
  }

  Serial.println("Connected to Wi-Fi!");
  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP());
}

void setup() {
  Serial.begin(9600); // Initialize serial
  connectToWiFi();

  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
  pinMode(LED1, OUTPUT);

  // Set up MQTT connection
  mqttClient.setServer(mqttServer, mqttPort);
}

void loop() {
  digitalWrite(trig, HIGH);
  delayMicroseconds(1000);
  digitalWrite(trig, LOW);

  duration = pulseIn(echo, HIGH);
  distance = (duration / 2) / 28.5;
  Serial.println(distance);

  if (distance <= 7) {
      for (int i = 0; i < 3; i++) { // Flash the LED 3 times
        digitalWrite(LED1, HIGH);
        delay(500);
        digitalWrite(LED1, LOW);
        delay(500);
      }
      publishMessage(); // Publish MQTT message when wave is detected
      delay(1000);      // Delay to avoid publishing multiple times for the same wave
    } else {
      digitalWrite(LED1, LOW);
    }

  // MQTT client loop
  if (!mqttClient.connected()) {
    reconnect();
  }
  mqttClient.loop();
}

void reconnect() {
  while (!mqttClient.connected()) {
    Serial.print("Attempting MQTT connection...");
    if (mqttClient.connect(mqttClientId)) {
      Serial.println("connected");
      mqttClient.subscribe(mqttTopic); // Subscribe to the MQTT topic
    } else {
      Serial.print("failed, rc=");
      Serial.print(mqttClient.state());
      Serial.println(" try again in 5 seconds");
      delay(5000);
    }
  }
}

void publishMessage() {
  Serial.print("Publishing MQTT message with payload: ");
  Serial.println(mqttPayload); // Print MQTT payload
  mqttClient.publish(mqttTopic, mqttPayload);
}


void callback(char* topic, byte* payload, unsigned int length) {
  Serial.print("Message arrived [");
  Serial.print(topic);
  Serial.print("] ");
  for (int i = 0; i < length; i++) {
    Serial.print((char)payload[i]);
  }
  Serial.println();


}

