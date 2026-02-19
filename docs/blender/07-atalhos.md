# Blender - Atalhos Essenciais para Modelagem 3D

## Mudancas de Keymap no Blender 4.0+

### Principais Alteracoes
- **1, 2, 3:** Alterna modos de selecao/mascara para o modo atual. Se em Object Mode, muda primeiro para Edit Mode (antes sempre mudava para Edit Mode)
- **5:** Menu pie de troca de modo (antes 5-7 eram modos individuais)
- **~ (til):** Transfer Mode - troca de objeto mantendo o modo atual (novo mapeamento)
- Mudancas afetam principalmente sculpting, painting e grease pencil

## Atalhos Globais

### Arquivo e Sistema
| Atalho | Acao |
|--------|------|
| Ctrl + N | Novo arquivo |
| Ctrl + O | Abrir arquivo |
| Ctrl + S | Salvar |
| Ctrl + Shift + S | Salvar como |
| Ctrl + Z | Desfazer |
| Ctrl + Shift + Z | Refazer |
| Ctrl + Q | Fechar Blender |
| F1 | Help |
| F2 | Renomear item ativo |
| F3 | Buscar comandos (Search) |
| F4 | File Context Menu |
| F9 | Ajustar ultima operacao |
| F11 | Mostrar render |
| F12 | Renderizar |

### Selecao
| Atalho | Acao |
|--------|------|
| Click esquerdo | Selecionar |
| Shift + Click | Adicionar/remover da selecao |
| A | Selecionar tudo |
| Alt + A | Deselecionar tudo |
| Ctrl + I | Inverter selecao |
| B | Box select (retangulo) |
| C | Circle select (circulo) |
| Ctrl + Click | Lasso select |
| L (hover) | Selecionar linked (sob cursor) |
| Ctrl + L | Selecionar linked (a partir da selecao) |
| Ctrl + Numpad + | Expandir selecao |
| Ctrl + Numpad - | Reduzir selecao |

### Viewport
| Atalho | Acao |
|--------|------|
| Numpad 1 | Vista frontal |
| Numpad 3 | Vista lateral direita |
| Numpad 7 | Vista topo |
| Ctrl + Numpad 1 | Vista traseira |
| Ctrl + Numpad 3 | Vista lateral esquerda |
| Ctrl + Numpad 7 | Vista de baixo |
| Numpad 5 | Ortografico/Perspectiva |
| Numpad 0 | Vista camera |
| Numpad . | Focar no selecionado |
| Home | Ver tudo |
| Z | Menu pie de shading |
| Alt + Z | Toggle X-Ray |
| Shift + Z | Toggle wireframe |

### Transformacao
| Atalho | Acao |
|--------|------|
| G | Mover (Grab) |
| R | Rotacionar |
| S | Escalar |
| G/R/S + X/Y/Z | Restringir a eixo |
| G/R/S + Shift + X/Y/Z | Excluir eixo |
| G/R/S + numero + Enter | Valor exato |
| Alt + G | Resetar posicao |
| Alt + R | Resetar rotacao |
| Alt + S | Resetar escala |
| Ctrl + A | Aplicar transformacao |

## Object Mode

### Objetos
| Atalho | Acao |
|--------|------|
| Shift + A | Adicionar objeto |
| X ou Delete | Deletar |
| Ctrl + C | Copiar |
| Ctrl + V | Colar |
| Shift + D | Duplicar |
| Alt + D | Duplicar linked (instancia) |
| M | Mover para colecao |
| H | Esconder selecionado |
| Alt + H | Mostrar tudo |
| Ctrl + J | Juntar objetos |
| P | Separar objetos |
| Ctrl + P | Parent (criar pai) |
| Alt + P | Clear parent |

### Snap e Alinhamento
| Atalho | Acao |
|--------|------|
| Shift + Tab | Toggle snap |
| Shift + Ctrl + Tab | Menu snap |
| Shift + S | Menu snap cursor/selecao |
| Shift + C | Cursor para origem |

## Edit Mode

### Navegacao
| Atalho | Acao |
|--------|------|
| Tab | Toggle Object/Edit Mode |
| 1 | Modo vertex |
| 2 | Modo edge |
| 3 | Modo face |
| Ctrl + Tab | Menu modos |

