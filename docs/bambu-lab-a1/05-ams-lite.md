# AMS Lite - Impressao Multicolorida na Bambu Lab A1

## Visao Geral

O AMS Lite (Automatic Material System Lite) e o sistema de troca automatica de filamento
da Bambu Lab, projetado especificamente para as impressoras da serie A1. Permite impressao
multicolorida com ate 4 cores em uma unica impressao.

---

## Especificacoes do AMS Lite

| Parametro | Valor |
|---|---|
| **Numero de slots** | 4 |
| **Cores maximas por impressao** | 4 |
| **Quantidade de AMS Lite por A1** | 1 (maximo) |
| **Largura de bobina suportada** | 40 - 68 mm |
| **Diametro interno da bobina** | 53 - 58 mm |
| **Deteccao RFID** | Sim (automatica para filamentos Bambu Lab) |
| **Compatibilidade** | Apenas serie A1 (NAO compativel com X1, P1) |

### Acesso Expandido via AMS HUB
- Com o acessorio **AMS HUB (SA013)**, a A1 pode ser conectada ao AMS, AMS 2 Pro, ou AMS HT
- Isso amplia as opcoes de materiais acessiveis

---

## Filamentos Compativeis com AMS Lite

### Compativeis (funcionam bem)

| Material | Nota |
|---|---|
| **PLA** | Ideal |
| **PLA+** | Ideal |
| **PETG** | Bom |
| **ABS** | Sim (mas limitado na A1 open-frame) |
| **ASA** | Sim (mas limitado na A1 open-frame) |
| **PLA Silk** | Bom |
| **PLA Matte** | Bom |

### NAO Compativeis com AMS Lite

| Material | Razao | Solucao |
|---|---|---|
| **TPU/TPE** | Material flexivel emaranha | Alimentar direto do suporte externo |
| **PVA** | Material absorve umidade e incha | Alimentar direto do suporte externo |
| **PA-CF/GF** | Material duro/fragil danifica engrenagens | Alimentar direto do suporte externo |
| **PET-CF/GF** | Material duro/fragil | Alimentar direto do suporte externo |
| **PLA-CF/GF** | Material duro/fragil | Alimentar direto do suporte externo |

---

## Configuracao e Carregamento

### Instalacao Fisica
1. Montar o AMS Lite no suporte da impressora A1
2. Fixar o eixo de rotacao da bobina com seguranca
3. Conectar os tubos PTFE entre o AMS Lite e a impressora

### Carregamento de Filamento
1. Alinhar o filamento com a entrada do alimentador (feeder inlet)
2. Inserir o filamento pela porta de insercao
3. O alimentador puxa automaticamente ~40 cm de filamento pelo tubo PTFE
4. Se atolado: pressionar botao de liberacao para desengatar o motor

### Deteccao RFID
- Cada slot tem uma bobina RFID
- Filamentos Bambu Lab sao detectados automaticamente
- Propriedades (tipo, cor, temperatura) sao lidas do chip RFID
- Habilitada por padrao, nao pode ser desativada
- Filamentos de terceiros: configurar manualmente no Bambu Studio ou na impressora

---

## Workflow de Impressao Multicolorida

### No Bambu Studio

#### Passo 1: Adicionar Filamentos
- Importar o modelo 3D
- Adicionar os filamentos/cores desejados na lista de filamentos
- Se usar suporte de material diferente (ex: PVA), adicionar tambem

#### Passo 2: Colorir o Modelo
O Bambu Studio oferece ferramentas de pintura:

| Ferramenta | Descricao |
|---|---|
| **Color Painting** | Pintar cores diretamente no modelo 3D |
| **Paint by Face** | Aplicar cor por face do modelo |
| **Split by Color** | Separar modelo em partes por cor |

#### Passo 3: Fatiar e Imprimir
1. Clicar em **Slice Plate** (canto superior direito)
2. Clicar em **Print Plate**
3. Mapear filamentos reais no AMS para as cores do arquivo
4. O mapeamento automatico escolhe a cor mais proxima

