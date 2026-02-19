# Perfis de Impressao por Tipo de Projeto

## Modelos Decorativos e Vasos

### Objetivo: Qualidade maxima de superficie

| Parametro | Valor | Nota |
|---|---|---|
| **Camada** | 0.08 - 0.12 mm | Extreme/High Quality |
| **Paredes** | 2-3 | Superficie lisa |
| **Infill** | 0-15% | Vasos podem ser 0% (modo vaso) |
| **Velocidade parede externa** | 50 - 80 mm/s | Reduzir para evitar ghosting |
| **Aceleracao parede externa** | 500 mm/s2 | Reduzir ringing |
| **Jerk** | 7 - 9 mm/s | Suavizar cantos |
| **Modo de velocidade** | Silent/Standard | Sem pressa |
| **Tempo minimo de camada** | 8+ segundos | Resfriamento adequado |
| **Variable Layer Height** | Recomendado | Detalhe onde necessario |

### Modo Vaso (Spiral Vase)
- Bambu Studio tem modo "Spiral Vase" para vasos/recipientes
- Imprime em uma unica espiral continua
- Parede unica - adequado apenas para vasos/recipientes
- Resultado muito liso e rapido

---

## Miniaturas e Figuras (Tabletop/D&D)

### Objetivo: Maximo detalhe em escala pequena

| Parametro | Valor | Nota |
|---|---|---|
| **Bico** | 0.2 mm | Trocar do padrao 0.4mm |
| **Camada** | 0.04 - 0.10 mm | Ultra detalhado |
| **Paredes** | 2-3 | Suficiente para escala pequena |
| **Infill** | 15 - 25% Gyroid | Leve e estrutural |
| **Velocidade** | Lenta (Silent) | Priorizar detalhe |
| **Suportes** | Tree (auto) | Mais facil de remover de detalhes finos |
| **Material** | PLA (melhor detalhe) | PETG para maior durabilidade |

### Dicas para Miniaturas
- Usar bico 0.2mm para features finas (espadas, dedos, etc.)
- Troca de bico e sem ferramentas na A1
- Orientar para minimizar suportes no rosto/detalhes frontais
- Usar suporte tree para preservar detalhes
- Considerar PLA para melhor detalhe, PETG para manuseio frequente

---

## Pecas Funcionais e Mecanicas

### Objetivo: Forca e precisao dimensional

| Parametro | Valor | Nota |
|---|---|---|
| **Camada** | 0.16 - 0.20 mm | Standard/Optimal |
| **Paredes** | 4+ | Maximizar resistencia |
| **Infill** | 20 - 50% | Cubic ou Gyroid para forca |
| **Camadas topo/base** | 5-6 | Superficie resistente |
| **Material** | PETG ou PA | PLA se nao exposto ao calor |
| **Velocidade** | Standard | Equilibrio qualidade/tempo |
| **Orientacao** | Forca no plano XY | Evitar tensao entre camadas |

### Ajustes de Precisao
- Usar X-Y Hole Compensation para furos criticos
- Fazer teste de ajuste com peca de referencia
- Projetar furos 0.2mm maiores que necessario
- Usar folga de 0.2-0.3mm para encaixes moveis
- Flow Dynamics Calibration para cada novo filamento

---

## Prototipagem Rapida

### Objetivo: Velocidade maxima, qualidade aceitavel

| Parametro | Valor | Nota |
|---|---|---|
| **Camada** | 0.24 - 0.28 mm | Draft/Extra Draft |
| **Paredes** | 2 | Minimo necessario |
| **Infill** | 10 - 15% | Economizar material |
| **Velocidade** | Sport/Turbo | Maximizar velocidade |
| **Material** | PLA | Mais rapido e facil |
| **Suportes** | Minimo | Apenas se essencial |

### Referencia de Tempo (Benchy 3DBenchy)
- 0.28mm Extra Draft + Turbo: ~19 minutos
- 0.20mm Standard: ~30-40 minutos
- 0.12mm High Quality: ~60-80 minutos
- 0.08mm Extreme: ~90-120 minutos

---

## Arquitetura e Maquetes

### Objetivo: Proporcoes corretas, boa aparencia geral

| Parametro | Valor | Nota |
|---|---|---|
| **Camada** | 0.12 - 0.16 mm | Detalhe moderado |
| **Paredes** | 2-3 | Suficiente para maquetes |
| **Infill** | 10 - 20% | Leve |
| **Material** | PLA (branco/cinza) | Facil de pintar depois |
| **Suportes** | Normal ou Hybrid | Para telhados e voladizos |
| **Brim** | Sim | Para pecas com base pequena |

### Dicas para Maquetes
- Dividir edificios grandes em secoes que cabem no volume de impressao
- Usar pinos de alinhamento nos encaixes entre pecas
- Escala comum: 1:100, 1:200, 1:500
- PLA branco e ideal para acabamento e pintura posterior
- Considerar multicolorido com AMS Lite para diferentes materiais/zonas

---

## Engrenagens e Pecas de Encaixe

### Objetivo: Maxima precisao e resistencia ao desgaste

| Parametro | Valor | Nota |
|---|---|---|
| **Camada** | 0.10 - 0.16 mm | Alta precisao |
| **Paredes** | 4-6 | Maxima resistencia |
| **Infill** | 40 - 100% | Solidez estrutural |
| **Padrao infill** | Cubic ou Concentric | Para forca radial |
| **Material** | PETG, PA, ou PLA+ | Resistencia ao desgaste |
| **Velocidade** | Standard ou Silent | Precisao > velocidade |
| **Hole Compensation** | Calibrado | Critico para encaixes |

---

## Impressao Multicolorida (AMS Lite)

### Objetivo: Multiplas cores, boa aparencia

| Parametro | Valor | Nota |
|---|---|---|
| **Camada** | 0.16 - 0.20 mm | Equilibrio qualidade/tempo |
| **Paredes** | 2-3 | Padrao |
| **Material** | PLA (todas as cores) | Melhor para purga/troca |
| **Flush volume** | Ajustar por teste | Claro apos escuro = mais flush |
| **Torre de purga** | Automatica | Minimizar com ordem de cores |

### Dica: Otimizar Ordem de Cores
1. Organizar cores do mais claro ao mais escuro
2. Minimizar numero de trocas por camada
3. Usar flush into infill quando possivel
4. Fazer teste pequeno antes de impressao grande

---

## Tabela Resumo Rapida

| Projeto | Camada | Paredes | Infill | Material | Velocidade |
|---|---|---|---|---|---|
| Decorativo | 0.08-0.12 | 2-3 | 0-15% | PLA | Silent |
| Miniatura | 0.04-0.10 | 2-3 | 15-25% | PLA | Silent |
| Funcional | 0.16-0.20 | 4+ | 20-50% | PETG | Standard |
| Prototipo | 0.24-0.28 | 2 | 10-15% | PLA | Turbo |
| Maquete | 0.12-0.16 | 2-3 | 10-20% | PLA | Standard |
| Engrenagem | 0.10-0.16 | 4-6 | 40-100% | PETG | Silent |
| Multicolor | 0.16-0.20 | 2-3 | 15% | PLA | Standard |
