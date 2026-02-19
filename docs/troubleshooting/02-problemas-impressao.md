# Problemas de Impressao - Troubleshooting Bambu Lab A1

## 1. Primeira Camada Nao Adere

### Sintomas
- Filamento nao gruda na placa
- Modelo descola durante impressao
- Cantos levantando (warping)

### Causas e Solucoes

| Causa | Solucao |
|---|---|
| **Placa suja** | Lavar com agua morna + detergente (NAO usar acetona na PEI texturizada) |
| **Oleosidade** | Nao tocar na superficie; manusear pelas bordas |
| **Temperatura da cama baixa** | Aumentar levemente (PLA: 55-60C, PETG: 80-90C) |
| **Z-offset incorreto** | Executar calibracao automatica |
| **Placa gasta** | Lixar com lixa 600; substituir se muito desgastada |
| **Tipo de placa errado** | Verificar se a placa selecionada no slicer corresponde a instalada |
| **Area de contato pequena** | Adicionar brim (3-8mm) |
| **Velocidade 1a camada alta** | Reduzir para 15-20 mm/s |

### Configuracoes de Primeira Camada Otimas
- **Largura de linha:** 0.5 mm
- **Altura de camada:** 0.25 mm (para bico 0.4mm)
- **Velocidade:** 15-20 mm/s (se com problemas)

### Uso de Cola
- PLA na Textured PEI: NAO usar cola (piora adesao)
- PETG na Textured PEI: NAO usar cola
- ABS/ASA/PC/PA: Usar cola Bambu Lab na placa
- NUNCA usar colas de terceiros (podem danificar a placa)

---

## 2. Warping (Empenamento)

### Sintomas
- Cantos do modelo levantam da cama
- Base do modelo curva

### Solucoes
1. **Limpar a placa** adequadamente
2. **Aumentar temperatura da cama** em 5-10C
3. **Adicionar brim** (aumenta area de contato)
4. **Usar enclosure** (essencial para ABS/ASA)
5. **Reduzir velocidade de impressao**
6. **Projetar com cantos arredondados** (menos stress termico)
7. **Mouse ears:** Adicionar pequenos discos nos cantos no slicer

---

## 3. Stringing (Fios entre partes)

### Sintomas
- Fios finos de plastico entre partes do modelo
- Blobs na superficie

### Solucoes

| Ajuste | Direcao | Nota |
|---|---|---|
| **Retracao** | Aumentar distancia/velocidade | Padrao e bom para PLA |
| **Temperatura do bico** | Reduzir 5-10C | Material menos fluido |
| **Velocidade de viagem** | Aumentar | Menos tempo no ar |
| **Wipe** | Habilitar | Limpa bico antes de viajar |
| **Combing** | Habilitar | Evita cruzar partes abertas |
| **Filamento umido** | Secar filamento | Causa principal em muitos casos |

### PETG Especificamente
- PETG e propenso a stringing
- Reduzir temperatura para 225-235C
- Aumentar retracao
- Reduzir aceleracao para 2500-4000 mm/s2

---

## 4. Entupimento do Bico (Clogging)

### Sintomas
- Sub-extrusao parcial ou total
- Estalos/clicks no extrusor
- Filamento nao sai do bico

### Solucoes

| Metodo | Como Fazer |
|---|---|
| **Cold Pull** | Usar nylon/cleaning filament, aquecer a 250C, puxar a 90-100C |
| **Limpeza manual** | Aquecer bico, remover filamento, usar agulha de limpeza |
| **Trocar bico** | Se cold pull nao resolver; bico pode estar danificado |
| **Verificar PTFE** | Tubo PTFE pode estar obstruido |
| **Secar filamento** | Umidade causa bolhas que entopem |

### Prevencao
- Usar filamento seco e de boa qualidade
- Nao exceder temperatura maxima do filamento
- Limpar bico periodicamente
- Usar bico endurecido para filamentos abrasivos (CF/GF)

---

## 5. Layer Shifting (Deslocamento de Camadas)

### Sintomas
- Camadas deslocadas horizontalmente
- Modelo com aparencia "deslizada"

### Causas e Solucoes

| Causa | Solucao |
|---|---|
| **Correias frouxas** | Verificar e apertar correias dos eixos |
| **Velocidade muito alta** | Reduzir velocidade/aceleracao |
| **Modelo colidindo com bico** | Verificar se modelo nao levanta (warping) |
| **Motor perdendo passos** | Verificar drivers e conexoes |
| **Obstrucao mecanica** | Limpar trilhos e verificar obstrucoes |

---

## 6. Sub-Extrusao

### Sintomas
- Lacunas entre perimetros
- Paredes finas/fracas
- Camadas visivelmente separadas

### Solucoes
1. **Verificar entupimento parcial** (cold pull)
2. **Calibrar fluxo** (Flow Dynamics Calibration)
3. **Aumentar temperatura do bico** em 5C
4. **Reduzir velocidade** de impressao
5. **Verificar filamento** (diametro consistente, sem umidade)
6. **Verificar engrenagens do extrusor** (desgaste, sujeira)

