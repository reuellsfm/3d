# Bambu Lab A1 - Restricoes de Design e Diretrizes

## Visao Geral

Este guia cobre as limitacoes fisicas e praticas ao projetar modelos 3D para impressao
na Bambu Lab A1. Seguir estas diretrizes resulta em impressoes mais confiaveis e com
melhor qualidade.

---

## Tamanhos Minimos e Maximos de Features

### Volume Maximo de Impressao
- **256 x 256 x 256 mm** (XYZ)

### Espessura Minima de Parede

| Condicao | Espessura | Notas |
|---|---|---|
| **Minimo absoluto** | 0.3 mm | Pode imprimir com qualidade reduzida |
| **Minimo recomendado** | 0.4 mm | 1 largura de bico (bico 0.4mm) |
| **Parede confiavel** | 0.8 mm | 2 larguras de bico - recomendado |
| **Parede forte** | 1.2 mm | 3 larguras de bico |

### Regras do Slicer para Features Finas (bico 0.4mm)

| Parametro | Valor | Descricao |
|---|---|---|
| **Minimum Feature Size** | 0.10 mm (25% do bico) | Features menores sao ignoradas |
| **Minimum Wall Width** | 0.34 mm (85% do bico) | Paredes finas sao engrossadas |

Para imprimir features finas, use o **Arachne wall generator** com:
- Minimum Wall Thickness: 85% ou maior
- Minimum Feature Size: 5%
- Isso engrossara paredes finas automaticamente

---

## Angulos de Overhang

O angulo de overhang e medido entre a superficie inclinada do modelo e a cama de impressao.

### Regras de Overhang

| Angulo (da cama) | Suporte Necessario? | Qualidade |
|---|---|---|
| **90** (vertical) | Nao | Perfeito |
| **60 - 89** | Nao | Boa qualidade |
| **45 - 59** | Geralmente nao | Aceitavel (pode precisar ajustes) |
| **30 - 44** | SIM recomendado | Qualidade degradada sem suporte |
| **< 30** | SIM obrigatorio | Impossivel sem suporte |

### Regra Geral: 45 Graus
- Overhangs com angulo >= 45 da cama geralmente imprimem sem suporte
- Abaixo de 45 da cama, habilitar suportes no Bambu Studio
- Para overhangs sem suporte: reduzir temperatura do bico + aumentar ventilacao

### Dicas para Melhorar Overhangs
1. Reduzir levemente a temperatura do bico
2. Aumentar velocidade do fan (cooling fan + auxiliary fan)
3. Habilitar "Auto Slow Down for Overhangs" (padrao no Bambu Studio)
4. Considerar orientacao do modelo para minimizar overhangs

---

## Ponte (Bridging)

Uma ponte e quando o filamento e extrudado no ar, entre duas areas suportadas, sem suporte
por baixo.

### Distancias de Ponte

| Distancia | Resultado | Acao |
|---|---|---|
| **< 5 mm** | Excelente | Sem necessidade de ajuste |
| **5 - 10 mm** | Bom | Funciona com configuracoes padrao |
| **10 - 20 mm** | Variavel | Ajustar bridge flow e velocidade |
| **> 20 mm** | Dificil | Usar suportes ou redesenhar |

### Parametro Max Bridge Length
- Padrao: ~10 mm no Bambu Studio
- Pontes maiores que este valor sao divididas em segmentos com pontos de suporte

### Como Melhorar Pontes
1. **Aumentar Bridge Flow:** Mais material por linha de ponte, permite linhas adjacentes
   se tocarem e colarem
2. **Mudar Bridge Direction:** Reduz distancia sem suporte dependendo da geometria
3. **Thick Bridges:** Extruda com fluxo maior, mais confiavel em distancias longas
   (mas superficie inferior fica pior)
4. **Reduzir velocidade de ponte:** Mais tempo para o filamento resfriar e solidificar

---

## Folgas e Tolerancias para Encaixes

### Folgas Recomendadas

| Tipo de Encaixe | Folga Recomendada | Descricao |
|---|---|---|
| **Press-fit (justo)** | 0.1 - 0.15 mm | Encaixe por pressao |
| **Deslizante** | 0.2 - 0.25 mm | Peca desliza com leve atrito |
| **Livre** | 0.3 - 0.5 mm | Movimento livre |
| **Peca girante** | 0.4 - 0.6 mm | Eixos e rotacoes |

### Compensacao de Furos
- Furos imprimem ~0.1 - 0.3 mm MENORES que o projetado
- Usar X-Y Hole Compensation no Bambu Studio
- Ou projetar furos 0.2mm maiores que o desejado

### Compensacao de Eixos/Pinos
- Eixos/pinos imprimem ~0.05 - 0.15 mm MAIORES que o projetado
- Considerar ao projetar encaixes macho/femea

