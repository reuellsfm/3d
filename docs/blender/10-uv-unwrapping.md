# Blender - UV Unwrapping Basico

## O que e UV Unwrapping?

UV Unwrapping e o processo de desdobrar um modelo 3D em uma representacao 2D plana, como desmontar uma caixa de papelao. Isso permite aplicar texturas 2D (imagens) sobre superficies 3D sem distorcao.

### Analogia
Imagine um globo terrestre (3D) sendo "achatado" para virar um mapa-mundi (2D). As "costuras" onde voce corta sao as **seams** (costuras) no Blender.

### Eixos UV
- **U:** eixo horizontal na textura 2D (equivalente ao X)
- **V:** eixo vertical na textura 2D (equivalente ao Y)

## Quando UV Unwrapping e Necessario

### Para Impressao 3D
- **Na maioria dos casos, NAO e necessario** para impressao FDM basica (monocromatica)
- **E necessario quando:**
  - Impressao multi-cor com mapeamento de textura
  - Impressao full-color (impressoras a jato de tinta 3D)
  - Exportacao OBJ/3MF com informacao de textura
  - Aplicar decals ou logos em modelos

### Para Visualizacao/Rendering
- Sempre necessario quando usa texturas de imagem
- Necessario para baking de texturas

## Acesso ao UV Editor

### Abrir UV Editor
1. Divida uma area do viewport
2. Mude o editor para **UV Editor** (dropdown no canto superior esquerdo)
3. Ou use o workspace **UV Editing** (tab no topo)

### Workflow Basico
O processo de unwrapping e feito em **Edit Mode** no 3D Viewport, e cria UV Islands no UV Editor.

## Conceitos Fundamentais

### Seams (Costuras)
Arestas marcadas manualmente que indicam onde o Blender deve "cortar" o mesh para desdobra-lo em 2D.

**Marcar Seam:**
1. Em Edit Mode, selecione edges
2. `Ctrl + E` > `Mark Seam` (a aresta fica vermelha)
3. Ou: `Edge Menu > Mark Seam`

**Limpar Seam:**
- Selecione edges > `Ctrl + E` > `Clear Seam`

**Dica:** Coloque seams em areas pouco visiveis (costas, parte inferior, dobras naturais).

### UV Islands
Cada pedaco separado do mesh desdobrado e uma "UV Island". Seams definem onde as islands se separam.

### Texel Density
A quantidade de detalhe de textura (pixels) por unidade de superficie do modelo 3D. Texel density consistente garante que texturas aparecam na mesma resolucao em todo o modelo.

## Metodos de Unwrapping

### Acesso
Em Edit Mode, selecione faces e pressione `U` para abrir o menu UV Mapping.

### 1. Unwrap (Padrao - Angle Based)
```
Uso: O metodo mais comum e recomendado
Passo a passo:
1. Marque seams nas arestas apropriadas
2. Selecione todas as faces: A
3. Pressione U > Unwrap
4. Resultado aparece no UV Editor
```
- Metodo baseado em angulos (ABF - Angle Based Flattening)
- Requer seams bem posicionadas
- Melhor resultado geral com menos distorcao

### 2. Smart UV Project
```
Uso: Unwrap automatico rapido
Passo a passo:
1. Selecione todas as faces: A
2. U > Smart UV Project
3. Ajuste Angle Limit (padrao: 66 graus)
4. Ajuste Island Margin
```
- NAO requer seams manuais
- Analisa a geometria e cria seams automaticamente
- Bom para prototipagem rapida
- Pode criar muitas islands pequenas

### 3. Project from View
```
Uso: Projetar UV baseado na vista atual do viewport
- U > Project from View
- Util para decals planos e labels
```

### 4. Cube Projection
```
Uso: Projeta nas 6 faces de um cubo
- Bom para objetos cubicos ou arquitetonicos
```

### 5. Cylinder Projection
```
Uso: Projeta como cilindro
- Bom para garrafas, canos, pernas
```

### 6. Sphere Projection
```
Uso: Projeta como esfera
- Bom para esferas, cabecas, planetas
```

### 7. Lightmap Pack
```
Uso: Empacota UVs para lightmaps
- Otimizado para uso eficiente de espaco
```

## Workflow Passo a Passo

### Unwrap Basico de um Objeto
1. Selecione o objeto e entre em Edit Mode (`Tab`)
2. Ative o modo Edge (`2`)
3. Selecione edges onde quer as costuras (pense em onde "cortaria" o objeto para planificar)
4. `Ctrl + E` > `Mark Seam` (edges ficam vermelhos)
5. Mude para modo Face (`3`)
6. Selecione todas as faces (`A`)
7. Pressione `U` > `Unwrap`
8. Visualize o resultado no UV Editor
9. Ajuste se necessario

### Dicas de Posicionamento de Seams
- **Menos seams** = islands maiores com potencial distorcao
- **Mais seams** = islands menores com menos distorcao
- **Regra geral:** Mais seams e melhor do que menos (reduz distorcao de area e angulo)
- Coloque seams em:
  - Bordas naturais do objeto (costas, dobras)
  - Areas nao visiveis na posicao final
  - Cantos vivos (mais facil de esconder a costura)

## Funcionalidades Avancadas

### Live Unwrap
- Ative no UV Editor: `UV > Live Unwrap`
- Pin vertices UV (`P` no UV Editor) e mova-os
- Tudo que nao esta pinned sera recalculado em tempo real
- Economiza muito tempo para ajustes finos

### Pinning
- No UV Editor, selecione vertices UV
- `P` para pin (fixa a posicao)
- `Alt + P` para unpin
- Vertices pinados nao se movem durante o unwrap

### Stretching Display
- No UV Editor: `Overlays > Display Stretch`
- Azul = sem distorcao
- Verde/Amarelo = distorcao media
- Vermelho = distorcao alta
- Use para identificar areas problematicas

### Pack Islands
- Apos unwrap, otimize o uso do espaco UV:
- UV Editor > `UV > Pack Islands`
- Ou `Ctrl + P` no UV Editor

## Verificar Qualidade do UV

### Texture de Teste
1. Crie uma nova imagem no UV Editor: `Image > New`
2. Escolha "UV Grid" ou "Color Grid"
3. Aplique ao material do objeto
4. Verifique no viewport se o grid esta uniforme (sem distorcao)

### Indicadores de Problemas
| Indicador | Problema | Solucao |
|-----------|----------|---------|
| Quadrados esticados | UV distorcido | Adicionar mais seams |
| Quadrados comprimidos | UV comprimido | Reposicionar seams |
| Tamanhos diferentes | Texel density inconsistente | Pack Islands + Average Islands |

## UV para Impressao 3D Multi-Cor

### Workflow Basico
1. Modele o objeto normalmente
2. Faca UV Unwrap completo
3. No UV Editor, pinte a textura com as cores desejadas
4. Exporte como OBJ (preserva UVs e texturas) ou 3MF
5. Importe no slicer que suporta impressao multi-cor

### Dica
Para impressao multi-cor simples (areas de cor solida), e mais facil usar **materiais separados** atribuidos a faces do que UV unwrapping. Reserve UV para texturas complexas/detalhadas.
