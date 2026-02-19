# Configuracoes Detalhadas por Material - Bambu Lab A1

## PLA - Configuracao Completa

### Temperaturas
```
Nozzle: 210-220C (iniciar em 215C)
Cama: 55-60C
Fan: 100% apos camada 3
```

### Velocidades
```
Parede externa: 80-150mm/s
Parede interna: 150-250mm/s
Infill: 200-300mm/s
Viagem: 300-500mm/s
Primeira camada: 30-50mm/s
Bridge: 30-50mm/s
```

### Retracao (Direct Drive A1)
```
Distancia: 0.5-0.8mm
Velocidade: 30-40mm/s
Z-hop: 0.2mm (opcional, ajuda com stringing)
```

### Flow
```
Flow rate: 0.98-1.02 (calibrar com cubo)
Pressure Advance: 0.02-0.05 (auto-calibrado)
```

### Padroes Recomendados
```
Decorativo: 0.08-0.12mm layer, 2 paredes, 10% infill
Funcional: 0.16-0.20mm layer, 3 paredes, 20% Gyroid
Rapido: 0.24-0.28mm layer, 2 paredes, 10% Grid
Print-in-Place: 0.12-0.16mm layer, 2 paredes, 15% Gyroid
```

---

## PETG - Configuracao Completa

### Temperaturas
```
Nozzle: 240-250C (iniciar em 245C)
Cama: 75-80C
Fan: 40-60% (NUNCA 100% - reduz adesao entre camadas)
```

### Velocidades
```
Parede externa: 50-80mm/s (mais lento que PLA)
Parede interna: 100-150mm/s
Infill: 100-200mm/s
Viagem: 200-350mm/s
Primeira camada: 20-30mm/s
Bridge: 20-30mm/s
Aceleracao: 2500-4000mm/s2 (reduzir do padrao)
```

### Retracao
```
Distancia: 0.8-1.5mm (mais que PLA)
Velocidade: 25-35mm/s
Z-hop: 0.4mm (recomendado - reduz stringing)
Wipe: ON (ajuda com stringing)
```

### Flow
```
Flow rate: 0.95-1.00 (PETG tende a over-extrude)
Pressure Advance: 0.04-0.08
```

### Dicas Especiais PETG
```
- Reduzir aceleracao para 2500-4000mm/s2
- Usar Z-hop de 0.4mm
- Ativar Wipe
- Fan nunca acima de 60%
- Primeira camada: Z-offset +0.02mm (mais alto que PLA)
- PETG gruda DEMAIS na PEI - pode arrancar coating
- Se grudar demais: usar cola stick como BARREIRA
```

---

## TPU 95A - Configuracao Completa

### Temperaturas
```
Nozzle: 220-230C
Cama: 45-55C
Fan: 50-80%
```

### Velocidades
```
Parede externa: 15-25mm/s
Parede interna: 20-30mm/s
Infill: 25-40mm/s
Viagem: 100-150mm/s
Primeira camada: 15-20mm/s
```

### Retracao
```
Distancia: 0-0.3mm (MINIMA ou zero)
Velocidade: 15-20mm/s
Z-hop: desativado (causa bolhas)
```

### Notas Criticas
```
- NAO usar no AMS Lite (direto no extrusor)
- Velocidade maxima: 30mm/s
- Infill minimo: 20% (paredes finas flexionam)
- Paredes: 3 minimo
- Suporte: MUITO dificil de remover (evitar)
- Bridging: pessimo (< 5mm)
- Cooling: nao exagerar (pode delaminar)
```

---

## ABS - Configuracao Completa

### AVISO: A1 e open-frame. ABS requer enclosure improvisado.

### Temperaturas
```
Nozzle: 250-260C
Cama: 95-100C
Fan: 0-30% (minimo!)
Enclosure: >= 40C ambiente
```

### Velocidades
```
Parede externa: 60-100mm/s
Parede interna: 100-150mm/s
Infill: 100-200mm/s
Viagem: 200-300mm/s
Primeira camada: 20-30mm/s
```

### Retracao
```
Distancia: 0.5-1.0mm
Velocidade: 30-40mm/s
Z-hop: 0.3mm
```

### Dicas Especiais ABS
```
- ENCLOSURE OBRIGATORIO para pecas > 50mm
- Usar cola stick na placa (evita warping)
- Ventilacao: ABS emite fumes toxicos
- Nao abrir porta do enclosure durante impressao
- Deixar esfriar lentamente (sem ventilar)
- Pos-processamento: acetone vapor smoothing (superficie lisa)
```

---

## Tabela Resumo Rapida

| Param | PLA | PETG | TPU | ABS |
|-------|-----|------|-----|-----|
| Nozzle C | 215 | 245 | 225 | 255 |
| Cama C | 58 | 78 | 50 | 98 |
| Fan % | 100 | 50 | 65 | 15 |
| Speed mm/s | 200 | 100 | 25 | 120 |
| Retract mm | 0.6 | 1.0 | 0.1 | 0.7 |
| PA | 0.03 | 0.06 | N/A | 0.06 |
| AMS Lite | Sim | Sim | NAO | Sim* |

*Com enclosure

## Teste de Calibracao por Material

### Sequencia de Calibracao Recomendada
```
1. Temperature Tower (torre de temperatura)
   - Imprime secoes de 10mm em temperaturas diferentes
   - Identifica temperatura ideal por overhang, bridge, stringing

2. Flow Rate Cube (cubo de calibracao)
   - Imprimir cubo 20mm com 1 parede, 0 infill
   - Medir parede com paquimetro
   - Parede ideal = largura do nozzle (0.4mm)
   - Ajustar flow rate ate parede medir 0.40mm

3. Retraction Test (teste de stringing)
   - Imprime 2 colunas com gap entre elas
   - Ajustar retraction ate sem fios

4. Overhang Test
   - Imprime secoes com angulos crescentes
   - Identifica angulo maximo sem suporte

5. Bridging Test
   - Imprime pontes com distancias crescentes
   - Identifica distancia maxima de bridge

6. Tolerance Test
   - Imprime furo/pino de referencia
   - Mede com paquimetro
   - Calcula compensacao necessaria
```
