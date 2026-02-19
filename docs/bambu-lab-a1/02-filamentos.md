# Bambu Lab A1 - Filamentos Compativeis e Configuracoes de Temperatura

## Visao Geral de Compatibilidade

A Bambu Lab A1 e uma impressora de estrutura aberta (open-frame). Isso significa que ela
se destaca com filamentos de baixa temperatura e pode ter dificuldades com materiais de
alta temperatura que requerem ambiente fechado.

---

## Filamentos Recomendados (Ideais para A1)

### PLA (Acido Polilactico)

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 190 - 220C |
| **Temperatura da cama** | 40 - 60C |
| **Velocidade de impressao** | 200 - 250 mm/s (padrao) |
| **Placa recomendada** | Textured PEI (sem cola) |
| **Compativel com AMS Lite** | Sim |
| **Ventilacao** | Alta (100% apos primeiras camadas) |

**Notas:**
- Material mais facil de imprimir
- Biodegradavel
- Ideal para modelos decorativos, prototipagem, miniaturas
- Baixa resistencia ao calor (~60C deformacao)
- Fragil sob impacto

### PETG (Polietileno Tereftalato Glicol)

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 220 - 250C |
| **Temperatura da cama** | 70 - 90C |
| **Velocidade de impressao** | Moderada (reduzir aceleracao para 2500-4000 mm/s2) |
| **Placa recomendada** | Textured PEI (sem cola) |
| **Compativel com AMS Lite** | Sim |
| **Ventilacao** | Moderada (50-70%) |

**Notas:**
- Mais duravel e resistente ao calor que PLA
- Boa para pecas funcionais com manuseio
- Tendencia a stringing (fios) - calibrar retracao
- Boa adesao entre camadas

### TPU (Poliuretano Termoplastico)

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 220 - 240C |
| **Temperatura da cama** | 40 - 60C |
| **Velocidade de impressao** | 20 - 30 mm/s (LENTO) |
| **Placa recomendada** | Textured PEI (sem cola) |
| **Compativel com AMS Lite** | NAO (alimentar direto do suporte de bobina) |
| **Ventilacao** | Baixa a moderada |
| **Retracao** | Minima ou desativada |

**Notas:**
- Material flexivel/elastico
- Dureza 95A, 85A, 83A, 80A sao suportadas (maior dureza = menor risco de falha)
- Deve ser alimentado diretamente do spool holder, NAO pelo AMS Lite
- Velocidade baixa e essencial para evitar atolamento

### PVA (Alcool Polivinilico)

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 190 - 210C |
| **Temperatura da cama** | 45 - 60C |
| **Compativel com AMS Lite** | NAO |

**Notas:**
- Material soluvel em agua
- Usado como suporte para impressoes multicoloridas
- Extremamente sensivel a umidade - armazenar selado

---

## Filamentos Suportados com Restricoes (Alta Temperatura)

**AVISO:** Devido ao design de estrutura aberta da A1, os seguintes materiais podem
apresentar reducao de forca entre camadas e aumento de warping em modelos grandes.
Use com cautela e em pecas pequenas.

### ABS (Acrilonitrila Butadieno Estireno)

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 240 - 270C |
| **Temperatura da cama** | 90 - 110C |
| **Enclosure recomendado** | SIM (fortemente recomendado) |
| **Placa recomendada** | High-Temp Plate com cola |
| **Compativel com AMS Lite** | Sim (material em si, mas resultados variam) |

**Notas:**
- Forte e resistente ao calor
- Alto risco de warping sem enclosure
- Emite fumos - ventilacao necessaria
- NAO recomendado para modelos grandes na A1

### ASA (Acrilonitrila Estireno Acrilato)

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 240 - 270C |
| **Temperatura da cama** | 90 - 110C |
| **Enclosure recomendado** | SIM |

**Notas:**
- Similar ao ABS mas com melhor resistencia UV
- Mesmas restricoes do ABS na A1

### PC (Policarbonato)

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 260 - 300C |
| **Temperatura da cama** | 90 - 110C |
| **Enclosure recomendado** | SIM |

### PA / Nylon

| Parametro | Valor |
|---|---|
| **Temperatura do bico** | 260 - 290C |
| **Temperatura da cama** | 80 - 100C |
| **Enclosure recomendado** | SIM |

**Notas:**
- Altamente higroscopico - secar antes de usar
- Flexivel e resistente ao impacto

---

## Filamentos com Fibra (CF/GF)

### PA-CF, PA-GF, PET-CF, PET-GF, PPA-CF, PPA-GF, PLA-CF, PLA-GF

| Parametro | Valor |
|---|---|
| **Bico necessario** | ACO ENDURECIDO (hardened steel) - OBRIGATORIO |
| **Compativel com AMS Lite** | NAO (alimentar direto do suporte) |

**IMPORTANTE:** Filamentos com particulas duras (fibra de carbono, fibra de vidro)
causam desgaste excessivo no bico de aco inoxidavel padrao. Trocar para bico de aco
endurecido antes de usar.

---

## Tabela Resumo de Compatibilidade

| Material | Bico (C) | Cama (C) | Vel. (mm/s) | AMS Lite | Cola | Enclosure |
|---|---|---|---|---|---|---|
| **PLA** | 190-220 | 40-60 | 200-250 | Sim | Nao | Nao |
| **PETG** | 220-250 | 70-90 | 150-200 | Sim | Nao | Nao |
| **TPU** | 220-240 | 40-60 | 20-30 | NAO | Nao | Nao |
| **PVA** | 190-210 | 45-60 | Lento | NAO | Nao | Nao |
| **ABS** | 240-270 | 90-110 | 150-200 | Sim* | Sim | SIM |
| **ASA** | 240-270 | 90-110 | 150-200 | Sim* | Sim | SIM |
| **PC** | 260-300 | 90-110 | 100-150 | Sim* | Sim | SIM |
| **PA** | 260-290 | 80-100 | 100-150 | Sim* | Sim | SIM |
| **PLA-CF** | 200-230 | 40-60 | 100-150 | NAO | Nao | Nao |
| **PA-CF** | 260-290 | 80-100 | 100-150 | NAO | Nao | SIM |

*Sim = compativel com AMS Lite mas resultados limitados na A1 open-frame

---

## Armazenamento de Filamento

- Manter filamentos em sacos selados com dessecante quando nao estiver em uso
- Filamentos higroscopicos (PA, PVA, TPU) requerem secagem antes do uso
- Adicionar dessecante dentro do AMS Lite
- Filamento umido causa: stringing excessivo, estalos durante impressao, camadas fracas, bolhas

---

## Fontes
- [Bambu Lab Wiki - Filament Guide Material Table](https://wiki.bambulab.com/en/general/filament-guide-material-table)
- [Bambu Lab Wiki - TPU Printing Guide](https://wiki.bambulab.com/en/knowledge-sharing/tpu-printing-guide)
- [Bambu Lab Wiki - A1 FAQ](https://wiki.bambulab.com/en/a1/manual/faq)
- [Bambu Lab Wiki - Build Plates](https://wiki.bambulab.com/en/filament-acc/acc/plates)
