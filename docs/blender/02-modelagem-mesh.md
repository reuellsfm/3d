# Blender - Modelagem com Mesh

## Conceitos Fundamentais

### Componentes de um Mesh
- **Vertices (pontos):** O elemento mais basico de um mesh, um ponto ou posicao no espaco 3D. Representados como pequenos pontos no Edit Mode. Armazenados como array de coordenadas.
- **Edges (arestas):** Sempre conectam exatamente 2 vertices por uma linha reta. Sao os "fios" visiveis em wireframe. Usados para construir faces.
- **Faces (poligonos):** Area entre 3+ vertices com uma aresta em cada lado:
  - **Triangles (tris):** 3 vertices - sempre planas, faceis de calcular
  - **Quads:** 4 vertices - preferidos para modelagem e subdivisao (deformam bem)
  - **N-gons:** 5+ vertices - evitar quando possivel (podem causar problemas)

### Edge Loops e Face Loops
- **Edge Loop:** Conjunto de arestas que formam um loop continuo ao longo do mesh
- **Face Loop:** Conjunto de faces que formam um loop continuo
- Essenciais para modelagem organica e controle de subdivisao
- Loops param em **poles** (vertices conectados a 3, 5 ou mais arestas)
- Vertices conectados a exatamente 1, 2 ou 4 arestas NAO sao poles

### Normais
- Direcao perpendicular a superficie de cada face
- Determinam o shading e qual lado e "fora" do mesh
- **Shade Smooth:** suaviza a aparencia sem alterar geometria
- **Shade Flat:** mostra cada face individualmente
- Verificar: `Overlay > Face Orientation` (azul = correto, vermelho = invertido)

### Modos de Trabalho
| Modo | Atalho | Funcao |
|------|--------|--------|
| Object Mode | Tab | Manipular objetos inteiros |
| Edit Mode | Tab | Editar vertices/edges/faces |
| Sculpt Mode | Ctrl+Tab > Sculpt | Esculpir formas organicas |

### Selecao no Edit Mode
| Componente | Atalho | Descricao |
|------------|--------|-----------|
| Vertex | 1 | Selecionar vertices |
| Edge | 2 | Selecionar arestas |
| Face | 3 | Selecionar faces |
| Loop Select | Alt + Click | Selecionar loop completo |
| Ring Select | Ctrl + Alt + Click | Selecionar ring |
| Select All | A | Selecionar tudo |
| Deselect All | Alt + A | Deselecionar tudo |
| Invert | Ctrl + I | Inverter selecao |
| Select Linked | Ctrl + L | Selecionar conectados |
| Select More/Less | Ctrl + Numpad +/- | Expandir/reduzir selecao |

## Operacoes Basicas de Transformacao

### Mover, Rotacionar, Escalar
| Operacao | Atalho | Exemplo |
|----------|--------|---------|
| Mover | G | G > X > 10 > Enter (mover 10mm em X) |
| Rotacionar | R | R > Z > 45 > Enter (rotacionar 45 graus em Z) |
| Escalar | S | S > 2 > Enter (escalar 2x) |
| Restringir eixo | G/R/S + X/Y/Z | G > Z (mover apenas em Z) |
| Excluir eixo | G/R/S + Shift+X/Y/Z | G > Shift+Z (mover em X e Y, nao Z) |
| Valor preciso | Digitar numero | G > X > 5.5 > Enter |

## Ferramentas de Modelagem (Edit Mode)

### Extrude (Extrusao)
A ferramenta mais usada em modelagem 3D:
- **Extrude Region:** `E` - extrudar faces/edges selecionados
- **Extrude Individual:** `Alt + E > Extrude Individual` - cada face separada
- **Extrude Along Normals:** `Alt + E > Extrude Along Normals` - ao longo das normais
- **Exemplo pratico:** Selecione uma face > `E` > mova o mouse > clique para confirmar

### Inset (Inserir Face)
Cria uma face menor dentro de outra:
- **Atalho:** `I`
- **Individual:** `I` > `I` (duplo) para inset individual
- **Uso:** criar bordas, preparar para extrude, detalhes

### Bevel (Chanfro)
Arredonda ou chanfra arestas:
- **Atalho:** `Ctrl + B`
- **Scroll mouse:** aumenta segmentos (mais suave)
- **Vertex Bevel:** `Ctrl + Shift + B`
- **Importante para impressao:** arredonda cantos vivos (reduz stress)

### Loop Cut
Adiciona loops de arestas:
- **Atalho:** `Ctrl + R`
- **Scroll mouse:** adiciona mais loops
- **Uso:** adicionar geometria, controlar subdivisao

### Knife Tool (Faca)
Cortar livremente a geometria:
- **Atalho:** `K`
- **Confirmar:** `Enter`
- **Cancelar:** `Esc`
- **Cut Through:** `Z` durante o corte (corta ambos lados)

