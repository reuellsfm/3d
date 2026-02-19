# Blender - Add-ons Recomendados para Impressao 3D

## Add-ons Nativos (inclusos no Blender)

### 1. 3D-Print Toolbox
**Essencial para qualquer workflow de impressao 3D**
- Ativacao: `Edit > Preferences > Add-ons > Mesh: 3D-Print Toolbox`
- Funcoes: verificacao de mesh, analise de espessura, overhangs, manifold
- Acesso: Sidebar (`N`) > 3D-Print

### 2. Bool Tool
**Operacoes booleanas rapidas**
- Ativacao: `Edit > Preferences > Add-ons > Object: Bool Tool`
- Funcoes: Union, Difference, Intersect com atalhos rapidos
- Atalhos: `Ctrl + Shift + B` (menu Bool Tool)

### 3. LoopTools
**Ferramentas adicionais para loops**
- Ativacao: `Edit > Preferences > Add-ons > Mesh: LoopTools`
- Funcoes: Bridge, Circle, Curve, Flatten, Relax, Space
- Acesso: `Right Click > LoopTools` no Edit Mode

### 4. F2
**Preenchimento de faces inteligente**
- Ativacao: `Edit > Preferences > Add-ons > Mesh: F2`
- Melhora o `F` (fill) com preenchimento mais inteligente
- Reconhece padroes e preenche de forma mais limpa

### 5. Mesh: Tiny CAD
**Ferramentas de precisao tipo CAD**
- Funcoes: intersecar edges, projetar vertices, gerar perpendiculares

### 6. Curve: Extra Objects
**Curvas adicionais**
- Funcoes: espirais, helicoides, perfis de engrenagem
- Util para roscas e molas

### 7. Mesh: Extra Objects
**Mesh primitivas adicionais**
- Funcoes: engrenagens, parafusos, poliedros, rochas, pipes
- Ideal para pecas mecanicas

### 8. Import-Export: STL Format
- Normalmente ja ativo
- Ativacao: `Edit > Preferences > Add-ons > Import-Export: STL`

## Add-ons da Comunidade (Download Separado)

### 9. CAD Sketcher (Gratuito)
**Desenho parametrico 2D no Blender (estilo Fusion 360)**
- Site: https://www.cadsketcher.com/
- Funcoes:
  - Sketches 2D com constraints (dimensoes, paralelo, perpendicular)
  - Extrude para 3D
  - Workflow parametrico
- Ideal para: pecas mecanicas, encaixes precisos
- Instalacao: baixar .zip > `Preferences > Add-ons > Install from Disk`

### 10. Mesh Heal (Gratuito)
**Reparacao automatica de meshes**
- Funcoes: corrigir non-manifold, preencher buracos, limpar mesh
- Mais poderoso que o 3D-Print Toolbox para reparos

### 11. Precise Align
**Alinhamento preciso de objetos**
- Funcoes: alinhar por faces, edges, vertices
- Ideal para: posicionar pecas mecanicas, alinhamento de montagem

### 12. Geometry Nodes Presets
**Nodes prontos para operacoes comuns**
- Funcoes: arrays parametricos, padroes, deformacoes
- Agiliza o uso de Geometry Nodes

### 13. Hard Ops / BoxCutter (Pagos)
**Ferramentas profissionais de hard-surface modeling**
- Hard Ops: workflow otimizado para pecas mecanicas
  - Booleans rapidos, sharpening automatico, mirror tools
- BoxCutter: cortes booleanos em tempo real
  - Cortar, fatiar, criar encaixes rapidamente
- Preco: ~$20 cada (Blender Market)
- Ideal para: modelagem mecanica profissional

### 14. MESHmachine (Pago)
**Edicao avancada de mesh**
- Funcoes: fuse, unfuse, flatten, turn corners, plug
- Ideal para: corrigir topologia apos booleans
- Preco: ~$30 (Blender Market)

### 15. Machin3tools (Gratuito)
**Ferramentas de produtividade**
- Smart Vert, Smart Face, Smart Edge
- Focus, Mirror, Clean Up automaticos
- Pie menus customizados

## Geometry Nodes para Impressao 3D

### O que sao Geometry Nodes?
Sistema visual de programacao no Blender para gerar e modificar geometria proceduralmente.

### Aplicacoes para Impressao 3D

#### 1. Padroes Repetitivos (Lattice/Grid)
```
Criar um padrao de furos em uma placa:
1. Geometry Nodes editor
2. Grid > Instance on Points > Cylinder (Boolean Difference)
3. Parametros ajustaveis: spacing, diametro, pattern
```

#### 2. Texturas de Superficie
```
Criar textura tipo "grip" ou escamas:
1. Mesh surface > Distribute Points on Faces
2. Instance on Points > forma desejada
3. Controlar densidade e aleatoriedade
```

#### 3. Estruturas Internas (Infill Customizado)
```
Criar estrutura gyroid ou voronoi interna:
1. Volume Cube > Volume to Mesh
2. Noise Texture para gerar padrao
3. Boolean com o objeto externo
```

#### 4. Engrenagens Parametricas
```
Gerar engrenagens com parametros ajustaveis:
1. Curve Circle > Resample (dentes)
2. Scale por indice (par/impar)
3. Fill > Extrude
```

### Scripts Blender para Geometry Nodes de Impressao
```python
import bpy

# Criar node group para array circular
def create_circular_array():
    # Criar novo node group
    ng = bpy.data.node_groups.new("CircularArray", 'GeometryNodeTree')

    # Input/Output
    input_node = ng.nodes.new('NodeGroupInput')
    output_node = ng.nodes.new('NodeGroupOutput')

    # Adicionar parametros
    ng.interface.new_socket("Count", in_out='INPUT', socket_type='NodeSocketInt')
    ng.interface.new_socket("Radius", in_out='INPUT', socket_type='NodeSocketFloat')
    ng.interface.new_socket("Geometry", in_out='OUTPUT', socket_type='NodeSocketGeometry')

    print("Circular Array node group criado!")

create_circular_array()
```

## Configuracao Recomendada de Add-ons

### Para Iniciantes em Impressao 3D
1. 3D-Print Toolbox (nativo)
2. Bool Tool (nativo)
3. LoopTools (nativo)
4. F2 (nativo)
5. Mesh: Extra Objects (nativo)

### Para Usuarios Intermediarios
Todos os anteriores +
6. CAD Sketcher (gratuito)
7. Machin3tools (gratuito)
8. Curve: Extra Objects (nativo)

### Para Profissionais
Todos os anteriores +
9. Hard Ops (pago)
10. BoxCutter (pago)
11. MESHmachine (pago)
