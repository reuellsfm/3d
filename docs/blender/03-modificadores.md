# Blender - Modificadores para Impressao 3D

## O que sao Modificadores?
Operacoes nao-destrutivas que alteram a geometria sem modificar o mesh original.
Acesso: `Properties Panel > Modifier Properties (icone de chave inglesa)`

**Importante:** Para exportar para impressao, os modificadores devem ser **aplicados** antes da exportacao (Ctrl+A no modifier ou aplique todos de uma vez).

## Modificadores Essenciais para 3D Print

### 1. Mirror (Espelho)
**Uso:** Modelar apenas metade de pecas simetricas

```
Configuracoes:
- Axis: X, Y e/ou Z (qual eixo espelhar)
- Clipping: ON (impede vertices de cruzar o eixo)
- Merge: ON (Distance: 0.001m = 1mm)
- Bisect: corta o mesh no eixo
- Mirror Object: usar outro objeto como centro
```

**Workflow:**
1. Delete metade do mesh (Edit Mode > selecionar metade > X)
2. Adicione Mirror Modifier
3. Ative Clipping
4. Modele apenas um lado

### 2. Solidify (Solidificar)
**Uso:** Dar espessura a superficies planas

**Modos:**
- **Simple:** Modo padrao - extruda a geometria por simples extrusao. Funciona bem para geometria simples, mas falha em edges com mais de 2 faces adjacentes.
- **Complex:** Gera mesh manifold mesmo com base nao-manifold. Lida com formas como Mobius strips, Klein bottles, layouts arquitetonicos. Mais lento que Simple.

```
Configuracoes:
- Thickness: espessura (ex: 2mm para paredes)
- Offset: -1 (para dentro), 0 (centro), 1 (para fora)
- Even Thickness: ON (espessura uniforme em angulos - ajusta para cantos agudos)
- High Quality Normals: ON (ajuda quando Even Thickness causa glitches)
- Fill Rim: ON (fecha as bordas abertas - cria edge loops entre superficies)
- Only Rim: apenas a superficie perpendicular gerada
- Clamp: limita sobreposicao
- Material Offset: usar slot de material diferente para geometria nova
```

**Modo Complex - Opcoes Adicionais:**
```
Thickness Solver:
- Flat: similar ao Simple sem Even Thickness
- Even: similar ao Simple com Even Thickness + High Quality Normals
- Constraints: modelo avancado que busca espessura otima em todo lugar

Boundary Shape:
- None: sem correcao de borda
- Round: ajusta borda para abertura voltada para dentro (como ovo)
- Flat: ajusta borda de abertura planar para ser plana (como esfera cortada)
```

**Nota:** A espessura e calculada usando coordenadas locais do vertice. Se o objeto tiver escala nao-uniforme, a espessura variara. Corrija com `Ctrl+A > Scale`.

**Dica:** Para vasos e recipientes, modele a forma externa e use Solidify para dar espessura a parede.

### 3. Boolean
**Uso:** Operacoes de uniao, subtracao e intersecao

```
Configuracoes:
- Operation: Union / Intersect / Difference
- Object: objeto para operar
- Solver:
  - Fast: simples e rapido, sem suporte para geometria sobreposta
  - Exact: complexo e preciso, suporte completo para overlaps (recomendado para impressao)
  - Float (Manifold): geralmente o mais rapido, so funciona com meshes manifold
- Self Intersection: resolver auto-intersecao (apenas Exact)
- Hole Tolerant: otimiza para geometria nao-manifold (mais lento, ativar apenas se Exact der erros)
```

**Workflow para furos:**
1. Adicione um cilindro posicionado onde quer o furo
2. No objeto principal, adicione Boolean > Difference
3. Selecione o cilindro como Object
4. Use Solver: Exact para melhor resultado
5. Esconda o cilindro (H)
6. Aplique o modifier quando satisfeito

