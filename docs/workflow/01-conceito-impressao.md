# Workflow Completo: Do Conceito a Impressao

## Visao Geral do Fluxo de Trabalho

```
Conceito/Ideia
    |
    v
Modelagem 3D (Blender)
    |
    v
Preparacao do Mesh (Blender)
    |
    v
Exportacao (STL/3MF/STEP)
    |
    v
Importacao no Bambu Studio
    |
    v
Configuracao de Fatiamento (Slicer)
    |
    v
Fatiamento (Slice)
    |
    v
Envio para Impressora
    |
    v
Impressao
    |
    v
Pos-Processamento
```

---

## Etapa 1: Modelagem no Blender

### Configuracao Inicial
- Definir unidades: **Metric, Scale 0.001** (1 Blender unit = 1mm)
  OU usar **Metric, Scale 1.0** (1 Blender unit = 1m) e escalar na exportacao
- Ativar add-on: **3D-Print Toolbox** (Edit > Preferences > Add-ons)

### Diretrizes de Modelagem para Impressao 3D
1. **Mesh manifold (watertight):** Sem buracos, arestas soltas, ou vertices duplicados
2. **Normais consistentes:** Todas as faces apontando para fora
3. **Sem faces sobrepostas:** Nenhuma geometria se cruzando
4. **Espessura adequada:** Paredes >= 0.4 mm (bico 0.4mm)
5. **Escala correta:** Verificar dimensoes antes de exportar

### Ferramentas Uteis no Blender
- **3D-Print Toolbox > Check All:** Verifica problemas no mesh
- **Mesh > Clean Up > Merge by Distance:** Remove vertices duplicados
- **Mesh > Normals > Recalculate Outside:** Corrige normais
- **Ctrl+A > All Transforms:** Aplica transformacoes antes de exportar
- **Boolean modifiers:** Para operacoes de uniao/subtracao de geometria

---

## Etapa 2: Preparacao do Mesh

### Checklist de Verificacao

| Verificacao | Como Fazer | Ferramenta |
|---|---|---|
| Mesh watertight | Sem buracos ou gaps | 3D-Print Toolbox > Check All |
| Normais corretas | Todas para fora | Mesh > Normals > Recalculate |
| Sem non-manifold | Sem arestas livres | 3D-Print Toolbox > Non-Manifold |
| Sem faces zero-area | Remover degeneradas | 3D-Print Toolbox > Degenerate |
| Escala aplicada | Scale = 1,1,1 | Ctrl+A > Scale |
| Rotacao aplicada | Rotation = 0,0,0 | Ctrl+A > Rotation |
| Dimensoes corretas | Verificar em N-panel | Panel N > Dimensions |

### Correcao de Problemas Comuns

**Mesh com buracos:**
1. Selecionar arestas do buraco (Select > All by Trait > Non-Manifold)
2. Preencher (F para Face ou Mesh > Fill)
3. Verificar novamente

**Normais invertidas:**
1. Selecionar tudo (A)
2. Mesh > Normals > Recalculate Outside
3. Verificar visualmente com Face Orientation overlay

**Geometria cruzada (self-intersecting):**
1. Usar 3D-Print Toolbox para detectar
2. Corrigir manualmente ou usar Boolean modifier
3. Remesh se necessario

---

## Etapa 3: Exportacao do Blender

### Formatos Suportados pelo Bambu Studio

| Formato | Vantagens | Recomendacao |
|---|---|---|
| **STEP** | Preserva curvas, melhor arc fitting, menores detalhes | MELHOR (se disponivel) |
| **3MF** | Pode incluir cores, materiais, perfis de slicer | BOM para multicolorido |
| **STL (binary)** | Universal, menor tamanho que ASCII | PADRAO mais comum |
| **OBJ** | Suporta textura e cor | Aceitavel |

### Exportar STL do Blender

1. Selecionar objeto(s) para exportar
2. **File > Export > STL (.stl)**
3. Configuracoes de exportacao:
   - **Selection Only:** Marcar (exportar apenas selecionado)
   - **Apply Modifiers:** Marcar
   - **Scale:** Depende da unidade usada no Blender
     - Se usou mm (Scale 0.001): Scale = 1.0
     - Se usou m (Scale 1.0): Scale = 1000 (para converter m para mm)
   - **ASCII vs Binary:** Binary (menor arquivo)
