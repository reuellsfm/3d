# Problemas de Modelagem no Blender - Troubleshooting

## 1. Mesh Nao-Manifold

### Sintomas
- 3D-Print Toolbox reporta "Non Solid"
- Slicer mostra buracos ou areas transparentes
- Modelo imprime com paredes faltando

### Diagnostico
```
Edit Mode > Select > All by Trait > Non Manifold
Elementos selecionados = problemas
```

### Causas e Solucoes

| Causa | Solucao |
|-------|---------|
| Buracos no mesh | Selecionar bordas > F (fill) |
| Faces internas | Delete faces internas (X > Faces) |
| Edges soltos | Delete edges soltos (Mesh > Clean Up > Delete Loose) |
| Vertices duplicados | Mesh > Merge by Distance (threshold 0.001) |
| Normais invertidas | Shift+N (Recalculate Outside) |
| Objetos sobrepostos | Boolean Union para fundir |
| T-vertices | Merge ou dissolve vertices extras |

### Correcao Rapida
```
1. Select All (A)
2. Mesh > Clean Up > Merge by Distance (0.001mm)
3. Mesh > Clean Up > Degenerate Dissolve
4. Mesh > Clean Up > Delete Loose
5. Mesh > Normals > Recalculate Outside (Shift+N)
6. 3D-Print Toolbox > Make Manifold (ultimo recurso)
```

---

## 2. Normais Invertidas

### Sintomas
- Face Orientation overlay mostra vermelho
- Modelo imprime com paredes de dentro para fora
- Partes do modelo transparentes no slicer

### Solucao
```
1. Overlay > Face Orientation (ativar)
2. Edit Mode > A (selecionar tudo)
3. Shift+N (Recalculate Outside)
4. Se faces individuais persistem:
   Selecionar face > Mesh > Normals > Flip
```

---

## 3. Modelo Sem Espessura

### Sintomas
- Modelo e uma superficie sem volume
- Slicer nao gera G-code ou gera muito fino
- Paredes impressas translucidas ou quebradicas

### Solucao
```
Adicionar Solidify modifier:
  Thickness: 1.0-2.0mm (para parede funcional)
  Offset: -1 (para dentro) ou 1 (para fora)
  Even Thickness: ON
  Fill Rim: ON
  Aplicar modifier antes de exportar
```

---

## 4. Escala Errada

### Sintomas
- Modelo minusculo no slicer (fracao de mm)
- Modelo gigante no slicer (metros)
- Dimensoes nao correspondem ao projetado

### Diagnostico
```
Verificar: N > Item > Dimensions
Verificar: Scene Properties > Units
Verificar: N > Item > Scale (deve ser 1,1,1)
```

### Solucoes
```
Se escala nao e (1,1,1):
  Ctrl+A > Scale (aplica escala)

Se unidades erradas:
  Scene > Units > Metric > Millimeters > Scale 0.001

Se modelo importado em escala errada:
  S > valor > Enter
  Exemplo: S > 1000 > Enter (se estava em metros)
  Depois: Ctrl+A > Scale
```

---

## 5. Boolean Falha

### Sintomas
- Boolean nao funciona
- Resultado com buracos ou artefatos
- Faces estranhas no resultado

### Solucoes
```
1. Usar solver Exact (mais preciso)
2. Garantir que ambos objetos sao manifold
3. Aplicar Ctrl+A > All Transforms nos dois objetos
4. Verificar se objetos se sobrepõem adequadamente
5. Aumentar overlap em 0.01mm se estao tangentes
6. Se falhar: Voxel Remesh do resultado (cleanup)
7. Verificar escala (objetos muito pequenos podem falhar)
```

---

## 6. Poligonos Excessivos

### Sintomas
- Blender fica lento
- Slicer trava ou demora muito
- Arquivo STL muito grande (>100MB)

### Solucoes
```
Decimate modifier:
  Ratio: 0.5 (reduz pela metade)
  Repetir ate atingir polycount alvo

Remesh > Voxel:
  Voxel Size: 0.5-1.0mm
  Reconstroi mesh uniforme

Polycount alvo para impressao:
  Peca pequena (< 50mm): 50k-200k faces
  Peca media (50-150mm): 100k-500k faces
  Peca grande (> 150mm): 200k-1M faces
  Maximo recomendado: 1M faces
```

---

## 7. Geometria Auto-Intersectante

### Sintomas
- 3D-Print Toolbox reporta "Intersections"
- Partes do modelo se cruzam internamente
- Impressao com artefatos internos

### Solucoes
```
1. Boolean Union para fundir meshes sobrepostos
2. Voxel Remesh (reconstroi mesh limpo)
3. Edit Mode > manualmente remover faces internas
4. Select > All by Trait > Interior Faces > Delete
```

---

## 8. Overhangs Excessivos

### Sintomas no Design
- 3D-Print Toolbox > Overhang mostra muitas faces
- Modelo precisa de suporte excessivo

### Solucoes de Design
```
1. Rotacionar o modelo para reduzir overhangs
2. Adicionar chanfros de 45 graus em saliencias
3. Redesenhar para auto-suportar (rule of 45)
4. Separar em partes e montar depois
5. Adicionar nervuras de suporte no proprio modelo
6. Usar Tear-drop shape para furos horizontais
   (circulo com ponta em V no topo = nao precisa suporte)
```

---

## 9. Detalhes Pequenos Demais

### Diagnostico
```
Verificar se detalhes sao >= diametro do nozzle:
  Nozzle 0.4mm: detalhe minimo 0.4mm
  Nozzle 0.2mm: detalhe minimo 0.2mm

Detalhes menores serao ignorados pelo slicer ou
ficarao indefidos na impressao.
```

### Solucoes
```
1. Aumentar escala do modelo (se possivel)
2. Usar nozzle menor (0.2mm para miniaturas)
3. Engrossar detalhes finos (min 0.5mm com 0.4mm nozzle)
4. Exagerar profundidade de gravacoes (+50%)
5. Usar layer height mais fino para detalhes em Z
```

---

## 10. Paredes Finas Invisíveis no Slicer

### Causa
Parede mais fina que o nozzle e ignorada pelo slicer.

### Solucao
```
1. No Blender: engrossar parede para >= 0.4mm
   (ou >= largura do nozzle)
2. No slicer: ativar "Detect Thin Walls"
3. Usar Arachne wall generator (adapta largura)
4. Solidify modifier com espessura adequada
```
