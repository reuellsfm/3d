# Blender - Interface e Workspace para Modelagem 3D

## Versao Recomendada
Blender 4.x (LTS) - Download gratuito em https://www.blender.org

### Versoes Atuais (2025-2026)
- **Blender 4.5 LTS** (Julho 2025) - Suportado ate Julho 2027 - Recomendado
- **Blender 4.2 LTS** (Julho 2024) - Suportado ate Julho 2026
- Blender 4.4 (Marco 2025)
- Blender 4.3 (Novembro 2024)

## Interface Principal

### Areas do Blender
```
+------------------------------------------------------------------+
|  Menu Principal (File, Edit, Render, Window, Help)               |
+------------------------------------------------------------------+
|  Toolbar  |                                    |   Properties     |
|  (T)      |        3D Viewport                 |   Panel (N)      |
|           |                                    |                  |
|  Ferramentas|      Area principal de            |  Transform       |
|  ativas   |      modelagem                     |  Dimensoes       |
|           |                                    |  Item info       |
+------------------------------------------------------------------+
|  Timeline / Outliner / Properties Editor                         |
+------------------------------------------------------------------+
```

### Configuracao Inicial para Modelagem 3D Print

1. **Abrir Blender** > `Edit > Preferences`
2. **Add-ons essenciais para ativar:**
   - `Mesh: 3D-Print Toolbox` (analise de mesh)
   - `Import-Export: STL format`
   - `Import-Export: OBJ format`
   - `Mesh: LoopTools`
   - `Mesh: F2`
   - `Object: Bool Tool`

3. **Configurar unidades:**
   - `Scene Properties > Units`
   - Unit System: **Metric**
   - Length: **Millimeters**
   - Scale: **0.001** (1 Blender unit = 1mm)

### Workspaces Recomendados

#### Workspace "3D Print Modeling"
1. Vá em `+` (adicionar workspace) > `General > Modeling`
2. Configure as areas:
   - **Centro:** 3D Viewport (modo Edit)
   - **Direita:** Properties Editor
   - **Inferior:** Outliner
   - **Lateral:** Tool Settings

#### Viewport Shading Modes
| Modo | Atalho | Uso |
|------|--------|-----|
| Wireframe | Z > 4 | Ver topologia, vertices internos |
| Solid | Z > 6 | Modelagem geral, ver forma |
| Material Preview | Z > 2 | Visualizar materiais/cores |
| Rendered | Z > 8 | Preview final |

### Viewport Navigation

| Acao | Mouse | Teclado |
|------|-------|---------|
| Orbitar | Middle Mouse Button | Numpad 4/6/8/2 |
| Pan | Shift + MMB | Shift + Numpad |
| Zoom | Scroll | Numpad +/- |
| Vista Frontal | - | Numpad 1 |
| Vista Lateral | - | Numpad 3 |
| Vista Topo | - | Numpad 7 |
| Vista Camera | - | Numpad 0 |
| Ortografico/Perspectiva | - | Numpad 5 |
| Focar no selecionado | - | Numpad . |

### Configuracao do Grid

Para modelagem precisa para impressao 3D:
1. `Overlay > Grid` (no header do 3D Viewport)
2. Scale: **0.001** (para milimetros)
3. Subdivisions: **10**
4. Ative `Floor` e os eixos X, Y, Z

### Snap (Alinhamento)

Ferramenta essencial para precisao:
- Ativar: `Shift + Tab` ou icone de ima no header
- Tipos de snap:
  - **Vertex:** encaixa em vertices
  - **Edge:** encaixa em arestas
  - **Face:** encaixa em faces
  - **Grid:** encaixa no grid
  - **Increment:** incrementos regulares

### Pivot Point (Ponto de Pivô)

Menu no header do 3D Viewport (`.` tecla):
- **Median Point:** centro da selecao
- **Individual Origins:** origem de cada elemento
- **3D Cursor:** posicao do cursor 3D
- **Active Element:** elemento ativo
- **Bounding Box Center:** centro da caixa limitante

### Transform Orientation

- **Global:** eixos do mundo (X, Y, Z fixos)
- **Local:** eixos do objeto
- **Normal:** perpendicular a face selecionada
- **View:** relativo a camera/vista atual
- **Cursor:** relativo ao cursor 3D

### Salvando Layout Customizado
1. Configure seu workspace ideal (split editors, resize paineis)
2. Para dividir editores: clique com botao direito na borda > `Vertical Split` ou `Horizontal Split`
3. Arraste a divisao para ajustar proporcoes
4. Salve: `File > Defaults > Save Startup File`
5. O workspace e preservado automaticamente ao fechar o Blender

## Dica para Impressao 3D

Sempre trabalhe em **milimetros**. Ao iniciar um projeto:
1. Delete o cubo padrao
2. Verifique as unidades (mm)
3. Adicione uma referencia de escala (cubo de 20mm por exemplo)
4. Salve como template: `File > Defaults > Save Startup File`

**Aviso importante:** A escala padrao do Blender e 1:1 metro. O cubo padrao tem 2x2x2 metros. Se nao configurar corretamente para mm, os modelos importados no slicer ficarao minusculos (fracao de milimetro) - este e um dos erros mais comuns.
