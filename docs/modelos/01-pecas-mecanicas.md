# Guia de Modelagem: Pecas Mecanicas e Encaixes

## Tabela de Tolerancias Milimetricas Precisas (Bambu A1, Nozzle 0.4mm)

### Furos Padrao - Compensacao Necessaria

| Furo Projetado | Imprime Como | Projetar Como | Compensacao |
|----------------|-------------|---------------|-------------|
| M2 (2.0mm) | ~1.75mm | 2.25mm | +0.25mm |
| M2.5 (2.5mm) | ~2.25mm | 2.75mm | +0.25mm |
| M3 (3.0mm) | ~2.75mm | 3.25mm | +0.25mm |
| M4 (4.0mm) | ~3.75mm | 4.25mm | +0.25mm |
| M5 (5.0mm) | ~4.80mm | 5.20mm | +0.20mm |
| M6 (6.0mm) | ~5.80mm | 6.20mm | +0.20mm |
| M8 (8.0mm) | ~7.85mm | 8.20mm | +0.20mm |
| M10 (10.0mm) | ~9.85mm | 10.20mm | +0.20mm |

### Pinos/Eixos - Compensacao Necessaria

| Pino Projetado | Imprime Como | Projetar Como | Compensacao |
|----------------|-------------|---------------|-------------|
| 2.0mm | ~2.10mm | 1.90mm | -0.10mm |
| 3.0mm | ~3.10mm | 2.90mm | -0.10mm |
| 4.0mm | ~4.08mm | 3.92mm | -0.08mm |
| 5.0mm | ~5.08mm | 4.92mm | -0.08mm |
| 6.0mm | ~6.06mm | 5.94mm | -0.06mm |
| 8.0mm | ~8.05mm | 7.95mm | -0.05mm |

### Encaixes Macho-Femea

#### Press-Fit (Permanente)
```
Gap total: 0.05mm - 0.10mm
Exemplo: Pino 4.95mm em furo 5.05mm
Resultado: Conexao firme, requer forca para encaixar
Uso: montagem permanente, pinos de alinhamento
```

#### Snap-Fit (Encaixe por pressao)
```
Gap: 0.10mm - 0.15mm
Deflexao do clip: 0.3mm - 0.8mm
Angulo de entrada: 30-45 graus
Angulo de retencao: 80-90 graus
Espessura do clip: 1.0mm - 1.5mm
Comprimento do clip: 5mm - 15mm

Exemplo no Blender:
  - Crie um retangulo 1.2mm x 8mm na parede
  - Extrude 0.5mm para fora (protuberancia)
  - Chanfre a entrada em 45 graus
  - No receptor: cavidade 1.4mm x 8.2mm (gap 0.1mm)
```

#### Dovetail (Rabo de Andorinha)
```
Angulo: 10-14 graus
Gap: 0.15mm - 0.20mm
Profundidade: >= 3mm
Largura minima: 5mm
Comprimento: variavel

Para impressao:
  - Imprimir com o dovetail na horizontal (melhor tolerancia)
  - Chanfrar entrada em 0.5mm para facilitar montagem
```

### Roscas Imprimiveis

| Rosca | Imprimivel (0.4mm)? | Notas |
|-------|---------------------|-------|
| M2 | NAO | Muito fino |
| M3 | Dificil | Possivel com 0.2mm nozzle |
| M4 | Possivel | Gap +0.3mm, passo grosso |
| M5 | Sim | Gap +0.2mm |
| M6+ | Sim | Funciona bem |

#### Inserts Metalicos (Heat-Set Inserts)
```
M2:   furo 3.2mm, profundidade 3.5mm
M2.5: furo 3.5mm, profundidade 4.0mm
M3:   furo 4.0mm, profundidade 4.5mm
M4:   furo 5.0mm, profundidade 5.5mm
M5:   furo 6.0mm, profundidade 6.5mm
```

#### Nut Traps (Captura de Porca)
```
M3 nut: cavidade hexagonal 5.9mm (chave) x 2.6mm profundidade
M4 nut: cavidade hexagonal 7.2mm x 3.4mm profundidade
M5 nut: cavidade hexagonal 8.2mm x 4.2mm profundidade
```

### Engrenagens
```
Modulo minimo imprimivel: 1.0 (nozzle 0.4mm)
Modulo recomendado: 1.5 - 2.0
Numero minimo de dentes: 8
Gap entre dentes: 0.15mm - 0.20mm
Folga de eixo: 0.20mm
Espessura minima do dente: 0.8mm
```

### Dobradicas Print-in-Place
```
Eixo: 3mm diametro minimo
Gap ao redor do eixo: 0.25mm
Cap do eixo: oversize 0.5mm
Layer height: 0.12mm recomendado
Orientacao: eixo paralelo a mesa
```

### Nervuras de Reforco
```
Espessura: 60-80% da parede principal
  Parede 1.2mm -> nervura 0.8mm
  Parede 2.0mm -> nervura 1.2-1.6mm
Altura: <= 3x espessura da nervura
Espacamento: 2-4x a espessura da parede
Filete na base: 0.25-0.5x espessura da nervura
```

## Tabela Rapida de Dimensoes Criticas

| Parametro | Valor (mm) |
|-----------|-----------|
| Min. parede imprimivel | 0.4 |
| Min. parede funcional | 0.8 |
| Min. parede mecanica | 1.2 |
| Min. furo imprimivel | 1.0 |
| Min. pino imprimivel | 1.0 |
| Compensacao de furo | +0.20 a +0.25 |
| Compensacao de pino | -0.05 a -0.10 |
| Gap press-fit | 0.05-0.10 |
| Gap slide-fit | 0.15-0.25 |
| Gap loose-fit | 0.25-0.40 |
| Gap print-in-place | 0.20-0.30 |
| Min. texto relevo | 0.5h, 0.4w |
| Min. texto gravado | 0.4d, 0.5w |
| Min. chanfro | 0.3 |
| Min. filete | 0.5 |
| Min. snap-fit | 1.0 espessura |
| Precisao XY | +/- 0.1 |
| Precisao Z | +/- 0.05 |

## Configuracao Bambu Studio para Pecas Mecanicas
```
Paredes: 3-4
Infill: 30% Gyroid
Layer: 0.16mm
Suporte: Organic quando necessario
Velocidade: Standard
Seam: Aligned (area nao-funcional)
Top/Bottom: 5 camadas
```
