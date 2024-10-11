## 미니프로젝트를 시작했따,,,!
배웠던 아두이노와 라즈베리파이, mqtt 통신 influx 등을 이용해서 모니터링 프로그램을 만드는게 목표다 

```
#include <WiFi.h>
#include <PubSubClient.h>
#include <Wire.h>
#include <BH1750.h>
#include "DHT.h"
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define PAYLOAD_MAXSIZE 64

// DHT Sensor Configuration
#define DHTPIN 4        // DHT11 핀 번호
#define DHTTYPE DHT11   // DHT11 타입
DHT dht(DHTPIN, DHTTYPE); // DHT11 인스턴스 생성

// BH1750 조도 센서 설정
BH1750 lightMeter;

// OLED 설정
#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64
#define OLED_RESET -1  // 리셋 핀이 없으면 -1로 설정
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

// Wi-Fi & MQTT 설정
const char* ssid = "RiatechA2G";           // Wi-Fi SSID
const char* password = "730124go";         // Wi-Fi Password
const char* mqtt_server = "192.168.1.4";   // MQTT 브로커 IP 주소
const char* mqtt_user = "mqtt_kdy";        // MQTT 사용자 이름
const char* mqtt_password = "1234";        // MQTT 비밀번호
const char* clientId = "ESP32Client";      // MQTT 클라이언트 ID
const char* topic = "sensor/data";         // MQTT 주제

// MQTT 클라이언트 설정
WiFiClient espClient;
PubSubClient client(espClient);

void setup_wifi() {
    delay(10);
    Serial.println();
    Serial.print("Connecting to ");
    Serial.println(ssid);

    WiFi.begin(ssid, password);

    while (WiFi.status() != WL_CONNECTED) {
        delay(500);
        Serial.print(".");
    }

    Serial.println("");
    Serial.println("WiFi connected");
}

void reconnect() {
    // MQTT 연결 상태 확인 및 재연결 시도
    while (!client.connected()) {
        Serial.print("Connecting to MQTT...");
        if (client.connect(clientId, mqtt_user, mqtt_password)) {
            Serial.println("connected");
        } else {
            Serial.print("failed, rc=");
            Serial.print(client.state());
            delay(5000);
        }
    }
}

void setup() {
    // 시리얼 통신 초기화
    Serial.begin(9600);

    // Wi-Fi 연결 설정
    setup_wifi();

    // MQTT 브로커 설정
    client.setServer(mqtt_server, 1883);

    // OLED 초기화
    if (!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {  // 0x3C는 I2C 주소
        Serial.println(F("SSD1306 초기화 실패"));
        for (;;);
    }
    display.display();
    delay(2000);
    display.clearDisplay();

    // 센서 초기화
    dht.begin();
    Wire.begin();
    if (lightMeter.begin()) {
        Serial.println("BH1750 초기화 성공");
    } else {
        Serial.println("BH1750 초기화 실패");
    }
}

void loop() {
    if (!client.connected()) {
        reconnect();
    }
    client.loop();

    // DHT11 센서에서 온도와 습도 읽기
    float h = dht.readHumidity();
    float t = dht.readTemperature();

    // 유효한 데이터인지 확인
    if (isnan(h) || isnan(t)) {
        Serial.println("DHT11 센서에서 데이터를 읽지 못했습니다.");
        return;
    }

    // BH1750 센서에서 조도 읽기
    float lux = lightMeter.readLightLevel();

    // OLED에 데이터 출력
    display.clearDisplay();
    display.setTextSize(1);       // 텍스트 크기 설정
    display.setTextColor(SSD1306_WHITE);  // 텍스트 색상 설정

    // OLED에 온도, 습도, 조도 출력
    display.setCursor(0, 0);
    display.print("Temp: ");
    display.print(t);
    display.println(" C");

    display.setCursor(0, 16);
    display.print("Humi: ");
    display.print(h);
    display.println(" %");

    display.setCursor(0, 32);
    display.print("Lux: ");
    display.print(lux);
    display.println(" lx");

    display.display();  // OLED에 그리기 완료

    // MQTT로 보낼 데이터 생성
    char payload[PAYLOAD_MAXSIZE];
    String sPayload = "{'Temp':" + String(t, 1) +
                      ",'Humi':" + String(h, 1) +
                      ",'Lux':" + String(lux, 1) + "}";
    sPayload.toCharArray(payload, PAYLOAD_MAXSIZE);

    // MQTT로 데이터 전송
    client.publish(topic, payload);

    // 시리얼 모니터에 전송된 데이터 출력
    Serial.print("Published to ");
    Serial.print(topic);
    Serial.print(": ");
    Serial.println(payload);

    delay(2000);  // 2초 대기 후 다시 데이터 전송
}
```
```
import paho.mqtt.client as mqtt
from influxdb import InfluxDBClient
import json

# InfluxDB 설정
influx_client = InfluxDBClient(host='localhost', port=8086, database='sensor_data')

# MQTT 브로커 설정
mqtt_broker = "192.168.1.4"  # MQTT 브로커 IP
mqtt_port = 1883
mqtt_user = "influx_KDY"
mqtt_password = "1234"

# MQTT 연결 시 콜백 함수
def on_connect(client, userdata, flags, rc):
    if rc == 0:
        print("Connected to MQTT broker")
        # 'sensor/data' 주제 구독
        client.subscribe("sensor/data")
    else:
        print(f"Failed to connect, return code {rc}")

# MQTT 메시지 수신 시 콜백 함수
def on_message(client, userdata, msg):
    try:
        # 수신된 메시지를 문자열로 디코딩
        message = msg.payload.decode()
        print(f"Received message: {message}")

        # JSON 형식으로 변환
        data = json.loads(message.replace("'", "\""))

        # InfluxDB에 저장할 데이터 생성
        json_body = [
            {
                "measurement": "sensor_data",
                "fields": {
                    "temperature": float(data['Temp']),
                    "humidity": float(data['Humi']),
                    "lux": float(data['Lux'])
                }
            }
        ]

        # InfluxDB에 데이터 쓰기
        influx_client.write_points(json_body)
        print("Data written to InfluxDB")
    
    except Exception as e:
        print(f"Error processing message: {e}")

# MQTT 클라이언트 설정
mqtt_client = mqtt.Client()
mqtt_client.username_pw_set(mqtt_user, mqtt_password)
mqtt_client.on_connect = on_connect
mqtt_client.on_message = on_message

# MQTT 브로커 연결
mqtt_client.connect(mqtt_broker, mqtt_port, 60)

# MQTT 메시지 대기
mqtt_client.loop_forever()
```
이 두 코드를 이용해서 sub/pub 기능을 구현했다.
![image](https://github.com/user-attachments/assets/8efee825-ec8d-4ab7-8796-a4bdd17d9506)



![image](https://github.com/user-attachments/assets/d33545cd-81e9-4bc2-96a5-fbc717e39c51)


이런식으로 우노와 라즈베리파이 사이에 통신이 발생하고 센서가 받아온 값을 influxdb 에 저장하게 된다.

저장한 값을 grafana로 시각화 해봤다.


![image](https://github.com/user-attachments/assets/9fc30b77-df20-4671-a9e9-cab80b677b3c)


이걸 좀 더 멋있게 만들기 위해서 생각한게 있다.
```
윈폼을 이용해서 앱을 만든다음 아두이노 보드와 연동된 데이터베이스의 값을 불러오고, 특정 조건이 만족되면 경고 메시지 등을 출력,
그다음 버튼으로 공정을 강제로 중단 할 수 있는 프로세스를 구동
```

어려울것같다 오후에 해봐야겠다~~

