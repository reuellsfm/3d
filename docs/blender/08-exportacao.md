# Blender - Exportacao para Impressao 3D

## Formatos de Arquivo

### STL (STereoLithography)
O formato mais universal para impressao 3D.

**Caracteristicas:**
- Suporta apenas geometria (sem cores, texturas ou materiais)
- Formato binario (menor) ou ASCII (legivel)
- Amplamente suportado por todos os slicers
- Nao preserva informacao de escala (depende das unidades)

**Exportar STL:**
1. `File > Export > STL (.stl)`
2. Configuracoes recomendadas (painel lateral esquerdo):
   ```
   Selection Only: ON (exporta apenas selecionado - evita geometria extra)
   Scene Unit: ON (grava unidades no arquivo STL)
   Apply Modifiers: ON (aplica modifiers no export sem alterar original)
   Format: Binary (menor, mais rapido - ASCII apenas para debug)
   Forward: Y Forward (padrao Blender)
   Up: Z Up (padrao Blender - maioria dos slicers usa Z Up)
   Scale: 1.0 (se unidades ja estao corretas)
   ```

**Nota sobre Apply Modifiers:** Exporta objetos usando o "evaluated mesh" - o resultado apos todos os Modifiers terem sido calculados. Permite manter Sub-division e Boolean "nao-aplicados" no Blender mas aplicados no STL exportado.

**Comportamento de unidades na importacao:**
- Se unidades NAO foram gravadas no STL: Blender assume metros
- Se unidades estao no STL mas Blender esta em "None": assume metros
- **Sempre ative Scene Unit no export para evitar confusao!**

**Conversao de eixos:**
Blender usa Y Forward, Z Up. Se o software destino usa Y como eixo Up, configure: `-Z Forward, Y Up`.

### OBJ (Wavefront)
**Caracteristicas:**
- Suporta geometria + materiais basicos + UV maps
- Pode incluir informacao de cor por vertice
- Dois arquivos: .obj (geometria) + .mtl (materiais)
- Bom para modelos pintados e impressoras full-color
- Tecnicamente mais preciso que STL (mais dados geometricos)
- Arquivos maiores e mais complexos que STL

**Exportar OBJ:**
1. `File > Export > Wavefront (.obj)`
2. Configuracoes:
   ```
   Selection Only: ON
   Apply Modifiers: ON
   Write Materials: ON (se usar cores/materiais)
   Include: Mesh (desativar Animation, etc.)
   Scale: 1.0
   Forward: -Y Forward
   Up: Z Up
   ```

**OBJ vs STL para impressao:**
OBJ e teoricamente mais preciso, mas STL e a melhor escolha para iniciantes por simplicidade. Quanto mais dados no formato, mais dados precisam ser decodificados pelo slicer - STL e simples e confiavel.

### 3MF (3D Manufacturing Format)
**O formato RECOMENDADO para Bambu Studio e impressao moderna.**

**Caracteristicas:**
- Formato moderno desenvolvido pela Microsoft, adotado por fabricantes
- Substituto inteligente do STL - formato de troca end-to-end (design -> slicer)
- Suporta cores, materiais, texturas e estruturas complexas
- Inclui informacao de escala (unidades embutidas) - sem problemas de conversao
- Suporta multiplos objetos/partes em um arquivo
- Compressao nativa (**arquivo MENOR que STL** apesar de mais informacao)
- Suporta 3MF Core Specification v1.2.3
- Suportado nativamente pelo Bambu Studio

**Exportar 3MF do Blender (via Add-on):**
Add-on: "Blender 3MF Format" (Ghostkeeper) - GitHub community add-on

Opcoes de exportacao:
```
use_selection: False (default) - Apenas exportar objetos selecionados
global_scale: 1 (default) - Fator de escala a partir da origem
use_mesh_modifiers: True (default) - Aplicar modifiers antes de exportar
coordinate_precision: 4 (default) - Casas decimais para coordenadas
                     (maior precisao = arquivo maior)
```

**Alternativas para obter 3MF:**
1. Exportar STL/OBJ do Blender e importar no Bambu Studio (converte automaticamente)
2. Instalar add-on "Blender 3MF Format" para export nativo
3. Usar Bambu Studio para salvar como 3MF

**Nota:** Eventualmente esperamos que 3MF seja integrado permanentemente no Blender. Por enquanto, STL continua como opcao mais segura e simples para iniciantes.

### Comparacao de Formatos

| Caracteristica | STL | OBJ | 3MF |
|----------------|-----|-----|-----|
| Geometria | Sim | Sim | Sim |
| Cores | Nao | Sim | Sim |
| Texturas | Nao | Sim | Sim |
| Escala/Unidades | Nao | Parcial | Sim |
| Multi-objeto | Nao | Sim | Sim |
| Tamanho arquivo | Grande | Grande | Pequeno |
| Bambu Studio | Sim | Sim | Nativo |

## Workflow de Exportacao Completo

### Passo 1: Preparar o Modelo
```
1. Aplicar todos os modifiers (Ctrl+A no modifier)
2. Aplicar escala (Ctrl+A > Scale)
3. Verificar dimensoes (N > Item > Dimensions)
4. Verificar unidades (Scene > Units > Millimeters)
```

### Passo 2: Verificar Mesh
```
1. Edit Mode > Select > All by Trait > Non Manifold
   (deve selecionar ZERO elementos)
2. Overlay > Face Orientation
   (tudo deve ser AZUL, nada vermelho)
3. 3D-Print Toolbox > Check All
   (resolver todos os problemas)
```

