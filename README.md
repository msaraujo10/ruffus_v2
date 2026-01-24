# RUFFUS — V2 Estável

RUFFUS não é apenas um bot de trade.  
É um **sistema de simulação do mundo real**, com arquitetura explícita, máquina de estados e separação total entre:

- realidade (World)
- decisão (DecisionEngine)
- execução (Broker)
- controle (Engine)
- persistência (Store)

Nada acontece fora de um estado válido.

---

## Arquitetura

---

```md
ruffus/
│
├─ main.py # Ponto de entrada
│
├─ core/
│ ├─ state_machine.py # Estados e transições
│ ├─ engine.py # Orquestrador central
│ ├─ decision.py # Estratégia (cérebro)
│ ├─ risk.py # Regras de risco
│ └─ world.py # Representação do mercado
│
├─ adapters/
│ ├─ virtual.py # Broker virtual (simulador)
│ └─ bybit.py # Broker real (Bybit)
│
├─ storage/
│ └─ store_json.py # Persistência (banca, posições, histórico)
│
└─ config/
└─ config.json # Parâmetros globais
│
└─ README.md
```

---

## Conceito Central

O sistema é dividido em três camadas:

- **🌍World**  
  Representa a realidade sincronizada (preços, símbolos, estado do mercado).

- **🌍Engine**  
  Orquestra tudo. Não conhece API, não conhece mercado, não decide nada.
  Apenas coordena:

World → Decision → Risk → Broker → StateMachine

- **🤖DecisionEngine**  
É o cérebro. Decide quando comprar e vender, por símbolo, baseado no estado atual do mundo.

## Máquina de Estados

Tudo acontece dentro de uma **StateMachine explícita**:

BOOT → SYNC → IDLE → ENTERING → IN_POSITION → EXITING → POST_TRADE → IDLE

Nada executa fora de um estado válido.

---

## Estado Atual (V2)

- ✅ Arquitetura limpa e modular
- ✅ Máquina de estados funcional
- ✅ Modo virtual em tempo real
- ✅ Multi-ativo (BTCUSDT, ETHUSDT, SOLUSDT, etc.)
- ✅ Estratégia desacoplada da execução
- ✅ Persistência real em JSON
- ✅ Restauração automática no boot
- ✅ Logs claros de transições e trades
- ✅ Modo real (Bybit) em integração progressiva

Exemplo real de execução:
```md
[BTCUSDT] IDLE → ENTERING
🚀 COMPRA BTCUSDT @ 1.078879
[BTCUSDT] ENTERING → IN_POSITION
[BTCUSDT] IN_POSITION → EXITING
🏁 VENDA BTCUSDT @ 1.091985 | 1.21%
[BTCUSDT] EXITING → POST_TRADE
[BTCUSDT] POST_TRADE → IDLE
```

---

## Filosofia

RUFFUS não “simula trades”.  
Ele **repete o mundo real** dentro de um sistema controlado:

- mundo → percepção → decisão → execução → consequência → memória

Cada camada tem contrato claro.  
Cada fase tem fronteiras explícitas.  
Cada erro deixa rastro.

Esse projeto não cresce por “tentativa e erro”,  
mas por **evolução arquitetural consciente**.

---

## Próximas Fases

- Fase 5 – Modo Real Observador (Bybit sem operar)
- Fase 6 – Execução real controlada
- Fase 7 – Estratégias reais plugáveis
- Fase 8 – Telemetria, métricas e dashboards

