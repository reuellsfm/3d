# Bambu Lab A1 - Especificacoes Tecnicas Completas

## Visao Geral

A Bambu Lab A1 e uma impressora 3D estilo "bed slinger" (cama movel no eixo Y) com velocidades
comparaveis a impressoras CoreXY. Projetada para iniciantes e usuarios experientes, oferece
calibracao totalmente automatica e sistema de troca rapida de bico.

- **Preco:** US$399 (impressora) / US$559 (combo com AMS Lite)
- **Tipo:** Bed slinger (FDM/FFF)
- **Design:** Estrutura aberta (open-frame)

---

## Especificacoes de Construcao

| Parametro | Valor |
|---|---|
| **Volume de impressao** | 256 x 256 x 256 mm (10 x 10 x 10 pol) |
| **Chassi** | Aco + Aluminio extrudado |
| **Dimensoes da impressora** | 465 x 410 x 430 mm |
| **Peso** | 8.3 kg |

---

## Bicos (Nozzles)

### Tamanhos Disponiveis

| Tamanho do Bico | Altura Min. de Camada | Altura Max. de Camada | Altura 1a Camada (padrao) |
|---|---|---|---|
| **0.2 mm** | 0.04 mm | 0.14 mm | 0.10 mm |
| **0.4 mm** (padrao) | 0.08 mm | 0.28 mm | 0.20 mm |
| **0.6 mm** | 0.12 mm | 0.42 mm | 0.30 mm |
| **0.8 mm** | 0.16 mm | 0.56 mm | 0.40 mm |

### Regra Geral de Altura de Camada
- **Minimo:** 20% do diametro do bico
- **Maximo:** 70% do diametro do bico
- **1a camada padrao:** 50% do diametro do bico

### Material do Bico
- **Padrao:** Aco inoxidavel (stainless steel)
- **Opcional:** Aco endurecido (hardened steel) - necessario para filamentos com fibra de carbono/vidro
- **Troca:** Sistema quick-change (sem ferramentas)

### Hot End
- **Tipo:** All-metal
- **Temperatura maxima do bico:** 300C
- **Engrenagens do extrusor:** Aco

---

## Velocidade e Aceleracao

| Parametro | Valor |
|---|---|
| **Velocidade maxima** | 500 mm/s |
| **Aceleracao maxima** | 10,000 mm/s2 |
| **Compensacao de fluxo** | Ativa (Active Flow Rate Compensation) |

### Modos de Velocidade (ajustaveis durante impressao)
1. **Silent** - Silencioso, velocidade reduzida
2. **Standard** - Padrao
3. **Sport** - Rapido (requer temperatura mais alta do hotend)
4. **Turbo** - Maximo (requer temperatura mais alta do hotend)

---

## Mesa Aquecida (Heated Bed)

| Parametro | Valor |
|---|---|
| **Temperatura maxima** | 100C |
| **Placas compativeis** | Textured PEI, Cool Plate, High-Temp Plate, Dual-Texture PEI |

---

## Perfis de Impressao no Bambu Studio (bico 0.4mm)

| Perfil | Altura de Camada | Uso Recomendado |
|---|---|---|
| **Extra Draft** | 0.28 mm | Prototipagem rapida |
| **Draft** | 0.24 mm | Rascunhos e testes |
| **Standard** | 0.20 mm | Uso geral (mais comum) |
| **Optimal** | 0.16 mm | Boa qualidade |
| **High Quality** | 0.12 mm | Alta qualidade |
| **Extreme Quality** | 0.08 mm | Qualidade maxima, detalhes finos |

---

## Calibracao Automatica

A A1 calibra automaticamente antes de cada impressao:
- **Z-offset** (distancia bico-cama)
- **Bed level** (nivelamento da cama)
- **Vibracao/ressonancia** (input shaping)
- **Pressao do bico** (pressure advance)

---

## Conectividade e Controle

| Parametro | Valor |
|---|---|
| **Conectividade** | Wi-Fi (2.4 GHz), microSD |
| **Software compativel** | Bambu Studio (Mac/Windows), Bambu Handy (app) |
| **Tela** | 3.5" IPS touchscreen |
| **Camera** | 1080p (low-rate) com suporte a timelapse |
| **Recuperacao de energia** | Sim (power-loss recovery) |

---

## Alimentacao Eletrica

| Parametro | Valor |
|---|---|
| **Entrada** | 100-240 VAC, 50/60 Hz |

---

## Filamento

| Parametro | Valor |
|---|---|
| **Diametro** | 1.75 mm |
| **Cortador de filamento** | Sim (integrado) |
| **Sensor de fim de filamento** | Sim (run-out sensor) |
| **Sensor de emaranhamento** | Sim (tangle sensor) |
| **Odometro de filamento** | Sim |

---

## Precisao Dimensional

| Parametro | Valor |
|---|---|
| **Erro medio eixo X** | 0.074 mm |
| **Erro medio eixo Y** | 0.124 mm |
| **Tolerancia alcancavel (calibrado)** | +/- 0.05 mm |
| **Reducao de furos (sem compensacao)** | 0.1 - 0.3 mm menores que o projetado |
| **Score de precisao (testes)** | 29/30 |

### Compensacao no Bambu Studio
- **X-Y Hole Compensation:** Compensa furos que imprimem menores
- **X-Y Contour Compensation:** Compensa contornos externos
- **Auto Circle Holes-Contour Compensation:** Compensacao automatica para furos circulares (compativel com filamentos oficiais Bambu)

---

## Compatibilidade com AMS

| Sistema | Compativel? | Cores |
|---|---|---|
| **AMS Lite** | Sim (direto) | Ate 4 cores |
| **AMS / AMS 2 Pro / AMS HT** | Sim (com AMS HUB SA013) | Ate 4 cores |

---

## Fontes
- [Bambu Lab A1 Tech Specs (oficial)](https://bambulab.com/en/a1/tech-specs)
- [Bambu Lab A1 - US Store](https://us.store.bambulab.com/products/a1)
- [Tom's Hardware - A1 Review](https://www.tomshardware.com/3d-printing/bambu-lab-a1-review)
- [Bambu Lab Wiki - Layer Height](https://wiki.bambulab.com/en/software/bambu-studio/layer-height)
- [Bambu Lab Wiki - A1 FAQ](https://wiki.bambulab.com/en/a1/manual/faq)