---

## 7. Parafusos do Hotend Soltos

### Sintomas
- Primeira camada sempre muito baixa mesmo apos nivelamento
- Bico arranha a placa
- Qualidade de impressao inconsistente

### Causa
- Vibracoes afrouxam parafusos de montagem do hotend

### Solucao
1. Verificar se a trava (clip) do conjunto de aquecimento esta correta
2. Apertar parafusos de fixacao do hotend
3. Testar manualmente se ha folga no hotend
4. Executar nivelamento automatico apos reinstalacao

---

## 8. Blob of Death (Bolha da Morte)

### Sintomas
- Falha catastrofica onde PLA acumula em uma grande bolha
- PLA se espalha pelo hotend e partes mecanicas
- Pode danificar o clip de fixacao do elemento de aquecimento

### Prevencao
1. **Monitorar primeiras camadas** via camera ou presencialmente
2. **Habilitar deteccao de falha** no firmware
3. **Verificar adesao da 1a camada** antes de deixar impressao sozinha
4. **Manter firmware atualizado**

### Se Acontecer
1. Esperar esfriar completamente
2. Aquecer hotend a ~200C para amolecer PLA
3. Remover cuidadosamente com ferramentas
4. Verificar danos ao clip e hotend
5. Pode ser necessario substituir pecas

---

## 9. Problemas com AMS Lite

### Filamento Atolado
1. Pressionar botao de liberacao para desengatar motor
2. Remover e reinserir filamento
3. Verificar tubos PTFE (curvas acentuadas, desgaste)
4. Limpar engrenagens do alimentador (poeira causa deslizamento)

### Filamento Quebrando na Retracao
- Causa mais comum: **filamento umido**
- Secar filamento antes de usar
- Adicionar dessecante dentro do AMS

### Falha na Deteccao RFID
- Reposicionar bobina no slot
- Limpar area do leitor RFID
- Para filamentos de terceiros: configurar manualmente

---

## 10. Problemas de Wi-Fi/Conectividade

### Solucoes
1. Usar rede **2.4 GHz** (A1 nao suporta 5 GHz bem)
2. Verificar se roteador nao separa bandas automaticamente
3. Mover impressora para mais perto do roteador
4. Usar microSD como alternativa

---

## 11. Camera Nao Funciona

### Solucoes
1. **Power cycle completo:** Desligar, desconectar da tomada por 30-60 segundos
2. **Verificar conexoes:** Cabos da camera podem se soltar com vibracao
3. **Atualizar firmware**
4. **Reset de fabrica** (ultimo recurso)

---

## 12. Qualidade de Superficie Ruim

### Ghosting/Ringing
| Ajuste | Valor |
|---|---|
| Reduzir aceleracao da parede externa | 500-1000 mm/s2 |
| Reduzir jerk | 7-9 mm/s |
| Habilitar input shaping | Via calibracao automatica |

### Linhas de Camada Visiveis
| Ajuste | Valor |
|---|---|
| Reduzir altura de camada | 0.08-0.12 mm |
| Usar Variable Layer Height | Detalhe onde necessario |
| Ironing | Habilitar para topo liso |

### Costura (Seam) Visivel
| Ajuste | Valor |
|---|---|
| Seam Position | Aligned (concentra) ou Random (distribui) |
| Nearest | Para geometrias complexas |

---

## Dicas Gerais de Manutencao

1. **Manter firmware atualizado** (impressora E Bambu Studio)
2. **Re-fatiar apos atualizacoes** de firmware ou slicer
3. **Lubrificar trilhos** conforme manual
4. **Limpar placa regularmente** (agua + detergente)
5. **Armazenar filamento seco** (sacos selados + dessecante)
6. **Executar calibracao** apos alteracoes mecanicas
7. **Monitorar primeiras camadas** de cada impressao

---

## Fontes
- [Bambu Lab Wiki - A1 Troubleshooting](https://wiki.bambulab.com/en/a1/troubleshooting)
- [Bambu Lab Wiki - First Layer Not Sticking](https://wiki.bambulab.com/en/knowledge-sharing/first-layer-not-sticking)
- [Bambu Lab Wiki - Common Print Quality Problems](https://wiki.bambulab.com/en/knowledge-sharing/common-print-quality-problem)
- [Bambu Lab Wiki - Textured PEI Plate Troubleshooting](https://wiki.bambulab.com/en/general/textured-PEI-plate-not-working-as-expected)
- [Bambu Lab Wiki - Bad Bridging Quality](https://wiki.bambulab.com/en/filament-acc/filament/print-quality/bridging)
- [Innocube3D - A1 Troubleshooting Guide](https://www.innocube3d.com/blogs/news/how-to-fix-common-bambulab-a1-print-quality-issues-complete-troubleshooting-guide)