**Workflow para corte de modelo (split para impressao):**
1. Aplique Rotation e Scale: `Object > Apply > Rotation and Scale`
2. Adicione um Plane e escale para cobrir o modelo
3. Adicione Solidify modifier no Plane para dar espessura
4. Aplique o Solidify
5. Use Boolean > Difference no modelo com o Plane como cortante

### 4. Subdivision Surface
**Uso:** Suavizar mesh com mais geometria

```
Configuracoes:
- Levels Viewport: 1-2 (para trabalhar)
- Levels Render: 2-3 (para exportar)
- Quality: 3+ para impressao
- UV Smooth: Keep Corners
- Boundary Smooth: Keep Corners (preserva bordas vivas)
```

**Controle de Creases:**
- Selecione edges > `Shift + E` > arraste para definir crease
- Crease 1.0 = borda totalmente viva
- Crease 0.0 = totalmente suavizado
- Alternativa: adicione Edge Loops proximos para endurecer

### 5. Array (Repeticao)
**Uso:** Criar padroes repetitivos

```
Configuracoes:
- Count: numero de copias
- Relative Offset: distancia relativa ao tamanho do objeto
- Constant Offset: distancia fixa em mm
- Object Offset: usar outro objeto para definir transformacao
- Merge: ON (conectar copias adjacentes)
```

**Exemplos:**
- Engrenagens: Array circular com Object Offset (Empty rotacionado)
- Correntes: Array linear com offset
- Padroes decorativos: Array em X e Y

### 6. Bevel (Chanfro)
**Uso:** Arredondar arestas (reduz concentracao de stress)

```
Configuracoes:
- Width: largura do chanfro
- Segments: 2-4 (mais = mais suave)
- Limit Method:
  - Angle: aplica em arestas acima de certo angulo
  - Weight: controle individual por edge
  - Vertex Group: grupo especifico
- Profile: 0.5 = arco, 0.25 = mais reto
- Clamp Overlap: evita sobreposicao
```

**Para impressao:** Use Bevel em todas as arestas vivas. Cantos vivos concentram stress e podem quebrar.

### 7. Decimate (Reduzir Poligonos)
**Uso:** Reduzir vertex/face count com minimas alteracoes de forma. Ideal para meshes de sculpting, modelos escaneados, ou apos aplicar Subdivision/Multiresolution.

```
Modos:

1. Collapse (padrao):
   - Ratio: 1.0 = sem alteracao, 0.5 = metade, 0.0 = remove tudo
   - Nota: ratio usa triangulos no calculo - quads/n-gons podem resultar
     em mais faces que o esperado se Triangulate estiver OFF
   - Symmetry: mantem simetria em um eixo
   - Triangulate: mantem geometria triangulada resultante
   - Vertex Group: controla quais areas sao decimadas
   - Factor: quantidade de influencia do vertex group

2. Un-Subdivide:
   - Iterations: vezes para reverter subdivisao
   - 2 iteracoes = reverso de 1 subdivisao (use numeros pares)
   - Funciona melhor em meshes com topologia grid uniforme

3. Planar:
   - Angle Limit: dissolve geometria com angulos menores que este valor
   - All Boundaries: dissolve vertices nas bordas (melhor com Angle alto)
   - Delimit:
     - Normal: nao dissolve bordas onde normais sao invertidas
     - Material: nao dissolve bordas entre materiais diferentes
     - Seam: nao dissolve edges marcadas como seam
```

**Quando usar:**
- Mesh com muitos poligonos (>500k) que trava o slicer
- Modelos escaneados com excesso de detalhe
- Reduzir tamanho de arquivo STL
- Apos escultura com Dyntopo ou Multires aplicado

### 8. Remesh
**Uso:** Reconstruir a topologia do mesh uniformemente