### Passo 3: Limpar Mesh
```
1. Edit Mode > A (selecionar tudo)
2. Mesh > Merge by Distance (threshold: 0.001)
3. Mesh > Clean Up > Degenerate Dissolve
4. Mesh > Clean Up > Delete Loose
5. Mesh > Normals > Recalculate Outside (Shift+N)
```

### Passo 4: Posicionar para Impressao
```
1. Origin na base: Object > Set Origin > Origin to 3D Cursor
   (com cursor em Z=0 da base do objeto)
2. Posicionar no Z=0: Alt+G (resetar posicao)
3. Centralizar: Shift+S > Cursor to World Origin, depois
   Object > Snap > Selection to Cursor
```

### Passo 5: Exportar
```
1. Selecionar objeto(s)
2. File > Export > STL (ou OBJ)
3. Configurar: Selection Only, Scene Unit, Apply Modifiers
4. Escolher local e nome
5. Exportar
```

### Passo 6: Verificar no Slicer
```
1. Abrir Bambu Studio
2. Importar o arquivo exportado
3. Verificar escala (modelo deve estar no tamanho correto)
4. Verificar se nao ha erros de mesh (Bambu Studio notifica)
5. Se houver erros, usar "Repair" do Bambu Studio ou voltar ao Blender
```

## Exportacao Multi-Cor (para AMS Lite)

### Metodo 1: Objetos Separados
1. No Blender, separe cada cor em um objeto diferente
2. Exporte cada objeto como STL separado
3. No Bambu Studio, importe todos os STL
4. Atribua cada objeto a um filamento diferente

### Metodo 2: Vertex Paint + OBJ
1. No Blender, pinte o modelo com Vertex Paint
2. Exporte como OBJ (preserva cores)
3. Importe no Bambu Studio
4. Use "Paint" para ajustar areas de cor

### Metodo 3: Multi-Material no Blender
1. Crie material slots diferentes para cada cor
2. Atribua faces a cada material
3. Exporte como OBJ com materiais
4. Bambu Studio reconhece os materiais como filamentos diferentes

## Scripts Python Uteis para Exportacao

### Exportar Todos os Objetos Selecionados como STL Individual
```python
import bpy
import os

export_path = "/caminho/para/exportacao/"

for obj in bpy.context.selected_objects:
    # Selecionar apenas este objeto
    bpy.ops.object.select_all(action='DESELECT')
    obj.select_set(True)
    bpy.context.view_layer.objects.active = obj

    # Aplicar modifiers
    for mod in obj.modifiers:
        bpy.ops.object.modifier_apply(modifier=mod.name)

    # Exportar
    filepath = os.path.join(export_path, f"{obj.name}.stl")
    bpy.ops.export_mesh.stl(
        filepath=filepath,
        use_selection=True,
        use_scene_unit=True,
        ascii=False
    )
    print(f"Exportado: {filepath}")
```

### Verificar e Exportar com Relatorio
```python
import bpy
import bmesh

obj = bpy.context.active_object
bpy.ops.object.mode_set(mode='EDIT')
bm = bmesh.from_edit_mesh(obj.data)

# Verificacoes
non_manifold = [e for e in bm.edges if not e.is_manifold]
loose_verts = [v for v in bm.verts if not v.link_edges]
loose_edges = [e for e in bm.edges if not e.link_faces]

print(f"=== Relatorio de Mesh: {obj.name} ===")
print(f"Vertices: {len(bm.verts)}")
print(f"Edges: {len(bm.edges)}")
print(f"Faces: {len(bm.faces)}")
print(f"Non-manifold edges: {len(non_manifold)}")
print(f"Loose vertices: {len(loose_verts)}")
print(f"Loose edges: {len(loose_edges)}")
print(f"Dimensions: {obj.dimensions}")
print(f"Volume: {bm.calc_volume():.2f} mm3")

if non_manifold or loose_verts or loose_edges:
    print("AVISO: Mesh tem problemas! Corrija antes de exportar.")
else:
    print("OK: Mesh esta limpo para exportacao.")

bpy.ops.object.mode_set(mode='OBJECT')
```

## Avisos Importantes Pre-Exportacao

### Smooth Shading vs Geometria Real
- **Smooth Shading** pode enganar voce - faz o modelo parecer mais suave do que a geometria real
- Smooth Shading e otimo para rendering/visualizacao digital mas NAO afeta a impressao 3D
- Para output fisico, o que importa e a geometria real (vertices/faces)
- Se precisa de modelo mais suave para impressao, adicione Subdivision Surface modifier

### Combinar Objetos Sobrepostos
- Antes de exportar, combine objetos sobrepostos com Boolean Union (Exact solver)
- Isso garante que a peca sera um solido unico, nao meshes sobrepostos
- Meshes sobrepostos podem causar problemas no slicer

### Reduzir Geometria se Necessario
- Use Decimate modifier para reduzir poligonos sem perder forma significativa
- Objetivo: manter detalhes importantes enquanto reduz tamanho do arquivo
- Mesh muito denso (>1M faces) pode ser lento no slicer

## Dicas Especificas para Bambu Studio

1. **Tamanho do arquivo:** STL binario e menor que ASCII; prefira binario
2. **Resolucao:** Para a A1, mesh com 100k-500k faces e ideal
3. **Multi-part:** Use 3MF para projetos com multiplas pecas
4. **Orientacao:** Bambu Studio pode rotacionar, mas exporte ja na orientacao de impressao
5. **Escala:** Se usar STL, verifique a escala ao importar no Bambu Studio (deve estar em mm)
6. **Diferenca FDM vs Resina:**
   - FDM (como Bambu A1): arredonda cantos, suaviza detalhes finos
   - Resina: mantem detalhes finos mas paredes finas podem quebrar
