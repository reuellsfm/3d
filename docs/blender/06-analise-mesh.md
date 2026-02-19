# Blender - Analise de Mesh para Impressao 3D

## 3D Print Toolbox

### Ativacao
1. `Edit > Preferences > Add-ons`
2. Buscar "3D-Print" ou "3D Print Toolbox"
3. Ativar `Mesh: 3D-Print Toolbox`
4. Versao atual: v1.3.2 (Janeiro 2026, compativel com Blender 4.2+)

### Acesso
`3D Viewport > Sidebar (N-Panel) > aba 3D-Print`
(Requer um mesh selecionado)

### Novidades Recentes
- **v1.3.2** (Jan 2026): Object/Mesh menu search operators, layout mais compacto do Sidebar Edit, fix Scale to Volume/Bounds com objetos nao-mesh
- **v1.3.0** (Dez 2025): Hollow tool como modifier (Blender 5.0+), Bisect modifier tool para cortar ao longo de plano

## Secao Analyze

### Estatisticas

| Funcao | Descricao |
|--------|-----------|
| **Volume** | Calcula o volume total do mesh (em unidades da cena, ex: mm3) |
| **Area** | Calcula a area total da superficie |
| Se volume for negativo = normais invertidas |

### Checks (Verificacoes)

#### 1. Solid (Manifold)
**O que verifica:** Edges nao-manifold e edges com contiguidade ruim.
- Edges devem conectar exatamente **2 faces**
- Edge com 1 face = **buraco no mesh**
- Edge com 3+ faces = **nao-manifold** (impossivel fatiar corretamente)
- **Bad Contiguous:** face com normal apontando em direcao diferente dos vizinhos

**Como corrigir:**
- Selecionar edges de borda > `F` (fill)
- `Select > All by Trait > Non Manifold` para encontrar problemas
- Recalcular normais: `Shift + N`

#### 2. Intersections (Intersecoes)
**O que verifica:** Faces que se cruzam dentro do mesh.
- Exemplo: dois cubos sobrepostos
- **Solucao:** Boolean modifier (Union) para fundir, Voxel Remesh, ou remover manualmente
- **Nota:** Alguns slicers conseguem lidar com intersecoes, mas nao e garantido

#### 3. Degenerate (Degeneradas)
**O que verifica:** Faces/edges com area ou comprimento zero.
- Triangulos com area zero (3 vertices na mesma linha)
- Edges com comprimento zero (vertices duplicados)
- **Solucao:** `Mesh > Merge > By Distance` (remove vertices duplicados)

#### 4. Distorted (Distorcidas)
**O que verifica:** Quads e N-gons nao-planos.
- Faces com 4+ vertices onde os vertices nao estao no mesmo plano
- Pode causar artefatos no slicing
- **Solucao:** Triangulacao manual ou automatica

#### 5. Thickness (Espessura)
**O que verifica:** Geometria fina demais para ser impressa.
- Configure o limite minimo de espessura do seu printer:
  - Nozzle 0.4mm: minimo = 2x largura do nozzle = **0.8mm**
  - Para paredes estruturais: **1.2mm** (3 paredes)
- Areas em **vermelho** sao problematicas
- **Solucao:** Adicionar espessura via modifiers (Solidify) ou editar geometria

#### 6. Edge Sharp (Arestas Afiadas)
**O que verifica:** Arestas afiadas que criam geometria fina problematica.
- Cantos muito agudos podem ser impossiveis de imprimir
- **Solucao:** Bevel modifier ou `Ctrl+B` para chanfrar

#### 7. Overhang (Saliencias)
**O que verifica:** Faces que necessitam de suporte para imprimir.
- Impressoras 3D nao imprimem no ar
- Limite padrao: **45 graus** da vertical (ajustavel)
- Faces acima deste angulo precisam de material de suporte
- Ajuste o campo "Angle" no 3D-Print Toolbox conforme sua impressora

#### 8. Check All
Executa **todas** as verificacoes acima simultaneamente.
- Resultados mostram partes invalidas do mesh
- Em **Edit Mode**, clicar nos resultados seleciona os componentes problematicos

### Exemplo Pratico
A Suzanne (macaco) padrao mostra varios problemas:
- Olhos sao partes separadas
- Cavidades dos olhos tem buracos
- Mesh nao e Solid
- Faces Intersecting
- Algumas faces Distorted

## Secao Clean Up

### Distorted
- Triangula automaticamente faces distorcidas flagadas
- Converte n-gons problematicos em triangulos planos

### Make Manifold
Tenta reparar varios problemas que tornam o mesh nao-manifold:
- Corrige normais ruins
- Preenche buracos
- Remove edges e faces vazias

**Aviso:** Use com cautela!
- Pode alterar significativamente a geometria
- Pode introduzir novos erros
- **Recomendacao:** Use o toolbox para **identificar** problemas, mas prefira correcoes manuais em Edit Mode para resultados mais limpos e confiaveis.

## Secao Transform