```
Modos (Blocks, Smooth e Sharp tem topologia quase identica - difere no smoothing):

1. Blocks:
   - Sem suavizacao alguma
   - Resultado blocado/pixelizado
   - Util para modelos estilizados (voxel art)

2. Smooth:
   - Superficie suave sem deteccao de sharp features
   - Bom para formas organicas gerais

3. Sharp:
   - Similar ao Smooth, mas preserva arestas e cantos vivos
   - Sharpness: valores altos = mais fiel ao original, baixos = filtra ruido
   - Recomendado para pecas mecanicas

4. Voxel:
   - Usa OpenVDB para gerar mesh manifold a partir da geometria atual
   - Tenta preservar o volume original
   - Voxel Size: tamanho do voxel no espaco do objeto (menor = mais detalhe)
     Default: 0.1 | Para impressao: 0.5-2mm
   - Adaptivity: reduz face count simplificando areas sem detalhe
     (introduz triangulacao)

Configuracoes Comuns:
- Octree Depth: resolucao do output (1-24, default: 4)
  Valores altos = mais denso e detalhado
- Smooth Shading: aplica smooth shading no output (nao preserva input)
```

**Dicas:**
- O mesh de input deve ter alguma espessura. Se for plano, adicione Solidify acima do Remesh
- Use Voxel Remesh apos operacoes booleanas complexas para limpar a topologia
- Voxel remesh e especialmente util para combinar multiplos meshes em um unico objeto manifold
- Baseado no paper "Dual Contouring of Hermite Data" (modos Blocks/Smooth/Sharp)

### 9. Screw (Parafuso/Torno)
**Uso:** Criar formas de revolucao e roscas

```
Configuracoes:
- Angle: angulo de revolucao (360 = volta completa)
- Steps: resolucao da curva
- Screw: distancia por volta (para roscas)
- Axis: eixo de revolucao
- Iterations: numero de voltas
```

**Para criar roscas de parafuso:**
1. Crie o perfil da rosca (triangulo em vista lateral)
2. Aplique Screw modifier
3. Ajuste Steps (32+), Screw (passo da rosca), Iterations (voltas)

### 10. Shrinkwrap
**Uso:** Projetar mesh sobre outro

```
Tipos:
- Nearest Surface Point: projeta no ponto mais proximo
- Project: projeta ao longo de eixo
- Nearest Vertex: projeta no vertice mais proximo
- Target Surface: projeta na superficie
```

**Uso em impressao:** Criar labels, relevos e texturas sobre superficies curvas.

### 11. Weld
**Uso:** Mesclar vertices proximos automaticamente

```
Configuracoes:
- Distance: distancia maxima para merge (0.01mm para impressao)
- Vertex Group: aplicar apenas em grupo especifico
```

### 12. Weighted Normal
**Uso:** Melhorar aparencia de normais sem alterar geometria

```
Configuracoes:
- Mode: Face Area / Corner Angle / Face Area and Angle
- Keep Sharp: preservar arestas marcadas como sharp
```

## Ordem dos Modificadores (Stack)

A ordem importa! Recomendacao para impressao 3D:

```
1. Mirror          (simetria primeiro)
2. Array           (repeticoes)
3. Boolean         (cortes e unioes)
4. Subdivision     (suavizacao)
5. Solidify        (espessura)
6. Bevel           (chanfros)
7. Remesh          (limpeza final se necessario)
8. Decimate        (reducao se necessario)
```

## Aplicando Modificadores para Exportacao

### Aplicar Individual
- Hover sobre o modifier > `Ctrl + A`
- Ou clique no dropdown > Apply

### Aplicar Todos
1. Selecione o objeto
2. `Ctrl + A` > Visual Geometry to Mesh
   Ou: Use script Python:
```python
import bpy
obj = bpy.context.active_object
for mod in obj.modifiers:
    bpy.ops.object.modifier_apply(modifier=mod.name)
```

### Importante Antes de Aplicar
- **Salve uma copia** antes de aplicar (os modifiers nao podem ser revertidos)
- Verifique se o resultado esta correto no viewport
- Aplique na ordem correta (de cima para baixo)
