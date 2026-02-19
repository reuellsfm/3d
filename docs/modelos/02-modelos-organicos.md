# Guia de Modelagem: Modelos Organicos e Artisticos

## Resolucao por Tipo de Modelo

| Tipo | Polycount | Voxel Size |
|------|----------|------------|
| Figura 28mm (tabletop) | 100k-300k | 0.1-0.2mm |
| Figura 75mm (display) | 200k-500k | 0.2-0.5mm |
| Busto 100mm | 300k-800k | 0.3-0.5mm |
| Estatua 200mm+ | 500k-1M | 0.5-1.0mm |

## Dimensoes Criticas para Figuras

### Membros e Apendices (escala 75mm)
```
Bracos/pernas: >= 3mm diametro (4mm+ recomendado)
Dedos: nao modelar individual, agrupar >= 2mm
Antenas/espadas base: >= 2mm, ponta >= 0.8mm
Orelhas espessura: >= 1.5mm na base, >= 0.8mm ponta
```

### Centro de Massa e Estabilidade
```
Base circular minima: diametro >= 40% da altura
  Figura 75mm -> base >= 30mm
  Figura 150mm -> base >= 60mm
Espessura da base: 2-3mm
```

### Cabelo para Impressao FDM
```
NAO modelar fios individuais

Blocos de cabelo: largura >= 2mm
Sulcos de separacao: 0.5mm profundidade, 0.4mm largura
Curvas suaves sem overhangs bruscos (< 45 graus)
```

### Texturas de Superficie
```
Pele suave: 0.1-0.2mm profundidade
Escamas/dragao: 0.3-0.5mm profundidade
Couro/casca: 0.5-1.0mm profundidade
Feature minima de textura: 0.5mm (nozzle 0.4mm)
```

## Separacao de Pecas

### Pinos de Encaixe
```
Pino cilindrico: 3mm (pino) / 3.2mm (furo) = 0.2mm gap
Profundidade: 5mm em cada peca
Quantidade: 2-3 por junta
Cola: cianoacrilato para PLA
```

## Configuracao de Impressao
```
Layer: 0.08-0.12mm
Nozzle: 0.4mm (ou 0.2mm para miniaturas)
Paredes: 3
Infill: 15% Gyroid
Suporte: Tree/Organic
Speed: Silent
Seam: Random ou Nearest (Hidden)
```

## Pos-Processamento
```
1. Remover suportes com alicate
2. Lixar: 120 -> 240 -> 400 -> 800 grit
3. Primer spray cinza
4. Lixar suave: 400 grit
5. Pintar com tinta acrilica
6. Verniz matte ou gloss
```