4. Verificar tamanho do arquivo (STL grandes podem causar lentidao)

### Exportar OBJ do Blender
1. **File > Export > Wavefront (.obj)**
2. Configuracoes similares ao STL
3. Incluir materiais se necessario

---

## Etapa 4: Importacao no Bambu Studio

### Importar Modelo
1. Abrir Bambu Studio
2. **File > Import > Import 3MF/STL/STEP/SVG/OBJ/AMF...**
3. Selecionar arquivo exportado
4. O modelo aparece na placa de construcao virtual

### Verificacoes Pos-Importacao
1. **Escala correta:** Verificar dimensoes no painel direito
2. **Posicao na cama:** Modelo deve tocar a cama
3. **Orientacao:** Ajustar para minimizar suportes e maximizar qualidade
4. **Multiplos modelos:** Posicionar com espaco adequado entre eles

### Ferramentas de Posicionamento
- **Mover:** Posicionar modelo na cama
- **Rotacionar:** Ajustar orientacao
- **Escalar:** Redimensionar se necessario
- **Lay on Face:** Clicar em uma face para deita-la na cama
- **Auto-orient:** Bambu Studio pode sugerir orientacao otima

---

## Etapa 5: Configuracao de Fatiamento

### Selecionar Perfis

1. **Impressora:** Bambu Lab A1 0.4mm Nozzle (ou outro bico)
2. **Filamento:** PLA / PETG / TPU etc. (selecionar marca/tipo)
3. **Processo:** Escolher perfil de qualidade (0.08mm a 0.28mm)

### Ajustes Comuns

| Parametro | Onde Encontrar | Quando Ajustar |
|---|---|---|
| **Infill %** | Process > Strength | Pecas funcionais: aumentar |
| **Paredes** | Process > Strength | Pecas fortes: 4+, decorativas: 2 |
| **Suportes** | Process > Support | Overhangs < 45 |
| **Brim** | Process > Others | Pecas pequenas ou altas |
| **Velocidade** | Process > Speed | Qualidade vs. tempo |
| **Temp. bico** | Filament > Temperature | Ajuste fino por material |

---

## Etapa 6: Fatiar e Enviar

### Fatiamento
1. Clicar em **Slice Plate** (canto superior direito)
2. Visualizar preview:
   - Verificar camadas individualmente
   - Checar suportes gerados
   - Confirmar tempo estimado e uso de material
3. Se necessario, ajustar configuracoes e re-fatiar

### Envio para Impressora
- **Wi-Fi:** Print Plate > selecionar impressora > enviar
- **microSD:** Export G-code > copiar para cartao SD
- **LAN:** Envio direto pela rede local

---

## Etapa 7: Impressao

### Antes de Imprimir
1. Verificar que a placa de construcao esta limpa
2. Confirmar que o filamento correto esta carregado
3. Verificar nivel de filamento restante
4. Confirmar que a placa correta esta selecionada no slicer

### Durante a Impressao
- Monitorar via camera ou app Bambu Handy
- Verificar primeiras camadas (adesao)
- Ajustar velocidade se necessario (Silent/Standard/Sport/Turbo)
- A calibracao automatica ocorre no inicio de cada impressao

### Apos a Impressao
1. Esperar a cama esfriar ate ~35C ou menos
2. Remover o modelo flexionando a placa de aco
3. Remover suportes cuidadosamente
4. Lixar/acabar conforme necessario

---

## Fontes
- [Bambu Lab Wiki - Setting Guide of Slicing Parameters](https://wiki.bambulab.com/en/software/bambu-studio/how-to-set-slicing-parameters)
- [Bambu Lab Community Forum - 3MF vs STL](https://forum.bambulab.com/t/3mf-vs-stl-files/81214)
- [Bambu Lab Community Forum - Fusion 360 Export](https://forum.bambulab.com/t/fusion-360-stl-vs-obj-vs-3mf-in-3d-print-option/87111)
