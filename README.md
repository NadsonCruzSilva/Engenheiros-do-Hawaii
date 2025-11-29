![Nuvem de Palavras](<img width="980" height="496" alt="image" src="https://github.com/user-attachments/assets/e93c2a32-dbe2-4ebb-9d64-3761b382f22d" />)

**Instituição:** IFES
**Disciplina:** Tópicos Especiais em Banco de Dados
**Grupo:** Flávia Partelli e Nadson da Cruz


---

## 1. Visão Geral do Projeto
Este projeto tem como objetivo aplicar técnicas de Processamento de Linguagem Natural (NLP) e modelos de linguagem (LLMs) para analisar a discografia da banda **Engenheiros do Hawaii**.

O foco foi investigar padrões no estilo lírico de Humberto Gessinger, utilizando desde contagens estatísticas simples até modelos de IA para detecção de similaridade semântica.

---

## 2. Experimentos Realizados (b.1)

Selecionamos três experimentos distintos conforme o desafio proposto:

1.  **Similaridade entre Letras (Embeddings):** Uso de IA para encontrar conexões semânticas profundas (Opção 1 do Desafio).
2.  **Palavras e Temas Dominantes (Nuvem):** Análise de frequência de vocabulário (Opção 2 do Desafio).
3.  **Classificação Intuitiva:** Categorização baseada em léxico de sentimentos (Opção 4 do Desafio).

---

## 3. Resultados e Métricas (b.2 e b.3)

### Experimento 1: Similaridade Semântica com Embeddings
**Objetivo:** Descobrir quais músicas tratam dos mesmos temas, mesmo que não usem as mesmas palavras.

* **Metodologia:** Utilizamos a biblioteca `sentence-transformers` com o modelo `paraphrase-multilingual-MiniLM-L12-v2`. Transformamos cada letra em um vetor vetorial (embedding) e calculamos a distância entre eles.
* **Métrica Utilizada:** **Similaridade de Cosseno** (Cosine Similarity), onde 1.0 significa idêntico e 0.0 significa totalmente diferente.

**Resultados Quantitativos:**
Para a música alvo **"Infinita Highway"**, o modelo identificou o seguinte Top 3 de similaridade:

1.  **[Cruzada]** — Score: `0.63`
2.  **[Deserto Freezer]** — Score: `0.61`
3.  **[A Promessa]** — Score: `0.52`
4.  **[Ando Só]** — Score: `0.52`

**Análise Qualitativa:**
O modelo foi capaz de agrupar músicas que compartilham a temática da **solidão, do deslocamento e da jornada individual**.
* Enquanto *Infinita Highway* fala sobre dirigir sozinho ("viver não é preciso"), *Ando Só* e *Cruzada* reforçam a ideia do indivíduo que caminha solitário pelas ruas ou pela vida ("não sei andar sozinho por essas ruas", "ando só pois só eu sei pra onde ir").
* Isso prova que os embeddings capturaram o sentimento de isolamento e movimento, indo além da simples coincidência de palavras.

---

### Experimento 2: Nuvem de Palavras e Temas Dominantes
**Objetivo:** Visualizar os termos mais frequentes ("buzzwords") na discografia da banda.

* **Metodologia:** Unificação de todo o *corpus* (letras), remoção de *stopwords* (conectivos sem significado) e tokenização simples.
* **Métrica Utilizada:** **Frequência de Termo (TF)** - contagem absoluta de aparições.

**Visualização (Print/Gráfico):**
![Nuvem de Palavras](<img width="980" height="496" alt="image" src="https://github.com/user-attachments/assets/e93c2a32-dbe2-4ebb-9d64-3761b382f22d" />)

**Resultados Quantitativos:**
As palavras com maior frequência absoluta foram:
1.  **Tudo**
2.  **Dia**
3.  **Nada**


**Análise Qualitativa:**
A predominância dos termos opostos **"Tudo"** e **"Nada"** nas primeiras posições confirma estatisticamente a característica central da lírica de Humberto Gessinger: o uso constante de **paradoxos e dicotomias**. As letras transitam frequentemente entre a totalidade e o vazio. Além disso, a alta frequência da palavra **"Dia"** reforça a temática da passagem do tempo e a observação do cotidiano, elementos essenciais na narrativa da banda.

---

### Experimento 3: Classificação Intuitiva (Léxico Robusto)
**Objetivo:** Classificar automaticamente **toda a discografia** em três categorias temáticas: *Melancólica*, *Otimista* ou *Filosófica*.

**Metodologia:**
Desenvolvemos um classificador baseado em regras com um dicionário léxico expandido:
* **Léxico Melancólico:** *tristeza, solidão, dor, fim, vazio, choro...*
* **Léxico Otimista:** *esperança, luz, sol, vida, renascer, vitória...*
* **Léxico Filosófico:** *tempo, razão, ser, verdade, existência, universo...*

O algoritmo percorreu todas as músicas da base de dados, contabilizou as ocorrências e atribuiu a categoria dominante para cada canção.

**Resultados Quantitativos (Distribuição):**
O gráfico abaixo mostra a quantidade de músicas identificadas em cada categoria:

![Gráfico de Barras]([INSIRA AQUI O PRINT DO GRÁFICO DE BARRAS GERADO PELO CÓDIGO])

* **Melancólica:**`[62]` músicas (Categoria Dominante)
* **Filosófica:** `[58]` músicas
* **Otimista:** `[45]` músicas
* **Indefinido:** `[12]` músicas

**Exemplos Classificados pelo Algoritmo:**
* **Músicas Melancólicas:** *Piano Bar, Vozes, Alívio Imediato*
* **Músicas Filosóficas:** *Seguir Viagem, Longe Demais das Capitais, A Conquista do Espaço*
* **Músicas Otimistas:** *Outras Frequências, Segurança, Nunca Mais Poder*

**Análise Qualitativa:**
O classificador apontou uma predominância da categoria **Melancólica**, o que condiz com a crítica musical sobre a banda. O uso de um dicionário expandido (incluindo sinônimos como "angústia" e "nostalgia") permitiu uma classificação mais precisa do que a contagem simples de poucas palavras, capturando melhor as nuances das letras.

---
---

## 4. Reflexão Final

A realização destes experimentos demonstrou como diferentes níveis de complexidade computacional revelam facetas diferentes da obra artística:

1.  A **contagem simples (Exp B e C)** foi surpreendentemente eficaz para categorizar o gênero e o estilo geral da banda.
2.  O uso de **Inteligência Artificial (Exp A)** trouxe um nível de profundidade maior, encontrando conexões sutis de significado que passariam despercebidas numa análise puramente estatística.

Concluímos que a máquina consegue, sim, "entender" a estrutura temática dos Engenheiros do Hawaii, validando matematicamente a percepção de que se trata de uma banda de rock com viés existencialista e filosófico.
