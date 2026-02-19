# Guia de Modelagem: Miniaturas e Figuras

## Escalas Comuns para Miniaturas

| Escala | Altura Humana | Uso |
|--------|--------------|-----|
| 28mm | 28mm | Wargames (Warhammer, D&D) |
| 32mm | 32mm | RPG tabletop moderno |
| 54mm | 54mm | Miniaturas de colecao |
| 75mm | 75mm | Display/painting |
| 1:10 (180mm) | 180mm | Bustos e figuras premium |

## Limites de Detalhe por Nozzle e Layer

### Nozzle 0.4mm (Padrao)
```
Detalhe minimo XY: 0.4mm
Detalhe minimo Z: layer height (0.08-0.28mm)

Escala 28mm (humano ~28mm altura):
  Olho: ~1.5mm -> IMPOSSIVEL detalhar iris
  Nariz: ~2mm -> forma basica apenas
  Dedo: ~0.8mm -> agrupados, nao individuais
  Botao de roupa: ~0.8mm -> basico
  Cinto: ~1mm -> visivel

Escala 75mm:
  Olho: ~4mm -> forma basica detectavel
  Nariz: ~5mm -> detalhavel
  Dedo: ~2mm -> agrupados, possivel separar
  Botao: ~2mm -> visivel
  Cinto: ~3mm -> detalhavel
  Textura de roupa: 0.5mm -> no limite
```

### Nozzle 0.2mm (Recomendado para Miniaturas)
```
Detalhe minimo XY: 0.2mm
Detalhe minimo Z: 0.04-0.14mm

Escala 28mm:
  Olho: ~1.5mm -> forma detectavel
  Nariz: ~2mm -> detalhavel
  Dedo: ~0.8mm -> possivel individual
  Botao: ~0.8mm -> detectavel
  Escrita em escudo: ~0.5mm -> no limite

Escala 75mm:
  Todos os detalhes acima ficam EXCELENTES
  Textura de pele: 0.3mm -> possivel
  Cabelo individual (mecha): ~1mm -> possivel
  Olhos com iris: ~1mm pupila -> basico
```

## Detalhes Milimetricos por Parte do Corpo

### Cabeca (Escala 75mm)
```
Cabeca total: ~18mm diametro
Olho: 4mm x 2.5mm (largura x altura)
  - Nao modelar iris/pupila (pintar)
  - Cavidade do olho: 0.5mm profundidade
Nariz: 5mm projecao, 4mm largura
Boca: sulco 0.5mm profundidade
Orelha: 7mm altura, 1.5mm espessura na borda
Queixo: projecao 3-4mm

Pescoço: 8-10mm diametro
  Se articulado: ball joint 6mm esfera, gap 0.25mm
```

### Torso (Escala 75mm)
```
Largura ombros: ~25mm
Espessura torso: ~12mm
Cintura: ~15mm largura

Detalhes de roupa:
  Colarinho: 1mm projecao, 1.5mm espessura
  Botoes: 2mm diametro, 0.5mm projecao
  Costuras: sulco 0.3mm profundidade, 0.4mm largura
  Cinto: 2-3mm largura, 1mm espessura
  Fivela: 3-4mm, 0.5mm projecao
```

### Membros (Escala 75mm)
```
Braco superior: 6-8mm diametro
Antebraco: 5-6mm diametro
Mao: 5mm x 3mm (sem dedos individuais)
  - Dedos agrupados: 2-3mm bloco
  - Polegar separado: 1.5mm

Coxa: 8-10mm diametro
Canela: 5-7mm diametro
Pe: 8mm comprimento, 4mm largura

Articulacoes ball joint:
  Ombro: esfera 5mm, socket 5.5mm (0.25mm gap cada lado)
  Cotovelo: esfera 4mm, socket 4.5mm
  Quadril: esfera 5mm, socket 5.5mm
  Joelho: esfera 4mm, socket 4.5mm
```

