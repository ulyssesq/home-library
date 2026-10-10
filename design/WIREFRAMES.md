# BookSticker — Especificação de Design e Wireframes (v2.0)

> **Versão:** 2.0.0  
> **Status:** Aprovado para Prototipação  
> **Evolução Arquitetural:** Transição da metáfora literal de "cromos" para o **Sistema de Coleções & Selos Triplos de Maestria** (separação rigorosa entre Posse Física e Consumo Literário), inclusão do **Tsundoku Tracker**, **Modo Prateleira (Scanner em Lote)** e **Métricas de Vocabulário / CEFR por IA**.

---

## 1. Princípios de Design & Modelo Conceitual

### 1.1 Separação Essencial: Posse Física vs. Experiência de Leitura
O leitor contemporâneo gerencia duas dimensões independentes:
- **Posse Física (O Objeto):** *Tenho na estante*, *Já tive (doei/vendi)*, *Peguei emprestado*, *Não possuo*.
- **Leitura (O Conhecimento):** *Lido*, *Lendo (páginas / %)*, *Quero Ler*, *Abandonado*.

### 1.2 O Sistema de Selos Triplos de Coleção (Tri-Seal System)
Os livros em cada álbum são classificados e exibidos visualmente com base nessa matriz:

| Selo / Nível | Critério (Posse x Leitura) | Visual no Álbum | Impacto no Perfil |
| :--- | :--- | :--- | :--- |
| 🥇 **Selo Ouro (Master)** | **Possui na Estante** + **Leitura Concluída** | Capa em cor plena, moldura dourada e insígnia de louro | Pontuação máxima de Colecionador-Leitor |
| 🥈 **Selo Prata (Leitor Ávido)** | **Não Possui** (Emprestado/Doado/Kindle) + **Leitura Concluída** | Capa em cor plena com moldura prateada refinada | Conta para o progresso intelectual e vocabulário |
| 🥉 **Selo Bronze (Guardião)** | **Possui na Estante** + **Não Lido / Lendo** | Capa com moldura bronze e indicador de leitura | Entra no cálculo da **Calculadora de Tsundoku** |
| ⚪ **Espaço Vazio (Bloqueado)** | **Não Possui** + **Não Lido** | Silhueta elegante com contorno pontilhado e número | Elegível para a **Wishlist Pública** |

---

## 2. Mapa de Navegação e Fluxos

```
[ App Launch ]
      │
      ├──> [ Tab 1: Coleções & Álbuns ] ─────> [ Detalhes do Álbum (Grid de Selos) ]
      │                                                │
      │                                                ├──> [ Ficha da Obra: Vocabulário, CEFR & IA ]
      │                                                ├──> [ Painel da Pilha Tsundoku ]
      │                                                └──> [ Exportar Wishlist Pública ]
      │
      ├──> [ Tab 2: Scanner Rápido ] ─────────> [ Alternador de Modos ]
      │                                                ├──> [ Modo Unitário + Bottom Sheet ]
      │                                                ├──> [ Modo Prateleira (Scanner em Lote) ]
      │                                                └──> [ OCR de Lombada / Folha de Rosto ]
      │
      ├──> [ Tab 3: Minha Estante & Estatísticas ] ──> [ Gráficos de Leitura & Nível Lexical ]
      │
      └──> [ Tab 4: Explorar Desafios ] ──────> [ Novos Álbuns Temáticos Curados ]
```

---

## 3. Wireframes Detalhados por Tela

---

### TELA 1: Scanner Rápido, Modo Prateleira & OCR de Contingência

```
┌────────────────────────────────────────────────────────┐
│ [X] Flash [⚡]   [• Unitário | ● MODO PRATELEIRA]  [?] │
├────────────────────────────────────────────────────────┤
│                                                        │
│              ┌────────────────────┐                    │
│              │ ┌────────────────┐ │                    │
│              │ │  ||||||||||||  │ │  <-- Retículo com  │
│              │ │  9788535914849 │ │      laser ativo   │
│              │ └────────────────┘ │                    │
│              └────────────────────┘                    │
│          [ ✓ Bip! 9788535914849 adicionado ]           │
│                                                        │
│ [ 📷 Sem código de barras? Tirar foto da Lombada/Folha ]│
├────────────────────────────────────────────────────────┤
│ BANDEJA DA PRATELEIRA (8 LIVROS BIPADOS):              │
│ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐                │
│ │1984 │ │Dom  │ │Cem  │ │O    │ │Sapi-│  +3 livros...  │
│ │     │ │Casm.│ │Anos │ │Idio.│ │ens  │                │
│ └─────┘ └─────┘ └─────┘ └─────┘ └─────┘                │
│                                                        │
│ [ ⭐ SALVAR LOTE DE 8 LIVROS NA ESTANTE / ÁLBUM ]      │
└────────────────────────────────────────────────────────┘
```

#### Elementos e Inovações:
1. **Alternador de Modos:**
   - *Unitário:* Abre bottom sheet detalhado com ficha completa a cada bip.
   - *Modo Prateleira:* A câmera nunca fecha. Emite vibração e bipe a cada ISBN capturado, empilhando na bandeja inferior. Permite cadastrar 30 livros da estante em menos de 2 minutos.
2. **OCR de Lombada / Folha de Rosto (Vision AI):**
   - Botão para livros antigos de sebo sem código de barras. Dispara visão computacional para extrair título e autor e buscar os metadados.

---

### TELA 2: Álbum de Coleção & Painel Tsundoku