| Ferramenta | Funcao |
|------------|--------|
| **Scale to Volume** | Escala o mesh para um volume exato especificado |
| **Scale to Bounds** | Escala o maior eixo para corresponder ao valor dado |

### Hollow Tool (v1.3.0+, Blender 5.0+)
- Cria espessura consistente para formas complexas como modifier
- Util para pecas que precisam ser ocas

### Bisect Modifier Tool (v1.3.0+)
- Corta objetos ao longo de um plano
- Util para dividir modelos grandes para impressao

### Align to Print Bed
- Rotaciona modelo alinhando face selecionada ao plano de impressao

## Secao Export
Acesso rapido aos operadores de `File > Export`:
- **STL** (.stl)
- **PLY** (.ply)
- **OBJ** (.obj)

## Mesh Analysis Panel (Complementar ao 3D Print Toolbox)

### Acesso
- `Properties Shelf (N-panel)` em **Edit Mode**
- Painel separado do 3D Print Toolbox

### Funcionalidade
Gera um **heatmap** (mapa de calor) sobre o mesh - diferente do 3D Print Toolbox que da respostas sim/nao por face:
- **Vermelho:** areas mais problematicas
- **Verde/Azul:** areas OK

### Modos de Analise
| Modo | Visualizacao |
|------|-------------|
| Overhang | Heatmap de angulo de saliencia |
| Thickness | Heatmap de espessura de parede |
| Distortion | Heatmap de distorcao de faces |
| Intersect | Destaca faces que se cruzam |
| Sharp | Destaca arestas muito afiadas |

## Verificacao Manual de Normais

### Ativar Visualizacao
1. `Viewport Overlays` (no header do 3D Viewport)
2. Ativar `Face Orientation`
3. **Azul = normal correta** (apontando para fora)
4. **Vermelho = normal invertida** (apontando para dentro)

### Corrigir Normais
1. Entre em Edit Mode (`Tab`)
2. Selecione tudo (`A`)
3. `Mesh > Normals > Recalculate Outside` (`Shift + N`)
4. Se faces individuais ainda estiverem invertidas:
   - Selecione a face
   - `Mesh > Normals > Flip`

### Verificar Manifold Manualmente
- Edit Mode > `Select > All by Trait > Non Manifold`
- Vertices/edges nao-manifold serao selecionados
- Corrija preenchendo buracos (`F`), removendo faces internas, ou ajustando

### Verificar Espessura com Secao Transversal
1. Adicione um plano (`Shift+A > Mesh > Plane`)
2. Escale grande o suficiente para cortar o modelo
3. Ative Boolean modifier no modelo > Intersect
4. Mova o plano para ver secoes diferentes
5. Verifique visualmente a espessura

## Workflow de Verificacao Pre-Exportacao

```
1. [ ] Aplicar todas as transformacoes (Ctrl+A > All Transforms)
2. [ ] Aplicar todos os modifiers necessarios
3. [ ] Verificar Scale = 1.0, 1.0, 1.0 (N-panel)
4. [ ] Ativar Face Orientation overlay - verificar normais (sem vermelho)
5. [ ] Recalcular normais se necessario (Shift+N)
6. [ ] Abrir 3D Print Toolbox (N-panel > 3D-Print)
7. [ ] Clicar "Check All"
8. [ ] Resolver problemas Solid (manifold) - PRIORITARIO
9. [ ] Resolver Intersections com Boolean Union
10. [ ] Verificar Thickness com limite da sua impressora
11. [ ] Avaliar Overhangs e planejar suportes
12. [ ] Remover Degenerates (Merge by Distance)
13. [ ] Corrigir Distorted faces (triangular se necessario)
14. [ ] Verificar volume e dimensoes
15. [ ] Limpar mesh final:
      - Mesh > Clean Up > Merge by Distance (threshold: 0.001mm)
      - Mesh > Clean Up > Degenerate Dissolve
      - Mesh > Clean Up > Delete Loose
16. [ ] Verificacao final: Check All novamente
17. [ ] Exportar
```

## Reparar Mesh com Problemas

### Metodo Automatico: Voxel Remesh
1. Object Mode > Properties > Remesh (ou Sculpt Mode header)
2. Mode: Voxel
3. Voxel Size: 0.5-1mm (menor = mais detalhe, mais poligonos)
4. Smooth Normals: ON
5. `Ctrl + R` para aplicar
6. **Resultado:** mesh limpo, manifold, uniforme

### Metodo Manual
1. Identifique problemas com Non Manifold select
2. Preencha buracos com `F` ou `Ctrl+F > Grid Fill`
3. Remova faces internas
4. Recalcule normais (`Shift+N`)
5. Merge by Distance (`M > By Distance`)
6. Verifique novamente com Check All

### Usando MeshLab (ferramenta externa)
Para meshes muito problematicos:
1. Exporte como STL do Blender
2. Abra no MeshLab
3. Filters > Cleaning and Repairing > Repair Non Manifold Edges
4. Exporte e reimporte no Blender
