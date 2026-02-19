# Blender - Medicao e Escala para Impressao 3D

## Configuracao de Unidades

### Unidades Padrao do Blender
- Sistema padrao: Metrico, em **Metros**
- O cubo padrao tem 2x2x2 metros
- Para impressao 3D, metros e grande demais (exceto impressoras industriais)

### Configurar para Milimetros
1. Abra `Scene Properties` (icone de cone no Properties panel)
2. Navegue ate `Units`
3. Configure:
   ```
   Unit System: Metric
   Unit Scale: 0.001
   Length: Millimeters
   ```
4. **Resultado:** 1 Blender unit = 1 milimetro

### Configurar Grid para mm
1. `Viewport Overlays > Grid` (no header do 3D Viewport)
2. Scale: **0.001**
3. Subdivisions: **10**
4. Ative Floor e eixos X, Y, Z
5. Ou: no N-panel (Properties Shelf), Display > Scale: 0.001

### Sistemas de Unidades Disponiveis
| Sistema | Uso |
|---------|-----|
| Metric (m) | Padrao do Blender |
| Metric (mm) | Impressao 3D (recomendado) |
| Metric (cm) | Modelagem arquitetonica |
| Imperial (ft/in) | Impressoras com unidades imperiais |
| None | Sem unidades - nao recomendado |

## Ferramenta Measure (Regua)

### Acesso
- **Toolbar:** Icone de regua na barra lateral esquerda do 3D Viewport
- **Menu:** `Toolbar > Measure`

### Como Usar
1. Clique e arraste no viewport para definir ponto inicial e final da regua
2. A medida aparece sobre a linha no viewport
3. Voce pode adicionar multiplas reguas no viewport
4. Arraste as extremidades para reposicionar

### Atalhos do Measure Tool
| Acao | Atalho |
|------|--------|
| Snap em vertices/edges | Segurar `Ctrl` enquanto arrasta |
| Medir distancia entre faces | Segurar `Shift` enquanto arrasta |
| Converter para transferidor | Clicar no ponto medio da regua |
| Deletar regua | Selecionar e `X` ou `Delete` |

### Comportamento
- Usa as configuracoes de unidade e escala da cena
- Mudar sistema de unidades (metric, imperial) ou unidade de comprimento (cm, m) atualiza as medicoes automaticamente
- Mudar unidade angular (graus, radianos) tambem atualiza

## Medicoes no Viewport (Overlay)

### Ativar Medicao de Edges
1. Acesse `Viewport Overlays` (menu dropdown no header do viewport)
2. Ative **Measurement** (ou Edge Length, Edge Angle, Face Area dependendo da versao)
3. Em Edit Mode, as medicoes dos edges selecionados aparecem automaticamente

### Atencao com Escala
Se voce escalar um objeto, as medicoes podem estar **"erradas"** porque so sao atualizadas apos aplicar a transformacao de escala:
- `Ctrl + A` > `Scale` (aplica a escala)
- Ou `Object > Apply > Scale`
- **Sempre aplique a escala antes de medir ou exportar!**

## N-Panel (Sidebar) - Dimensoes

### Acesso
Pressione `N` no 3D Viewport para abrir o painel lateral.

### Informacoes Disponiveis
```
Item Tab:
- Location: X, Y, Z (posicao do objeto)
- Rotation: X, Y, Z (rotacao)
- Scale: X, Y, Z (deve ser 1.0, 1.0, 1.0 para impressao)
- Dimensions: X, Y, Z (tamanho real do objeto em unidades da cena)
```

### Dimensoes vs Scale
- **Dimensions:** mostra o tamanho real (ex: 50mm x 30mm x 20mm)
- **Scale:** mostra o fator de escala (deve ser 1.0 para exportacao correta)
- Se Scale != 1.0, aplique com `Ctrl + A > Scale`

## Measure and Scale Add-on

### Ativacao
`Edit > Preferences > Add-ons > buscar "Measure and Scale"`

### Localizacao
`3D Viewport > Sidebar (N-Panel) > Item Tab > Measure and Scale`

### Funcionalidades
- Medir distancia entre dois pontos selecionando vertices
- Medidas em tempo real enquanto seleciona
- Suporte para unidades Metricas (m, cm, mm) e Imperiais (ft, in)
- Customizacao visual (cor, tamanho da fonte, unidades)
- Configuracoes de medicao multipla com pontos vinculados

### Como Medir entre Dois Pontos
1. Entre em Edit Mode
2. Selecione o vertice inicial
3. Shift+Click no vertice final
4. A medida aparece no painel

## 3D Print Toolbox - Medicao

### Volume e Area
Com o 3D Print Toolbox ativado (`N-Panel > 3D-Print`):
- **Volume:** Clique no botao para calcular o volume do mesh selecionado
- **Area:** Clique no botao para calcular a area da superficie

### Scale To (Escalar Para)
Ferramentas de escala direta no 3D Print Toolbox:
- **Volume:** Escala o mesh para um volume especifico exato
- **Bounds:** Escala o maior eixo para corresponder ao valor dado

## Dicas de Escala para Impressao 3D

### Workflow Recomendado
1. **Antes de modelar:** Configure unidades para mm (Unit Scale: 0.001)
2. **Durante modelagem:** Verifique dimensoes regularmente (N-panel)
3. **Antes de exportar:**
   - Aplique todas as transformacoes: `Ctrl + A > All Transforms`
   - Verifique que Scale = 1.0, 1.0, 1.0
   - Confira Dimensions no N-panel
4. **No export STL:** Marque "Scene Unit" para gravar unidades no arquivo

### Problemas Comuns de Escala
| Problema | Causa | Solucao |
|----------|-------|---------|
| Modelo minusculo no slicer | Modelou em metros, slicer le em mm | Unit Scale 0.001 ou scale x1000 no export |
| Modelo gigante no slicer | Unit Scale incorreto | Verificar unidades e aplicar escala |
| Dimensoes inconsistentes | Scale != 1.0 | `Ctrl + A > Scale` |
| Medidas erradas no viewport | Escala nao aplicada | `Ctrl + A > Scale` antes de medir |

### Fator de Conversao
```
175 mm = 17.5 cm = 0.175 m

Se trabalhando em metros (padrao):
- 0.175 m no Blender = 0.175 mm no slicer (errado!)
- Solucao: multiplicar por 1000 no export
- Ou: configurar Unit Scale para 0.001 desde o inicio
```