```
┌────────────────────────────────────────────────────────┐
│ [< Voltar]      1001 Livros Para Ler      [Compartilhar]
├────────────────────────────────────────────────────────┤
│ PROGRESSO GERAL: 54 / 100 Títulos Concluídos (54%)     │
│ [████████████████████░░░░░░░░░░░░░░░░░]                │
│ Selos: 🥇 28 Ouro  •  🥈 14 Prata  •  🥉 12 Bronze    │
├────────────────────────────────────────────────────────┤
│ 📚 PILHA TSUNDOKU DESTE ÁLBUM:                         │
│ "Você tem 12 livros físicos na estante ainda não lidos.│
│ No seu ritmo (2.4 livros/mês), são ~5 meses de leitura."│
├────────────────────────────────────────────────────────┤
│ Filtros: [ Todos ] [ 🥇 Ouro ] [ 🥈 Prata ] [ 🥉 Bronze ] [ ⚪ Faltam ]
├────────────────────────────────────────────────────────┤
│ GRID DE LIVROS:                                        │
│                                                        │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐              │
│  │ 🥇 OURO  │  │ 🥈 PRATA │  │ 🥉 BRONZE│              │
│  │ [CAPA A] │  │ [CAPA B] │  │ [CAPA C] │              │
│  │ 1984     │  │ Dom      │  │ Grande   │              │
│  │          │  │ Casmurro │  │ Sertão   │              │
│  │ [Tenho+  │  │ [Lido    │  │ [Na      │              │
│  │  Lido ✓] │  │  s/posse]│  │  Estante]│              │
│  └──────────┘  └──────────┘  └──────────┘              │
│                                                        │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐              │
│  │ ⚪ VAZIO │  │ 🥇 OURO  │  │ ⚪ VAZIO │              │
│  │ ┌──────┐ │  │ [CAPA E] │  │ ┌──────┐ │              │
│  │ │SILHU-│ │  │ Ulisses  │  │ │SILHU-│ │              │
│  │ │ ETTA │ │  │          │  │ │ ETTA │ │              │
│  │ └──────┘ │  │ [Tenho+  │  │ └──────┘ │              │
│  │ Cem Anos │  │  Lido ✓] │  │ O Idiota │              │
│  └──────────┘  └──────────┘  └──────────┘              │
└────────────────────────────────────────────────────────┘
```

---

### TELA 3: Ficha da Obra — Vocabulário, CEFR & Glossário por IA

```
┌────────────────────────────────────────────────────────┐
│ [< Voltar]            Ficha da Obra           [Editar] │
├────────────────────────────────────────────────────────┤
│              ┌──────────┐                              │
│              │ CAPA EM  │   Selo Atual: 🥇 OURO        │
│              │ ALTA DEF │   Álbum: 1001 Livros (#001)  │
│              └──────────┘                              │
│           Dom Casmurro (1899)                          │
│           Machado de Assis • 256 págs                  │
│                                                        │
│ ── GESTÃO DE POSSE E LEITURA ───────────────────────── │
│ Posse Física:     [X] Tenho na Estante                 │
│ Status de Leitura:[X] Lido  (Concluído em 14/08/2026)  │
│                                                        │
│ ── 🧠 ANÁLISE LINGUÍSTICA & IA ─────────────────────── │
│ ┌────────────────────────────────────────────────────┐ │
│ │ 📖 Complexidade Lexical: ERUDITO / CLÁSSICO SÉC XIX│ │
│ │ Nível CEFR Equivalente: C1 / C2 (Leitura Avançada) │ │
│ │ Volume Estimado de Vocabulário Único: ~8.400 termos│ │
│ ├────────────────────────────────────────────────────┤ │
│ │ 📝 Mini-Glossário de Apoio da Obra:                 │ │
│ │ • Casmurro: Teimoso, obstinado, calado, retraído.  │ │
│ │ • Metonímia: Figura de linguagem de substituição.  │ │
│ │ • Alvíssaras: Recompensa ou prêmio por boas novas. │ │
│ │ • Empáfia: Soberba, arrogância, presunção.         │ │
│ ├────────────────────────────────────────────────────┤ │
│ │ 🎯 Ganho no Perfil do Leitor:                      │ │
│ │ +320 pontos de repertório lexical erudito          │ │
│ └────────────────────────────────────────────────────┘ │
│                                                        │
│ ── 🗺️ ROADMAP DE RECOMENDAÇÕES ─────────────────────── │
│ • Próximo passo sugerido: "Memórias Póstumas de Brás   │
│   Cubas" ou "O Alienista".                             │
└────────────────────────────────────────────────────────┘
```

---

## 4. Matriz Comparativa de Funcionalidades

| Recurso | Objetivo | Tecnologia / Estratégia |
| :--- | :--- | :--- |
| **Tri-Seal System** | Valorizar quem lê tanto quanto quem compra livros | Relação N:N `UserBooks` com campos `OwnershipStatus` e `ReadingStatus` |
| **Tsundoku Tracker** | Conscientização contra compras por impulso | Lógica relacional simples: `count(possuo && !lido) / media_mensal` |
| **Modo Prateleira** | Escaneamento contínuo sem fricção de modal | SQLite Outbox local com buffer em memória no Expo |
| **OCR de Lombada** | Salvar livros antigos sem ISBN | Vision AI (Google Gemini Flash) com fallback textual |
| **Nível CEFR / Vocabulário** | Aprendizado de idiomas e valorização de clássicos | Análise única por ISBN salva em cache perpétuo no PostgreSQL (`BookAiCurations`) |
