# Arduino-Led-s-controler-based-on-two-LDR-s-read
Controle visual com dois LEDs baseado na leitura de dois LDRs
// Arduino C++
// Controle visual com dois LEDs baseado na leitura de dois LDRs

#define ledvermelho 13  // LED vermelho conectado ao pino digital 13
#define ledbranco 12    // LED branco conectado ao pino digital 12
#define ldr1 A0          // LDR 1 conectado ao A0
#define ldr2 A1          // LDR 2 conectado ao A1

int valorldr1 = 0;       // valor lido do LDR 1
int valorldr2 = 0;       // valor lido do LDR 2

void setup() {
  pinMode(ledvermelho, OUTPUT);
  pinMode(ledbranco, OUTPUT);

  // Observação: entradas analógicas não precisam de pinMode,
  // mas deixar Aqui não causa erro.

  Serial.begin(9600);
}

void loop() {
  // Leitura dos dois LDRs
  valorldr1 = analogRead(ldr1);
  valorldr2 = analogRead(ldr2);

  // Exibe os valores no Serial para monitoramento
  Serial.print("LDR1: "); Serial.print(valorldr1);
  Serial.print("  LDR2: "); Serial.println(valorldr2);

  // Lógica de controle dos LEDs
  if (valorldr1 == valorldr2) {
    // Se os valores forem iguais, acende os dois LEDs
    digitalWrite(ledvermelho, HIGH);
    digitalWrite(ledbranco, HIGH);
  } else if (valorldr1 > valorldr2) {
    // LDR1 maior que LDR2 -> LED vermelho aceso, branco apagado
    digitalWrite(ledvermelho, HIGH);
    digitalWrite(ledbranco, LOW);
  } else {
    // LDR1 menor que LDR2 -> LED vermelho apagado, branco aceso
    digitalWrite(ledvermelho, LOW);
    digitalWrite(ledbranco, HIGH);
  }

  delay(100); // pequeno atraso para estabilidade de leitura
}