### Mapeamento Automatico de Filamentos
- Ao enviar impressao multicolorida, o slicer mapeia automaticamente
  as cores do modelo para os filamentos nos slots do AMS
- Pode ser customizado manualmente na janela de mapeamento
- Se nenhum filamento corresponde a cor, escolher substituto com
  propriedades similares

---

## Transicao de Cores (Flushing)

### Como Funciona
Quando o AMS troca de filamento, o novo filamento empurra o antigo para fora do
extrusor/bico. Durante essa transicao, a cor muda gradualmente. Para garantir
que a cor do modelo nao seja contaminada, e necessario um **volume de flush** suficiente.

### Volume de Flush
- Configuravel no Bambu Studio
- Mais flush = cores mais limpas, mas mais desperdicio
- Menos flush = menos desperdicio, mas possivel contaminacao de cor
- Cores claras apos escuras requerem MAIS flush
- Cores escuras apos claras requerem MENOS flush

### Torre de Purga (Purge Tower)
- O Bambu Studio gera automaticamente uma torre de purga
- Consome filamento durante trocas de cor
- Tamanho configuravel
- Pode ser minimizada otimizando a ordem das cores

### Dicas para Reduzir Desperdicio
1. **Minimizar trocas de cor:** Agrupar areas da mesma cor em camadas proximas
2. **Ordem de cores:** Planejar sequencia de cores para minimizar flush
3. **Flush into infill:** Usar material de flush como infill do modelo
4. **Usar cores similares em sequencia:** Transicoes entre cores proximas requerem menos flush

---

## Backup de Filamento

### Recurso AMS Filament Backup
- Quando o filamento de um slot acaba, o AMS Lite troca automaticamente
  para outro slot com filamento identico
- Propriedades verificadas: marca, tipo, cor, temperatura do bico
- Se nao encontrar filamento identico, exibe aviso

### Ativacao
- Habilitar "AMS filament backup" nas configuracoes do AMS
- Util para impressoes longas ou quando a bobina esta quase vazia

---

## Limitacoes da Impressao Multicolorida na A1

| Limitacao | Detalhes |
|---|---|
| **Maximo 4 cores** | Apenas 1 AMS Lite suportado |
| **Tempo adicional** | Cada troca de cor adiciona tempo (purga + troca) |
| **Desperdicio de material** | Torre de purga consome filamento |
| **Materiais limitados** | TPU, PVA, CF/GF nao funcionam no AMS Lite |
| **Resolucao de cor** | Nao mistura cores - cores sao por regiao/face |
| **Apenas 1 bico** | Nao e dual-extrusion, trocas sao sequenciais |

---

## Dicas para Melhores Resultados Multicoloridos

1. **Design com cores em mente:** Planejar separacao de cores durante modelagem
2. **Usar cores contrastantes:** Cores muito similares podem parecer iguais apos flush
3. **Testar flush volume:** Fazer teste com amostras pequenas primeiro
4. **Evitar muitas trocas por camada:** Aumenta significativamente o tempo de impressao
5. **PLA e o melhor material:** Mais facil de purgar e mais previsivel
6. **Verificar mapeamento:** Sempre conferir mapeamento de cores antes de imprimir
7. **Limpar tubo PTFE:** Manter os tubos de alimentacao limpos para trocas confiaveis

---

## Fontes
- [Bambu Lab Wiki - AMS Lite Introduction](https://wiki.bambulab.com/en/ams-lite/manual/intro-ams-lite)
- [Bambu Lab Wiki - Multi-Color Printing](https://wiki.bambulab.com/en/software/bambu-studio/multi-color-printing)
- [Bambu Lab Wiki - Multi-Color Printing Operation Guide](https://wiki.bambulab.com/en/x1/manual/multi-color-printing)
- [Bambu Lab Wiki - A1 First Print with AMS Lite](https://wiki.bambulab.com/en/a1/manual/first-print-with-ams-lite)
- [Bambu Lab US Store - AMS Lite](https://us.store.bambulab.com/products/ams-lite)
