# Bambu Studio - Configuracoes e Perfis do Slicer

## Visao Geral

Bambu Studio e o software de fatiamento (slicer) oficial da Bambu Lab. Disponivel para
Mac e Windows, oferece perfis pre-configurados otimizados para cada impressora e material.

---

## Categorias de Configuracao

O Bambu Studio organiza parametros em tres categorias:

1. **Printer (Impressora):** Configuracoes especificas do hardware
2. **Filament (Filamento):** Temperaturas, fluxo, resfriamento por material
3. **Process (Processo):** Qualidade, velocidade, infill, paredes, suportes

---

## Perfis de Processo Pre-configurados (Bico 0.4mm)

### Perfis por Altura de Camada

| Perfil | Camada | Uso | Tempo Relativo |
|---|---|---|---|
| **0.08mm Extra Detail** | 0.08 mm | Qualidade maxima, miniaturas finas | Muito lento |
| **0.12mm High Quality** | 0.12 mm | Alta qualidade, pecas decorativas | Lento |
| **0.16mm Optimal** | 0.16 mm | Bom equilibrio qualidade/velocidade | Medio |
| **0.20mm Standard** | 0.20 mm | Uso geral (MAIS COMUM) | Medio-rapido |
| **0.24mm Draft** | 0.24 mm | Rascunhos rapidos | Rapido |
| **0.28mm Extra Draft** | 0.28 mm | Prototipagem maxima velocidade | Muito rapido |

### Altura da Primeira Camada
- Padrao: 50% do diametro do bico
- Bico 0.4mm: primeira camada = 0.20mm
- Bico 0.2mm: primeira camada = 0.10mm

---

## Configuracoes de Velocidade

### Velocidade Volumetrica Maxima (MVS)

O limitador REAL de velocidade no Bambu Studio nao e o valor de mm/s, mas sim o
**Maximum Volumetric Speed (MVS)** configurado no perfil de filamento. Mesmo com
velocidade nominal alta, o printer reduz automaticamente se o MVS for atingido.

- PLA generico: MVS conservador (~10 mm3/s)
- PLA Bambu Lab: MVS otimizado (maior)
- PETG: MVS mais baixo que PLA

### Tempo Minimo de Camada
- Padrao: **8 segundos**
- O printer NUNCA imprime uma camada mais rapido que isso
- Garante resfriamento adequado entre camadas

### Modos de Velocidade (durante impressao)

| Modo | Descricao | Nota |
|---|---|---|
| **Silent** | Velocidade reduzida, baixo ruido | Ideal para noite |
| **Standard** | Configuracao padrao | Uso geral |
| **Sport** | Velocidade aumentada | Requer temp. mais alta do hotend |
| **Turbo** | Velocidade maxima | Requer temp. mais alta do hotend |

---

## Configuracoes de Qualidade

### Wall Generator (Gerador de Paredes)

| Tipo | Descricao | Recomendacao |
|---|---|---|
| **Classic** | Largura de parede fixa | Simples e previsivel |
| **Arachne** | Largura de parede variavel | RECOMENDADO - melhor para paredes finas |

**Arachne** se adapta a larguras variadas de parede, produzindo pecas mais fortes com
menos lacunas.

### Ordem de Impressao de Paredes

| Ordem | Quando Usar |
|---|---|
| **Inner/Outer** | Melhor para overhangs (padrao) |
| **Outer/Inner** | Melhor acabamento de superficie |
| **Inner/Outer/Inner** | Equilibrio entre ambos |

### Suavizacao de Velocidade (Speed Smoothing)
- Habilitado por padrao (v1.9.4+)
- Suaviza transicoes de velocidade entre areas com/sem overhang
- Melhora qualidade de resfriamento

---

## Configuracoes de Forca/Resistencia

### Paredes (Walls)

| Configuracao | Valor Tipico | Nota |
|---|---|---|
| **Numero de paredes** | 2-4 | 4 para pecas funcionais, 2 para decorativas |
| **Largura da parede externa** | 0.4 mm (= bico) | Ajustavel |
| **Largura da parede interna** | 0.4 mm | Ajustavel |

### Preenchimento (Infill)

| Configuracao | Valor Tipico | Nota |
|---|---|---|
| **Densidade de infill** | 15% (padrao) | 20-50% para pecas funcionais |
| **Padrao de infill** | Grid/Gyroid/Cubic | Gyroid/Cubic para maior resistencia |
| **Combinacao de infill** | Habilitada | Infill mais grosso que as paredes (economiza tempo) |

### Combinacao de Infill por Altura de Camada

| Altura de Camada | Infill Combinado | Proporcao |
|---|---|---|
| 0.08 mm | 0.40 mm | 1:5 |
| 0.12 mm | 0.36 mm | 1:3 |
| 0.16 mm | 0.32 mm | 1:2 |
| 0.20 mm | 0.40 mm | 1:2 |
| 0.24 mm | N/A | Sem combinacao |
| 0.28 mm | N/A | Sem combinacao |

