# Guia de Modelagem: Arquitetura e Maquetes

## Escalas Comuns para Maquetes

| Escala | 1m Real = | Uso | Volume A1 Equivale a |
|--------|----------|-----|---------------------|
| 1:50 | 20mm | Interiores detalhados | 12.8m x 12.8m x 12.8m |
| 1:100 | 10mm | Edificios individuais | 25.6m x 25.6m x 25.6m |
| 1:200 | 5mm | Conjuntos de edificios | 51.2m x 51.2m x 51.2m |
| 1:500 | 2mm | Quadras urbanas | 128m x 128m x 128m |
| 1:1000 | 1mm | Master plans | 256m x 256m x 256m |

## Dimensoes Minimas por Escala

### Escala 1:100 (mais comum)
```
Parede interna (10cm real): 1.0mm -> OK (>= 0.8mm)
Parede externa (20cm real): 2.0mm -> OK
Coluna 30cm: 3.0mm -> OK
Coluna 15cm: 1.5mm -> OK
Escada (1.2m real): 12mm -> detalhavel
Porta (0.8m real): 8mm largura -> OK
Janela frame (5cm): 0.5mm -> limite minimo
Corrimao (5cm): 0.5mm -> dificil, considerar omitir ou engrossar
```

### Escala 1:200
```
Parede interna (10cm real): 0.5mm -> no limite
Parede externa (20cm real): 1.0mm -> OK
Coluna 30cm: 1.5mm -> OK
Escada: 6mm -> basico
Porta: 4mm -> OK
Janela frame: 0.25mm -> IMPOSSIVEL, simplificar
```

### Escala 1:500
```
Parede: 0.2-0.4mm -> somente externas, simplificar
Edificio inteiro: apenas forma externa e volumetria
Detalhes internos: impossivel
Recomendacao: apenas volumes e silhuetas
```

## Workflow de Maquete no Blender

### Passo 1: Importar Planta
```
1. File > Import > Image as Plane
2. Escalar a planta para dimensao real
   Exemplo 1:100: se edificio tem 20m, escalar para 200mm
3. Usar como referencia (nao exportar)
```

### Passo 2: Extrusao de Plantas
```
1. Desenhar contorno com vertices (Edit Mode)
2. Extrudar para cima (E + Z + altura)
   Exemplo: andar de 3m em 1:100 = 30mm extrude
3. Repetir por andar
4. Adicionar lajes (Plane escalado na posicao)
```

### Passo 3: Detalhes
```
Janelas: Boolean Difference com retangulo
  1:100: janela 1.0m x 1.5m = 10mm x 15mm (OK)
  Depth da moldura: 0.5mm - 1.0mm

Portas: Boolean ou simplesmente rebaixo
  1:100: porta 0.8m x 2.1m = 8mm x 21mm

Telhados: modelar como mesh separado
  Inclinacao tipica: 15-30 graus
  Espessura: 1.0mm minimo

Escadas: usar Array modifier com steps
  1:100: step 17cm = 1.7mm altura, 28cm = 2.8mm profundidade
```

### Passo 4: Divisao em Partes
```
Para edificios maiores que 256mm:
1. Boolean > cortar em secoes
2. Adicionar pinos de alinhamento (3mm + 3.2mm furo)
3. Numerar as pecas (texto gravado na base)

Divisao tipica:
  - Base/terreno: separado
  - Cada andar: separado (se detalhado)
  - Telhado: separado
  - Elementos decorativos: separados
```

## Terreno e Topografia

### Modelar Terreno
```
1. Plane com subdivisions (Ctrl+R para loop cuts)
   Grid: 10x10 ou 20x20 (depende do detalhe)
2. Sculpt Mode > Grab brush para elevar/rebaixar
3. Smooth brush para suavizar
4. Solidify modifier: 3-5mm de espessura
```

### Curvas de Nivel
```
1. Importar curvas de nivel como SVG (File > Import > SVG)
2. Converter para mesh (Object > Convert > Mesh)
3. Extrudar cada curva para a altura correspondente
4. Preencher entre curvas com Bridge Edge Loops
5. Smooth final
```

## Vegetacao Simplificada
```
Arvores (1:100):
  Tronco: cilindro 1mm diametro
  Copa: esfera 5-10mm diametro
  Ou: cone para coniferas

Arvores (1:500):
  Ponto elevado 2-3mm
  Representacao simbolica apenas

Grama/vegetacao: textura no terreno (nao modelar)
```

## Configuracao de Impressao para Maquetes
```
Layer: 0.12-0.16mm
Paredes: 2-3
Infill: 10-15%
Material: PLA branco ou cinza claro
Suporte: Normal ou Hybrid
Brim: Sim (pecas com base pequena)
Speed: Standard
```

## Multicolor com AMS Lite para Maquetes
```
Cor 1: Branco - estrutura principal
Cor 2: Cinza - telhados/lajes
Cor 3: Verde - areas verdes/terreno
Cor 4: Azul - agua/piscina

Pintura pos-impressao: alternativa mais flexivel
```
