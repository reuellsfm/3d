# Guia Completo de Materiais para Impressao 3D

## Escolha do Material por Aplicacao

| Aplicacao | Material Recomendado | Alternativa |
|-----------|---------------------|-------------|
| Prototipo rapido | PLA | PLA+ |
| Decoracao/display | PLA Silk/Matte | PLA |
| Peca funcional (interior) | PETG | PLA+ |
| Peca funcional (exterior) | ASA | PETG |
| Peca mecanica (stress) | PETG | PA/Nylon |
| Engrenagem/desgaste | PA/Nylon | PETG |
| Flexivel/elastico | TPU 95A | TPU 85A |
| Alta temperatura | ABS (com enclosure) | PC |
| Miniatura/detalhe | PLA | PLA grey |
| Suporte soluvel | PVA | BVOH |
| Print-in-Place | PLA | PETG |
| Maquete arquitetonica | PLA branco | PLA cinza |

## Propriedades Mecanicas Comparativas

| Material | Tracao (MPa) | Flexao (MPa) | Impacto | Temp Max (C) |
|----------|-------------|-------------|---------|-------------|
| PLA | 37-60 | 80-100 | Baixo | 52-60 |
| PLA+ | 45-65 | 85-110 | Medio | 55-62 |
| PETG | 40-55 | 65-80 | Medio-Alto | 70-80 |
| ABS | 35-50 | 60-80 | Alto | 95-105 |
| ASA | 40-55 | 65-85 | Alto | 95-100 |
| TPU 95A | 20-40 | Flexivel | Muito Alto | 60-80 |
| PA/Nylon | 50-85 | 70-100 | Muito Alto | 80-120 |
| PC | 55-75 | 80-100 | Muito Alto | 120-140 |

## Propriedades para Design

### PLA - Para o Designer 3D
```
Forca entre camadas: BOA (85-95% da forca XY)
Encolhimento: BAIXO (0.3-0.5%)
Deformacao termica: 52-60C (cuidado com calor)
Resistencia UV: BAIXA (degrada ao sol)
Resistencia quimica: BAIXA
Facilidade de impressao: EXCELENTE
Acabamento: EXCELENTE (facil de lixar e pintar)
Biodegradavel: SIM (em condicoes industriais)
Custo: BAIXO (~R$80-120/kg)

Limitacoes do designer:
  - Nao usar em pecas expostas ao calor (carro, exterior)
  - Fragil sob impacto (pode estilhacar)
  - Degrada ao sol em meses
  - Bom para indoor apenas
```

### PETG - Para o Designer 3D
```
Forca entre camadas: EXCELENTE (90-98% da forca XY)
Encolhimento: MEDIO (0.5-1.0%)
Deformacao termica: 70-80C
Resistencia UV: BOA
Resistencia quimica: BOA
Facilidade de impressao: BOA (mais dificil que PLA)
Acabamento: MEDIO (mais dificil de lixar)
Custo: MEDIO (~R$100-150/kg)

Limitacoes do designer:
  - Stringing frequente (ajustar retracao)
  - Superficie menos lisa que PLA
  - Mais dificil de colar (usar epoxy ou CA com primer)
  - Pode riscar menos facilmente
```

### TPU - Para o Designer 3D
```
Flexibilidade: depende da dureza Shore
  95A: semi-rigido (capas, bumpers)
  85A: flexivel (vedacoes, amortecedores)
  80A: muito flexivel (borracha)

Forca entre camadas: BOA
Encolhimento: MEDIO-ALTO (1-2%)
Resistencia ao impacto: EXCELENTE
Resistencia a abrasao: EXCELENTE
Custo: ALTO (~R$150-250/kg)

Limitacoes do designer:
  - Impressao LENTA (20-30mm/s)
  - NAO usar no AMS Lite
  - Bridging ruim
  - Detalhes finos perdidos (material escorre)
  - Infill minimo 20% (paredes flexionam)
```

## Acabamentos Especiais

### PLA Silk (Metalico)
```
Aparencia: brilho metalico (ouro, prata, cobre)
Temperatura: +5C do PLA normal
Forca: ~80% do PLA normal
Uso: decoracao, vasos, trofeus
Detalhes: perdem-se levemente no brilho
```

### PLA Matte (Fosco)
```
Aparencia: fosco, esconde layer lines
Temperatura: similar ao PLA
Forca: similar ao PLA
Uso: figuras para pintar, modelos de exibicao
Acabamento: excelente (parece injecao plastica)
```

### PLA Dual Color (Rainbow/Gradient)
```
Aparencia: muda de cor ao longo do rolo
Uso: vasos, decoracao, arte
Efeito: depende da velocidade de impressao e tamanho
```

## Tabela de Secagem de Filamento

| Material | Temperatura | Tempo | Sinais de Umidade |
|----------|-----------|-------|-------------------|
| PLA | 45-55C | 4-6h | Estalos, bolhas, stringing |
| PETG | 60-70C | 4-6h | Estalos, superficie rugosa |
| TPU | 50-60C | 4-8h | Bolhas, sub-extrusao |
| ABS | 60-80C | 2-4h | Estalos, delamination |
| Nylon | 70-80C | 6-12h | Estalos intensos, bolhas |
| PVA | 45-55C | 4-6h | Nao extruda, engasga |

## Compatibilidade de Materiais (Multi-material)

| Material 1 | Material 2 | Adesao | Uso |
|-----------|-----------|--------|-----|
| PLA | PLA | Excelente | Multi-cor |
| PLA | PVA | Boa | Suporte soluvel |
| PETG | PETG | Excelente | Multi-cor |
| PLA | PETG | Ruim | NAO recomendado |
| ABS | ABS | Excelente | Multi-cor |
| ABS | ASA | Boa | Funcional |
| TPU | PLA | Media | Grip + estrutura |