---

## Suportes

### Quando Usar Suportes

| Situacao | Suporte? | Tipo Recomendado |
|---|---|---|
| Overhangs < 45 da cama | Sim | Hybrid (auto) |
| Grandes superficies planas suspensas | Sim | Normal |
| Geometrias complexas com overhangs | Sim | Tree ou Hybrid |
| Pontes > 10 mm | Sim | Normal |
| Modelos sem overhangs | Nao | - |

### Tipos de Suporte no Bambu Studio

| Tipo | Vantagens | Desvantagens |
|---|---|---|
| **Normal** | Melhor superficie em overhangs planos | Mais material, mais dificil de remover |
| **Tree** | Menos material, mais facil de remover | Superficie pode ser pior |
| **Hybrid (Auto)** | Melhor dos dois mundos | Automatico - recomendado geral |

### Dicas de Suporte
- **Top Z Distance:** Manter gap padrao para facil remocao
- **Support Interface:** Usar camadas de interface para melhor acabamento
- Considerar orientacao do modelo para minimizar necessidade de suporte
- Partes tocando a cama NAO precisam de suporte

---

## Orientacao do Modelo

A orientacao do modelo na cama afeta significativamente:

### Fatores Afetados pela Orientacao

| Fator | Impacto |
|---|---|
| **Forca** | Camadas sao fracas em tencao entre si (eixo Z) |
| **Qualidade de superficie** | Superficies voltadas para cima = melhor |
| **Necessidade de suporte** | Orientar para minimizar overhangs |
| **Tempo de impressao** | Menos altura = menos camadas = mais rapido |
| **Adesao a cama** | Mais area de contato = melhor adesao |

### Diretrizes de Orientacao
1. **Maximizar area de contato com a cama** para melhor adesao
2. **Direcao de forca no eixo XY** (nao Z) para maior resistencia
3. **Superficies criticas voltadas para cima** para melhor acabamento
4. **Minimizar overhangs** para reduzir suporte necessario
5. **Evitar pecas altas e finas** sem brim/suporte

---

## Restricoes por Tipo de Feature

### Features Positivas (Saliencias)

| Feature | Tamanho Minimo | Notas |
|---|---|---|
| **Texto em relevo** | 0.5 mm largura, 0.3 mm altura | Usar fonte bold |
| **Detalhes decorativos** | 0.4 mm | 1 largura de bico |
| **Pinos/colunas** | 1.0 mm diametro | Menor que isso quebra facilmente |

### Features Negativas (Entalhes/Furos)

| Feature | Tamanho Minimo | Notas |
|---|---|---|
| **Furos** | 1.0 mm diametro | Menores tendem a fechar |
| **Entalhes/ranhuras** | 0.5 mm largura | Depende da orientacao |
| **Texto entalhado** | 0.6 mm largura, 0.3 mm profundidade | Mais facil que em relevo |

### Cantos e Raios

| Feature | Recomendacao |
|---|---|
| **Cantos internos** | Adicionar raio >= 0.5 mm (evita concentracao de tensao) |
| **Cantos externos** | Podem ser vivos |
| **Filetes em base** | Adicionar filete de 1-2 mm para melhor adesao |

---

## Checklist de Design para A1

- [ ] Espessura minima de parede >= 0.4 mm (ideal 0.8 mm)
- [ ] Furos projetados 0.2 mm maiores que desejado
- [ ] Overhangs <= 45 da cama ou com suportes
- [ ] Pontes <= 10 mm (ou com suportes)
- [ ] Folga de 0.2-0.3 mm em encaixes moveis
- [ ] Modelo dentro de 256 x 256 x 256 mm
- [ ] Mesh watertight (manifold) sem buracos
- [ ] Normais das faces orientadas corretamente
- [ ] Escala verificada (1 unidade Blender = 1 mm ou metros conforme config.)
- [ ] Area de contato com cama suficiente para adesao
- [ ] Features finas >= 0.4 mm

---

## Fontes
- [Bambu Lab Wiki - Support](https://wiki.bambulab.com/en/software/bambu-studio/support)
- [Bambu Lab Wiki - How to Print Overhangs](https://wiki.bambulab.com/en/filament-acc/filament/print-quality/overhang)
- [Bambu Lab Wiki - Bridge Settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/bridge)
- [Bambu Lab Wiki - Wall Generator](https://wiki.bambulab.com/en/software/bambu-studio/wall-generator)
- [Bambu Lab Wiki - Quality Advanced Settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/quality-advance-settings)
- [Bambu Lab Wiki - Auto Circle Compensation](https://wiki.bambulab.com/en/software/bambu-studio/manual/auto-circle-contour-compensation)
- [Bambu Lab Community Forum](https://forum.bambulab.com)