### Selecao Edit Mode
| Atalho | Acao |
|--------|------|
| Alt + Click | Select loop |
| Ctrl + Alt + Click | Select ring |
| Ctrl + Shift + Click | Shortest path select |
| Shift + G | Select similar |
| Ctrl + Numpad + | Select more |
| Ctrl + Numpad - | Select less |

### Modelagem
| Atalho | Acao |
|--------|------|
| E | Extrude |
| I | Inset faces |
| Ctrl + B | Bevel edges |
| Ctrl + Shift + B | Bevel vertices |
| Ctrl + R | Loop cut |
| K | Knife tool |
| J | Connect vertices |
| F | Make face/edge |
| M | Merge vertices |
| V | Rip (rasgar) |
| Alt + M | Merge menu |
| Ctrl + F | Face menu |
| Ctrl + E | Edge menu |
| Ctrl + V | Vertex menu |
| Y | Split (separar) |
| P | Separate selection |

### Mesh
| Atalho | Acao |
|--------|------|
| Shift + N | Recalcular normais |
| Ctrl + T | Triangulate faces |
| Alt + J | Tris to quads |
| Ctrl + Shift + Alt + F | Select non-manifold |
| Shift + Space | Toolbar |

### Proporional Editing
| Atalho | Acao |
|--------|------|
| O | Toggle proportional editing |
| Shift + O | Cycle proportional type |
| Scroll (durante transform) | Ajustar raio |

## Sculpt Mode

### Pinceis
| Atalho | Acao |
|--------|------|
| X | Draw |
| S | Smooth |
| C | Clay |
| G | Grab |
| I | Inflate |
| L | Layer |
| Shift + C | Crease |
| K | Snake Hook |
| Shift + T | Flatten |

### Controles do Pincel
| Atalho | Acao |
|--------|------|
| F | Ajustar raio |
| Shift + F | Ajustar strength |
| Ctrl | Inverter direcao (add/subtract) |
| Shift (durante stroke) | Smooth |

### Mascaras Sculpt
| Atalho | Acao |
|--------|------|
| M | Mask brush |
| Ctrl + I | Inverter mascara |
| Alt + M | Limpar mascara |
| H | Hide unmasked |
| Shift + H | Hide masked |
| Alt + H | Show all |

## Dicas de Produtividade

### Busca Rapida
- **F3:** Busca qualquer comando pelo nome
- Exemplo: F3 > "mirror" > Mirror Modifier

### Favoritos
- **Q:** Menu de favoritos rapidos
- Adicione seus comandos mais usados

### Pie Menus
- **Z:** Shading pie
- **Ctrl + Tab:** Mode pie
- **.** (ponto): Pivot pie
- **,** (virgula): Orientation pie

### Last Operation
- **F9:** Ajusta parametros da ultima operacao
- Funciona para quase todas as operacoes

### Repetir
- **Shift + R:** Repete a ultima operacao
- Muito util com Extrude, Loop Cut, etc.

### Edge Slide
- **G + G:** Ativa Edge Slide (deslizar vertices ao longo de edges)
- **C** (durante Edge Slide): Toggle Clamping (permite ir alem dos limites)

### Outros Atalhos Uteis para Modelagem
| Atalho | Acao |
|--------|------|
| Shift + E | Ajustar crease (para Subdivision Surface) |
| Alt + Click | Selecionar edge loop |
| Ctrl + Alt + Click | Selecionar edge ring |
| Numpad / | Toggle Local View (isola objeto selecionado) |
| Ctrl + B (viewport) | Bevel edges |
| G > G | Edge Slide |
| Shift + Space | Menu de ferramentas |
| N | Toggle painel lateral (sidebar) |
| T | Toggle toolbar |

### Atalhos do Measure Tool
| Atalho | Acao |
|--------|------|
| Ctrl (durante arraste) | Snap em vertices/edges |
| Shift (durante arraste) | Medir distancia entre faces |
| Click no ponto medio | Converter regua em transferidor |

### Atalhos de UV Unwrapping (Edit Mode)
| Atalho | Acao |
|--------|------|
| U | Menu de UV Mapping/Unwrap |
| Ctrl + E > Mark Seam | Marcar seam para UV |
| Ctrl + E > Clear Seam | Limpar seam |
