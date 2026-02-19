# Blender - Medidas e Escala para Impressao 3D

## Configuracao de Unidades

### Configurar Milimetros
1. `Scene Properties` (icone de cone no Properties Panel)
2. `Units:`
   - Unit System: **Metric**
   - Unit Scale: **0.001**
   - Length: **Millimeters**
   - Rotation: **Degrees**

### Escala do Objeto vs Dimensoes

**CRITICO:** Antes de exportar, a escala do objeto DEVE ser (1, 1, 1).

Verificar escala:
- Selecione o objeto > `N` (painel lateral) > Item > Scale
- Se nao for (1.000, 1.000, 1.000), aplique a escala

Aplicar escala:
- `Ctrl + A` > Scale
- Ou `Ctrl + A` > All Transforms (aplica tudo)

## Ferramentas de Medicao

### 1. Measure Tool (Regua)
- **Atalho:** Toolbar > Measure (regua)
- **Uso:** Clique e arraste entre dois pontos
- **Mostra:** distancia, angulo
- **Snap:** ative para medir entre vertices exatos

### 2. Ruler/Protractor
- **Acessar:** View > Ruler (no 3D Viewport)
- **Criar regua:** Clique e arraste
- **Protractor:** Ctrl + Click no ponto medio da regua
- **Mover pontos:** arraste os endpoints
- **Deletar:** selecione > X

### 3. Dimensions no Painel N
- Selecione o objeto > `N` > Item
- **Location:** posicao X, Y, Z
- **Rotation:** rotacao
- **Dimensions:** dimensoes reais (largura x profundidade x altura)
- **Scale:** fator de escala

### 4. Bounding Box
Visualizar dimensoes:
- `Object Properties > Viewport Display > Display As > Bounds`
- Mostra a caixa limitante com dimensoes

### 5. Edge Length (Comprimento de Aresta)
No Edit Mode:
- `Overlays > Mesh Analysis > Edge Length` (ativa exibicao)
- Ou: `Overlay dropdown > Measurement > Edge Length`
- Mostra o comprimento de cada aresta no viewport

### 6. Face Area
No Edit Mode:
- `Overlays > Measurement > Face Area`
- Mostra area de cada face

### 7. Edge Angle
No Edit Mode:
- `Overlays > Measurement > Edge Angle`
- Mostra angulo entre faces adjacentes
- Util para verificar overhangs

## Escalar para Tamanho Real

### Metodo 1: Dimensoes Diretas
1. Selecione o objeto
2. `N` > Item > Dimensions
3. Digite o tamanho desejado (ex: X: 50mm, Y: 30mm, Z: 20mm)
4. **Aplicar escala:** `Ctrl + A > Scale`

### Metodo 2: Escalar por Referencia
1. Adicione um cubo de referencia com tamanho conhecido
2. `S` > digite o fator de escala > Enter
3. Compare visualmente
4. Aplique escala quando correto

### Metodo 3: Script Python para Dimensao Exata
```python
import bpy

obj = bpy.context.active_object
# Definir dimensoes em metros (Blender usa metros internamente)
target_x = 0.050  # 50mm
target_y = 0.030  # 30mm
target_z = 0.020  # 20mm

current = obj.dimensions
obj.scale.x *= target_x / current.x
obj.scale.y *= target_y / current.y
obj.scale.z *= target_z / current.z

# Aplicar escala
bpy.ops.object.transform_apply(scale=True)
```

## Tolerancias para Impressao 3D (Bambu Lab A1)

### Tolerancia de Encaixe
Para pecas que se encaixam:
```
Encaixe justo (press-fit):     +0.1mm a +0.15mm
Encaixe deslizante (slide-fit): +0.2mm a +0.3mm
Encaixe solto (loose-fit):     +0.3mm a +0.5mm
Rosca:                         +0.2mm a +0.4mm
Snap-fit:                      +0.1mm a +0.2mm
```

### Exemplo Pratico: Furo para Parafuso M3
- Diametro do parafuso: 3.0mm
- Furo para passagem: 3.3mm - 3.5mm
- Furo para rosca: 2.5mm (para roscar no plastico)
- Furo para insert metalico: 4.0mm - 4.2mm

### Compensacao de Shrinkage (Encolhimento)
Cada material encolhe diferente:
| Material | Shrinkage | Compensacao |
|----------|-----------|-------------|
| PLA | 0.3-0.5% | +0.15-0.25% |
| PETG | 0.5-1.0% | +0.25-0.5% |
| ABS | 1.5-2.0% | +0.75-1.0% |
| TPU | 1.0-2.0% | +0.5-1.0% |
| Nylon | 1.5-2.5% | +0.75-1.25% |

## Verificacao de Dimensoes Pre-Exportacao

### Checklist
1. [ ] Unidades configuradas em milimetros
2. [ ] Escala do objeto aplicada (1, 1, 1)
3. [ ] Dimensoes verificadas no painel N
4. [ ] Tolerancias de encaixe adicionadas
5. [ ] Compensacao de shrinkage considerada
6. [ ] Origin do objeto posicionado corretamente
7. [ ] Objeto posicionado sobre o eixo Z (base no Z=0)

### Definir Origin Point
O ponto de origem afeta a posicao no slicer:
- `Object > Set Origin > Origin to Geometry` (centro do objeto)
- `Object > Set Origin > Origin to 3D Cursor` (posicao personalizada)
- `Object > Set Origin > Origin to Bottom` (base - ideal para impressao)

**Dica:** Posicione o origin na base do objeto para facilitar o posicionamento no slicer.
