# Blender - Escultura Digital (Sculpt Mode)

## Quando Usar Escultura?
- Modelos organicos (figuras, criaturas, rostos)
- Detalhes de superficie (texturas, relevos)
- Formas naturais (rochas, terrenos, plantas)
- Refinamento de formas base

## Acessar Sculpt Mode
1. Selecione o objeto
2. `Ctrl + Tab` > Sculpt Mode
3. Ou dropdown no header > Sculpt Mode

## Preparacao do Mesh para Escultura

### Resolucao Necessaria
Para esculpir detalhes, o mesh precisa de muitos poligonos:

1. **Metodo 1 - Subdivision:**
   - Em Object Mode, adicione Subdivision Surface modifier
   - Levels: 4-6 (para escultura detalhada)
   - Aplique o modifier

2. **Metodo 2 - Remesh (recomendado):**
   - No Sculpt Mode, header > Remesh
   - Voxel Size: 0.5mm - 2mm (menor = mais detalhe)
   - `Ctrl + R` para aplicar remesh

3. **Metodo 3 - Dyntopo (Dynamic Topology):**
   - Ative no header do Sculpt Mode
   - Adiciona geometria dinamicamente onde voce esculpe
   - Detail Size: controla resolucao
   - Detailing: Relative (adapta ao zoom) ou Constant

## Pinceis Essenciais (Brushes)

### Pinceis de Forma
| Pincel | Atalho | Funcao |
|--------|--------|--------|
| Draw | X | Pincel basico, adiciona/remove volume |
| Clay | C | Adiciona volume em camadas (como argila) |
| Clay Strips | - | Tiras de argila, bom para buildup |
| Inflate | I | Infla a superficie |
| Blob | - | Cria protuberancias arredondadas |
| Layer | L | Adiciona camada uniforme |
| Crease | Shift+C | Cria vincos e dobras |

### Pinceis de Suavizacao
| Pincel | Atalho | Funcao |
|--------|--------|--------|
| Smooth | S (ou Shift durante outro pincel) | Suaviza superficie |
| Flatten | Shift+T | Achata areas |
| Fill | - | Preenche depressoes |
| Scrape | - | Raspa areas elevadas |
| Pinch | - | Puxa vertices para o centro do pincel |

### Pinceis de Detalhe
| Pincel | Atalho | Funcao |
|--------|--------|--------|
| Grab | G | Move a geometria (como puxar argila) |
| Snake Hook | K | Puxa geometria como uma cobra |
| Thumb | - | Empurra geometria na direcao do stroke |
| Nudge | - | Empurra suavemente |
| Rotate | - | Rotaciona area sob o pincel |
| Elastic Deform | - | Deformacao elastica |

### Pinceis Especiais
| Pincel | Funcao |
|--------|--------|
| Mask | Protege areas da edicao |
| Draw Face Sets | Define conjuntos de faces |
| Multires Displacement Eraser | Apaga detalhes de multires |
| Cloth | Simula tecido na escultura |
| Pose | Reposiciona partes do modelo |
| Boundary | Edita bordas |

## Configuracoes dos Pinceis

### Propriedades Principais
- **Radius:** `F` + mover mouse (tamanho do pincel)
- **Strength:** `Shift + F` + mover mouse (intensidade)
- **Direction:** `Ctrl` durante stroke (inverte add/subtract)
- **Smooth Stroke:** suaviza o tracado
- **Stabilize Stroke:** delay para tracos mais precisos

### Simetria
- Ative no header: `X`, `Y`, `Z` (espelha o pincel)
- **Radial:** repete o pincel em padroes radiais
- **Tile:** repete em padroes de ladrilho

## Workflow de Escultura para Impressao 3D

### Etapa 1: Forma Base (Blockout)
1. Comece com formas primitivas simples
2. Use Grab, Move, Scale para posicionar
3. Use Clay/Clay Strips com Strength alto
4. Foque em proporcoes e silhueta
5. Dyntopo com detalhe baixo (8-12px)

### Etapa 2: Formas Secundarias
1. Aumente a resolucao (Remesh ou Dyntopo)
2. Use Draw, Inflate para volumes menores
3. Crease para dobras e vincos
4. Defina musculos, roupas, features
5. Smooth para refinar transicoes

### Etapa 3: Detalhes Finos
1. Resolucao maxima (Remesh com voxel size pequeno)
2. Poros, rugas, escamas, texturas
3. Use Strength baixo e Radius pequeno
4. Layer para detalhes uniformes
5. Draw Sharp para linhas finas

### Etapa 4: Preparacao para Impressao
1. **Remesh final:** uniformizar topologia
2. **Decimate:** reduzir poligonos se necessario (alvo: <500k para peca tipica)
3. **Verificar manifold:** sem buracos
4. **Verificar espessura:** minimo 1-2mm em todas as partes
5. **Adicionar base plana:** para boa adesao na mesa

## Multires (Multi-Resolution)

Alternativa ao Dyntopo para workflow mais controlado:

1. Adicione modifier Multires
2. Subdivide: incrementa niveis
3. Esculpa em diferentes niveis de detalhe
4. Nao precisa aplicar - pode navegar entre niveis
5. Ideal para workflow de retopologia depois

## Mascaras e Face Sets

### Mascaras
- **Pintar mascara:** `M` (pincel de mascara)
- **Inverter mascara:** `Ctrl + I`
- **Limpar mascara:** `Alt + M`
- **Expandir mascara:** `Shift + A`
- **Box Mask:** `B` (mascara retangular)
- **Lasso Mask:** `Shift + Ctrl + Click` (mascara livre)

### Face Sets
Agrupam faces para controle seletivo:
- **Criar:** Draw Face Sets brush
- **Isolar:** `H` (esconde outros)
- **Mostrar tudo:** `Alt + H`
- **Usar para:** esculpir areas especificas, remesh parcial

## Novidades em Sculpt Mode (Blender 4.2 - 4.5)

### Blender 4.2
- Trim tools agora suportam solver Fast e Exact
- Sculpt e Weight Paint usam incremento de rotacao global customizavel
- Line tools com snapping habilitado (ex: Line Hide em Sculpt)

### Blender 4.3
- Nova **Brush Library** para acesso rapido e customizacao de pinceis favoritos
- Pinceis **Inflate** e **Pinch** melhorados para performance e usabilidade
- **Smooth brush** aprimorado com mais controle (suaviza mantendo detalhes)
- **Brush Shelf** para organizacao de pinceis
- **Cloth simulation brushes** aprimorados
- Opcoes expandidas de customizacao de pinceis (falloff, strength, texture mapping)

### Blender 4.4
- Novo tipo de pincel **Plane** com configuracoes customizaveis
- Controle mais preciso sobre tarefas de escultura

## Dicas para Escultura de Miniaturas (Impressao 3D)

1. **Escala:** esculpa em tamanho real (ex: figura de 75mm)
2. **Detalhes minimos:** considere a resolucao da impressora
   - Bambu A1 com nozzle 0.4mm: detalhes >= 0.4mm
   - Para miniaturas, layer height 0.08-0.12mm
3. **Overhangs:** considere angulos de suporte (>45 graus)
4. **Separar pecas:** para pecas complexas, separe em partes
5. **Base solida:** sempre inclua uma base plana
6. **Pontos de encaixe:** adicione pinos para pecas separaveis
