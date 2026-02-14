# 🧠 RUFFUS V2 — Arquitetura Cognitiva Restaurada

Ruffus V2 é um sistema operacional de trading estruturado em camadas cognitivas.

Esta versão restaurada resgata a arquitetura original baseada em:

- Engine cognitivo
- State Machine formal
- World desacoplado
- Strategy modular
- Risk Manager independente
- Feedback Engine (auto-diagnóstico)
- Persistência consistente

---

## 📁 Estrutura Atual

```
RUFFUS_V2/
│
├── adapters/
│   └── bybit.py
│
├── core/
│   ├── engine.py
│   ├── state_machine.py
│   ├── world.py
│   └── risk.py
│
├── storage/
│   ├── state.json
│   ├── events.jsonl
│   ├── journal.jsonl
│   └── memory.json
│
├── strategies/
│   └── canonical/
│
├── tools/
│   └── feedback.py
│
├── config/
│   └── config.json
│
└── main.py
```

---

## 🧠 Arquitetura

### Engine
- Orquestrador central
- Restaura estado persistido
- Executa decisões aprovadas
- Alimenta aprendizado contínuo

### World
- Mantém preços e histórico
- Fornece snapshot para estratégia

### Strategy
- Decide BUY / SELL / HOLD
- Pode aprender com histórico
- Pode adaptar comportamento via feedback

### Risk Manager
- Limita posições simultâneas
- Controla trades diários
- Implementa cooldown pós-loss

### Feedback Engine
- Analisa eventos recentes
- Classifica saúde: OK / UNSTABLE / RISK_BLOCKED
- Mantém memória cognitiva persistente

---

## 🔁 Modos Operacionais

- `REAL`
- `OBSERVADOR`
- `VIRTUAL`
- `PAUSED`

Auto-regulação baseada em diagnóstico.

---

## ⚙️ Execução

```
python main.py
```

---

## 📌 Estado Atual

✔ Engine Cognitivo restaurado  
✔ Persistência funcional  
✔ Feedback ativo  
✔ Risk configurável  
✔ Integração Bybit Unified Spot  
✔ Sincronização de posições via saldo  

---

## 🚀 Próximo Passo Planejado

- Scanner modular separado
- Ranking momentum
- Retorno do perfil adaptativo
- Reativação completa do sistema de aprendizado

---

Ruffus voltou à base estrutural correta.

A evolução agora pode ser feita com estabilidade.



# 🧠 RUFFUS BINARY

Sistema autônomo de trading para opções binárias / digitais.

Derivado da arquitetura Ruffus V2, porém completamente isolado
do sistema principal de cripto.

---

# 🎯 OBJETIVO

Operar contratos binários na Deriv (Índices Sintéticos),
utilizando detecção de regime de mercado em tempo real.

Foco atual:
- Volatility 10 Index
- Volatility 25 Index
- Volatility 50 Index
- Volatility 100 Index

Operações:
- CALL / PUT
- 3 a 5 ticks
- Seleção automática do melhor índice

---

# 🏗️ ARQUITETURA

Ruffus Binary é composto por:

## 1️⃣ BinaryEngine
Motor exclusivo do subsistema binário.
- Loop vital
- Execução de ordens
- Processamento de resultados
- Persistência
- Integração com feedback

## 2️⃣ DerivVolatilityBroker
Conexão WebSocket direta com Deriv.
- Autenticação via token
- Stream de ticks em tempo real
- Execução de contratos
- Captura automática de resultado (WIN/LOSS)

## 3️⃣ Estratégia: Volatility Regime Engine
Arquivo:
strategies/volatility/trend_tick.py


Responsável por:
- Detectar regime de mercado
- Classificar: TREND | CHAOS | DEAD
- Medir energia do movimento
- Calcular força da tendência
- Selecionar o melhor índice
- Controlar cooldown

---

# 🧠 LÓGICA ATUAL DE DECISÃO

Para entrar em operação:

1. Índice deve estar em regime TREND
2. Baixo ruído (noise ratio controlado)
3. Energia mínima acumulada
4. Sequência mínima de direção (min_sequence)
5. Score superior aos outros índices

Se aprovado:
→ Executa CALL ou PUT
→ Aplica cooldown
→ Reseta energia

---

# 📊 REGIME DETECTADO

| Regime      | Significado                     |
|------------|----------------------------------|
| TREND      | Tendência clara                  |
| CHAOS      | Ruído excessivo                  |
| DEAD       | Mercado sem energia              |
| UNDEFINED  | Insuficiente para classificar    |

Ruffus só opera em TREND.

---

# ⚙️ MODOS

## SHADOW
Analisa mas não executa ordens.

## ASSISTED
Executa contratos na conta DEMO.

---

# 💾 PERSISTÊNCIA

Arquivos utilizados:

storage/binary/state.json
storage/binary/events.jsonl
storage/binary/journal.jsonl
storage/binary/memory.json


Sistema totalmente isolado do Ruffus V2.

---

# 🚀 EXECUÇÃO

python -m apps.ruffus_binary


Requisitos:
- Token Deriv no .env
- Conta DEMO ativa

---

# 🔐 SEGURANÇA

- Máximo de trades configurável
- Cooldown automático
- Estratégia isolada
- Sem interferência no sistema principal

---

# 📈 STATUS ATUAL

✔ Conexão Deriv estável  
✔ Stream de ticks funcionando  
✔ Execução de contrato funcional  
✔ Captura de WIN/LOSS ativa  
✔ Estratégia com detecção de regime  
✔ Painel cognitivo operacional  

---

# 🔜 PRÓXIMAS EVOLUÇÕES

- Ajuste adaptativo de duração (3 ou 5 ticks)
- Filtro de horário
- Controle de risco progressivo
- Metamemória por índice
- Estatísticas avançadas por regime

---

# 🧩 FILOSOFIA

Ruffus Binary não opera por impulso.

Ele:
- Detecta ambiente
- Avalia energia
- Classifica regime
- Seleciona oportunidade
- Age com controle temporal

---

Sistema em desenvolvimento ativo.
Modo atual: Produção DEMO.