### Topo e Base (Top/Bottom Shells)

| Configuracao | Valor Tipico |
|---|---|
| **Camadas de topo** | 4-6 |
| **Camadas de base** | 4-6 |

---

## Configuracoes de Ponte (Bridge)

| Parametro | Valor Padrao | Descricao |
|---|---|---|
| **Max Bridge Length** | ~10 mm | Distancia maxima de ponte sem suporte |
| **Bridge Flow** | 1.0 (100%) | Aumentar para pontes mais confiaves |
| **Bridge Speed** | Reduzida | Velocidade mais lenta durante ponte |
| **Thick Bridges** | Desativado | Ativar para pontes mais longas (menos qualidade) |
| **Bridge Direction** | Automatico | Pode ser ajustado para reduzir distancia sem suporte |

---

## Configuracoes de Suporte

### Tipos de Suporte

| Tipo | Quando Usar |
|---|---|
| **Normal** | Overhangs planares grandes - melhor qualidade de superficie |
| **Tree** | Geometrias complexas - menos material, mais rapido |
| **Hybrid (Auto)** | Recomendado para uso geral - combina Normal + Tree |

### Parametros de Suporte

| Parametro | Descricao |
|---|---|
| **Support Threshold Angle** | Angulo a partir do qual suporte e gerado (padrao ~45) |
| **Top Z Distance** | Gap entre suporte e modelo (facilita remocao) |
| **Support Interface** | Camadas de interface para melhor superficie |

---

## Configuracoes de Resfriamento (Cooling)

Os perfis de filamento Bambu Lab vem com configuracoes de resfriamento otimizadas.

| Material | Fan Speed | Notas |
|---|---|---|
| **PLA** | 80-100% | Maximo resfriamento apos primeiras camadas |
| **PETG** | 50-70% | Resfriamento moderado |
| **TPU** | 30-50% | Resfriamento baixo |
| **ABS** | 0-30% | Minimo resfriamento |

### Auto Slow Down para Overhangs
- Habilitado por padrao
- Reduz velocidade automaticamente em areas de overhang
- Previne deformacao em alta velocidade

---

## Configuracoes Avancadas

### Precisao

| Parametro | Descricao | Valor |
|---|---|---|
| **X-Y Hole Compensation** | Compensa furos menores | Ajustar por teste |
| **X-Y Contour Compensation** | Compensa dimensoes externas | Ajustar por teste |
| **Seam Position** | Posicao da costura | Aligned/Random/Nearest |
| **Arc Fitting** | Suaviza movimentos curvos | Habilitado (reduz vibracao) |

### Formato de Arquivo Recomendado

Para melhor qualidade, importar modelos como:
1. **STEP** (melhor - preserva curvas, permite arc fitting)
2. **3MF** (bom - pode conter perfis de fatiamento)
3. **STL** (aceitavel - formato mesh padrao)
4. **OBJ** (aceitavel)

---

## Criando Perfis Customizados

1. Selecionar um perfil base (ex: 0.20mm Standard)
2. Modificar parametros desejados
3. Salvar como novo perfil customizado
4. Perfis customizados podem ser exportados/importados

### Perfis Recomendados por Tipo de Modelo

| Tipo de Modelo | Camada | Paredes | Infill | Velocidade |
|---|---|---|---|---|
| Decorativo/Vaso | 0.08-0.12mm | 2-3 | 0-15% | Lenta |
| Miniatura | 0.08-0.12mm | 2-3 | 15-25% | Lenta |
| Funcional | 0.16-0.20mm | 4 | 20-50% | Standard |
| Prototipo rapido | 0.24-0.28mm | 2 | 10-15% | Sport/Turbo |
| Mecanico/encaixe | 0.12-0.16mm | 4+ | 30-50% | Standard |

---

## Fontes
- [Bambu Lab Wiki - Print Settings](https://wiki.bambulab.com/en/bambu-studio/parameter)
- [Bambu Lab Wiki - Layer Height](https://wiki.bambulab.com/en/software/bambu-studio/layer-height)
- [Bambu Lab Wiki - High Speed Print at Quality](https://wiki.bambulab.com/en/software/bambu-studio/high-speed-print-at-quality)
- [Bambu Lab Wiki - Quality Advanced Settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/quality-advance-settings)
- [Bambu Lab Wiki - Bridge Settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/bridge)
- [Bambu Lab Wiki - Support](https://wiki.bambulab.com/en/software/bambu-studio/support)
- [Bambu Lab Wiki - Wall Generator](https://wiki.bambulab.com/en/software/bambu-studio/wall-generator)
- [Bambu Lab Wiki - Variable Layer Height](https://wiki.bambulab.com/en/software/bambu-studio/adaptive-layer-height)
