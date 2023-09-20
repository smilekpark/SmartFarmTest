# SmartFarmTest

### 클래스 다이어그램 

```mermaid
classDiagram
    class Arduino {
        +Arduino()
        -WiFiModule
        -DHTSensor
        -SoilMoistureSensor
        -LightSensor
        -RelayModule
    }

    class Blynk {
        +Blynk()
        -MobileApp
        -WebApp
    }

    class User {
        +User()
    }

    Arduino --|> Sensor : contains
    Arduino --|> Actuator : controls
    Blynk --|> User : interacts with
    Blynk --|> Arduino : communicates with

    class Sensor {
        +getData()
    }

    class Actuator {
        +control()
    }
```
### 클래스 다이어그램 

```mermaid
sequenceDiagram
    participant User as User
    participant BlynkApp as Blynk App
    participant BlynkServer as Blynk Server
    participant Arduino as Arduino

    User ->> BlynkApp: Request sensor data
    BlynkApp ->> BlynkServer: Forward data request
    BlynkServer ->> Arduino: Request sensor data
    Arduino -->> BlynkServer: Send sensor data
    BlynkServer -->> BlynkApp: Forward sensor data
    BlynkApp -->> User: Display sensor data

```
