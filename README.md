# Placa do teste estático — UTFPR Rocket

Placa de aquisição para o **teste estático de motor**: mede o empuxo com uma célula de carga (HX711) e grava no cartão microSD. É usada pela propulsão nos estáticos dos foguetes de 500 m (F-500) e 1 km (MWTH). Feita pela aviônica, equipe Rocket 2026-1.

| | |
|---|---|
| PCB | 2 camadas, 26 componentes, 51 nets (KiCad 10) |
| Microcontrolador | ESP32-DevKitC-32E |
| Célula de carga | módulo HX711 (DT = GPIO21, SCK = GPIO22), alimentado em 5 V |
| Pressão | entrada analógica no IO34 (não há BMP280 nesta placa) |
| Armazenamento | adaptador microSD |
| Alimentação | conversor buck + bornes AK500 |
| Sinalização | buzzer (BC548) e LEDs |

## Abrir no KiCad
Usa componentes da biblioteca da equipe: [kicad-biblioteca-js](https://github.com/stansca/kicad-biblioteca-js). Instale-a e defina a variável `JS_KICAD_LIB` antes de abrir o projeto.

## Firmware
- Teste da célula de carga (tara, calibração com peso conhecido, ruído): `teste_celula_carga`, no repositório [rocket-arduino](https://github.com/stansca/rocket-arduino).
- Antes do teste estático, ligue o HX711 em **80 amostras/s** (pino RATE em nível alto). O padrão de 10/s dá só ~40 pontos numa queima de ~4 s.

## Pendências
- [ ] Confirmar se a placa foi fabricada.
- [ ] Calibrar a célula da equipe e anotar a escala aqui.
