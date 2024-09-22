# Script 
```cpp
int motorPin = 10;  // Pino do motor
int ledPin = 9;     // Pino do LED
int piezoPin = 8;   // Pino do piezo
int tempPin = A0;   // Pino do sensor de temperatura

void setup() {
    pinMode(motorPin, OUTPUT); // Configura o pino do motor como saída
    pinMode(ledPin, OUTPUT);   // Configura o pino do LED como saída
    pinMode(piezoPin, OUTPUT); // Configura o pino do piezo como saída
    Serial.begin(9600);        // Inicia a comunicação serial para depuração
}

void loop() {
    // Lê a temperatura do sensor
    int sensorValue = analogRead(tempPin);
    float voltage = sensorValue * (5.0 / 1023.0); // Converte para tensão
    float temperature = (voltage - 0.5) * 100;    // Converte para Celsius

    Serial.print("Temperatura: ");
    Serial.println(temperature); // Para verificar a temperatura no monitor serial

    // Aciona motor e LED se a temperatura for maior que 30°C
    if (temperature > 30) {
        digitalWrite(motorPin, HIGH); // Liga o motor
    } else {
        digitalWrite(motorPin, LOW);  // Desliga o motor
        
    }

    // Toca o som no piezo se a temperatura for maior que 45°C
    if (temperature > 50) {
        tone(piezoPin, 1000); // Emite som de 900 Hz
      	digitalWrite(ledPin, HIGH);   // Liga o LED
    } else {
        noTone(piezoPin); // Para o som
      	digitalWrite(ledPin, LOW);    // Desliga o LED
    }

    delay(1000); // Espera 1 segundo antes de ler novamente
}
```
# Simulação do sistema de monitoramento de temperatura.
![image](https://github.com/user-attachments/assets/c8d94258-2d67-4508-8f0a-411ee6dbc072)