### Acessorios (Escala 75mm)
```
Espada: 3mm largura lamina, 1.5mm espessura
  Punho: 3mm diametro, 15-20mm comprimento
  Guarda: 8mm x 2mm
  Lamina: engrossar para 1.5mm (muito fino = quebra)

Escudo: 1.5-2mm espessura, borda 2.5mm
  Emblema em relevo: 0.5mm projecao

Arco: 2mm espessura, corda OMITIR (usar fio real)

Cajado/bastao: 2.5-3mm diametro
  Orbe no topo: 4-5mm diametro

Mochila/bolsa: 5mm x 4mm x 3mm minimo
```

## Articulacoes Dummy 13 Style

### Dimensoes de Ball Joint
```
Para figura ~130mm (Dummy 13):
  Pescoco: esfera 8mm, socket 8.5mm, gap 0.25mm
  Ombro: esfera 10mm, socket 10.5mm, gap 0.25mm
  Cotovelo: esfera 7mm, socket 7.5mm, gap 0.25mm
  Punho: esfera 5mm, socket 5.5mm, gap 0.25mm
  Quadril: esfera 10mm, socket 10.5mm, gap 0.25mm
  Joelho: esfera 8mm, socket 8.5mm, gap 0.25mm
  Tornozelo: esfera 6mm, socket 6.5mm, gap 0.25mm

Socket depth: >= 50% diametro da esfera
  Esfera 10mm: socket depth >= 5mm
  Abertura do socket: 70-80% do diametro (para capturar)
```

### Print-in-Place para Articulacoes
```
Gap: 0.20mm - 0.25mm (nozzle 0.4mm)
Layer: 0.12mm (melhor resolucao vertical para esferas)
Suporte: DESATIVADO nas articulacoes
Cooling: 100%
Speed: Silent ou Standard
First layer: 0.20mm

IMPORTANTE:
  - Esfera e socket devem ser impressos NA MESMA PECA
  - O gap permite que a esfera se solte apos impressao
  - Mover manualmente apos impressao para liberar
```

### Modularidade (Compatibilidade)
```
Ao modificar membros (mais fortes, mais longos):
  - MANTER diametro da esfera/socket ORIGINAL
  - Alterar apenas o corpo do membro
  - Isso garante compatibilidade com pecas originais

Exemplo: "Deixar braco mais musculoso"
  - Aumentar escala X,Y do biceps/antebraco
  - NAO alterar esfera do ombro/cotovelo
  - Verificar centro de massa apos modificacao
```

## Bases para Miniaturas

### Dimensoes Padrao
```
25mm redonda: D&D/Pathfinder standard
32mm redonda: Warhammer/40K infantry
40mm redonda: Warhammer special units
50mm redonda: Warhammer monsters
60mm redonda: Warhammer large models

Espessura: 2-3mm
Borda: 1mm chanfro ou 2mm lip
```

### Texturas de Base
```
Terra/areia: Sculpt com noise texture, 0.5-1mm
Pedra: blocos 3-5mm com 0.3mm gap
Grama: tufos 1-2mm (ou usar grama statica real)
Neve: smooth com ondulacoes suaves
Metal/deck: linhas paralelas 0.3mm profundidade
```

## Configuracao de Impressao para Miniaturas

### Setup Ideal (28-32mm)
```
Nozzle: 0.2mm (TROCAR do padrao)
Layer: 0.06mm
Paredes: 3
Infill: 20% Gyroid
Suporte: Tree (auto, threshold 40 graus)
Speed: Silent (max precisao)
Cooling: 100%
Material: PLA grey (melhor para detectar detalhes e pintar)
Seam: Random
Interface suporte: 2 layers, 0.10mm gap
```

### Setup Aceitavel (75mm+)
```
Nozzle: 0.4mm (padrao)
Layer: 0.08mm
Paredes: 3
Infill: 15% Gyroid
Suporte: Tree
Speed: Silent
Material: PLA grey
```

### Setup Rapido (prototipo)
```
Nozzle: 0.4mm
Layer: 0.16mm
Paredes: 2
Infill: 10%
Speed: Standard
Material: PLA qualquer
```