### Merge (Mesclar Vertices)
- **Atalho:** `M`
- Opcoes: At Center, At Cursor, Collapse, At First, At Last
- **Merge by Distance:** `M > By Distance` (remove vertices duplicados)

### Fill (Preencher)
- **Atalho:** `F`
- Cria faces entre vertices/edges selecionados
- **Grid Fill:** `Ctrl + F > Grid Fill` (preenche com grid uniforme)

### Bridge Edge Loops
Conecta dois loops de arestas com faces:
- Selecione dois edge loops
- `Edge > Bridge Edge Loops`
- Util para conectar formas, criar tuneis

## Primitivas Mesh

### Adicionar Primitivas
`Shift + A > Mesh >`

| Primitiva | Uso Comum na Impressao 3D |
|-----------|---------------------------|
| Cube | Base para pecas mecanicas, caixas |
| Cylinder | Eixos, pinos, furos |
| Sphere (UV/Ico) | Formas organicas, juntas |
| Torus | Aneis, vedacoes, detalhes |
| Cone | Guias, transicoes |
| Plane | Bases, paredes finas |

### Painel de Ajuste (F9 apos adicionar)
Ao adicionar qualquer primitiva, pressione `F9` para ajustar:
- **Segments/Vertices:** resolucao da curva
- **Radius:** raio
- **Depth/Size:** tamanho
- **Location:** posicao exata

**Dica para impressao:** Use no minimo 32 segmentos para cilindros visiveis e 16 para furos pequenos.

## Tecnicas Avancadas

### Boolean Operations
Fundamentais para pecas mecanicas:

1. **Union (Uniao):** combina dois ou mais objetos em um unico mesh fundido
2. **Difference (Diferenca):** subtrai um do outro (criar furos, encaixes, cavidades)
3. **Intersect (Intersecao):** mantem apenas o volume que ambos ocupam

**Solvers disponiveis (Blender 4.x):**
| Solver | Velocidade | Precisao | Notas |
|--------|-----------|----------|-------|
| Fast | Rapido | Boa | Nao suporta geometria sobreposta |
| Exact | Lento | Melhor | Suporte completo para geometria sobreposta |
| Float (Manifold) | Mais rapido | Variavel | So funciona com meshes manifold |

**Como usar:**
1. Selecione o objeto base
2. Adicione modifier Boolean (`Ctrl + 1` ou Properties > Modifier)
3. Escolha a operacao (Union/Difference/Intersect)
4. Selecione o objeto cortante
5. Escolha o Solver (Exact recomendado para impressao)
6. Aplique o modifier (`Ctrl + A` no modifier)

**Bool Tool Add-on (Blender 4.2+):**
- Add-on atualizado e modernizado com novos Carver tools
- Oferece boolean rapida (brush booleans), cortes destrutivos (auto boolean)
- Workspace tools para cortar objetos com formas customizadas
- Ativar: `Edit > Preferences > Add-ons > Bool Tool`

**Boas praticas para impressao:**
- Use Exact solver para resultados mais confiaveis
- Garanta que as formas originais tenham geometria limpa
- Apos aplicar, inspecione para artefatos ou imperfeicoes
- Verifique se o resultado e manifold
- Aplique `Object > Apply > Rotation and Scale` antes de operacoes boolean

### Symmetry (Simetria)
Para pecas simetricas:
- **Mirror Modifier:** espelha automaticamente
  - Ative Clipping para evitar vertices passarem do centro
  - Merge Distance: 0.001mm
- **Symmetrize:** `Mesh > Symmetrize` (forca simetria)

### Proportional Editing
Edita vertices com influencia gradual nos vizinhos:
- **Ativar:** `O`
- **Scroll:** ajusta raio de influencia
- **Tipos:** Smooth, Sphere, Sharp, etc.

## Topologia para Impressao 3D

### Regras Essenciais
1. **Mesh deve ser Manifold (estanque):**
   - Sem buracos
   - Sem faces internas
   - Sem edges soltos
   - Sem vertices soltos
   - Sem normais invertidas

2. **Verificar normais:**
   - `Overlay > Face Orientation` (azul = correto, vermelho = invertido)
   - Corrigir: `Mesh > Normals > Recalculate Outside` (Shift+N)

3. **Espessura minima:**
   - Paredes: minimo 0.4mm (1 nozzle width) para Bambu A1
   - Recomendado: 0.8mm (2 paredes) ou mais

4. **Sem faces com area zero:**
   - Remover: `Mesh > Clean Up > Degenerate Dissolve`

5. **Sem geometria duplicada:**
   - `Mesh > Merge by Distance` (threshold: 0.001mm)

### Clean Up do Mesh
Menu: `Mesh > Clean Up`
- **Merge by Distance:** remove vertices duplicados
- **Degenerate Dissolve:** remove faces degeneradas
- **Fill Holes:** preenche buracos
- **Delete Loose:** remove vertices/edges soltos
- **Decimate Geometry:** reduz poligonos mantendo forma
