# 🔆 Arduino Dual LDR LED Controller

> Controle visual inteligente de LEDs baseado na comparação de luminosidade entre dois sensores LDR.

---

## 📋 Descrição

Este projeto utiliza um **Arduino** para ler dois sensores de luminosidade (**LDRs**) e controlar dois LEDs de acordo com a diferença de luz captada por cada sensor. É ideal para aprender sobre leitura analógica, lógica condicional e controle de saídas digitais com Arduino.

**Comportamento:**

| Condição | LED Vermelho | LED Branco |
|---|---|---|
| LDR1 recebe mais luz | 🔴 Aceso | ⚫ Apagado |
| LDR2 recebe mais luz | ⚫ Apagado | ⚪ Aceso |
| Luminosidade semelhante | 🔴 Aceso | ⚪ Aceso |

---

## 🛠️ Componentes Necessários

| Componente | Quantidade |
|---|---|
| Arduino Uno (ou compatível) | 1 |
| Sensor LDR | 2 |
| LED vermelho | 1 |
| LED branco | 1 |
| Resistor 10kΩ (pull-down para LDR) | 2 |
| Resistor 220Ω (para LEDs) | 2 |
| Protoboard | 1 |
| Jumpers | vários |

---

## 🔌 Pinagem (Pinout)

```
Arduino        Componente
-------        ----------
Pino 13   →   LED Vermelho (anodo) + resistor 220Ω → GND
Pino 12   →   LED Branco   (anodo) + resistor 220Ω → GND
Pino A0   →   LDR 1 (com divisor de tensão: LDR + resistor 10kΩ para GND)
Pino A1   →   LDR 2 (com divisor de tensão: LDR + resistor 10kΩ para GND)
5V        →   Lado positivo dos LDRs
GND       →   Referência comum
```

> **Dica:** Monte cada LDR em série com um resistor de 10kΩ entre 5V e GND. O ponto de junção (meio do divisor) vai ao pino analógico.

---

## 🚀 Como Usar

1. **Monte o circuito** conforme o pinout acima na protoboard.
2. **Abra a Arduino IDE** (versão 1.8+ ou 2.x).
3. **Copie o código** acima ou clone este repositório.
4. **Selecione a placa:** `Ferramentas > Placa > Arduino Uno`
5. **Selecione a porta:** `Ferramentas > Porta > (sua porta COM/ttyUSB)`
6. **Clique em Upload** (→).
7. Abra o **Monitor Serial** (`Ctrl+Shift+M`) em 9600 baud para acompanhar as leituras.

---

## 📊 Como Funciona

Os LDRs (Light Dependent Resistors) variam sua resistência de acordo com a intensidade de luz:

- **Mais luz** → menor resistência → tensão mais alta no pino analógico → valor mais alto (próximo de 1023)
- **Menos luz** → maior resistência → tensão mais baixa → valor mais baixo (próximo de 0)

O Arduino compara os dois valores e acende o LED correspondente ao sensor que está recebendo mais luz. A variável `DEADBAND` evita oscilações quando os dois LDRs recebem quantidades semelhantes de luz.

---

## 🔧 Possíveis Melhorias

- [ ] Usar `millis()` no lugar de `delay()` para não bloquear o loop
- [ ] Fazer média de múltiplas leituras para reduzir ruído
- [ ] Controlar o brilho dos LEDs com PWM proporcional à leitura
- [ ] Adicionar display OLED para exibir os valores em tempo real
- [ ] Threshold ajustável via Serial Monitor

---

## 📁 Estrutura do Repositório

```
/
├── README.md          # Este arquivo
├── LICENSE            # Licença MIT
└── .gitignore         # Arquivos ignorados pelo Git
```

---

## 📄 Licença

Este projeto está sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 👤 Autor

**Davi Cardoso**
- GitHub: [@DaviCarodoso0](https://github.com/DaviCarodoso0)

---

*Feito com Arduino*
