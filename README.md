# **Análise Computacional da Lírica: Engenheiros do Hawaii**

**Instituição:** IFES  
**Disciplina:** Tópicos Especiais em Banco de Dados  
**Grupo:** Flávia Partelli e Nadson da Cruz Silva

---

## **1\. Visão Geral do Projeto**

Este projeto transcende a simples contagem de palavras. Utilizamos técnicas avançadas de Processamento de Linguagem Natural (NLP) e Modelos de Linguagem (LLMs) como ferramentas para desconstruir a "arquitetura de pensamento" de Humberto Gessinger.

O nosso objetivo central foi investigar se os dados matemáticos corroboram a **assinatura existencialista, os paradoxos e a crítica social** que, em nossa visão, definem a banda Engenheiros do Hawaii.

---

## **2\. Experimentos Realizados**

Executamos três abordagens distintas para triangular o estilo da banda:

1. **Palavras e Temas Dominantes (Nuvem de Palavras):** Mapeamento de frequência e relevância (TF-IDF) para identificar as obsessões vocabulares do compositor(Opção 2 do desafio).  
2. **Similaridade Semântica (Embeddings):** Uso de vetores densos para mapear a proximidade de *significado* entre músicas, ignorando a coincidência exata de palavras(Opção 1 do desafio).  
3. **Classificação Temática Intuitiva:** Um classificador baseado em regras léxicas expandidas para categorizar a discografia em estados emocionais(Opção 4 do desafio).

---

## **3\. Resultados Detalhados e Nossa Análise**

### **Experimento 1: Palavras e Temas Dominantes (Nuvem de Palavras)**

*Metodologia: Contagem absoluta e TF-IDF.*

**Objetivo:** Visualizar os termos mais frequentes ("buzzwords") na discografia da banda.

* **Metodologia:** Unificação de todo o *corpus* (letras), remoção de *stopwords* (conectivos sem significado) e tokenização simples.
* **Métrica Utilizada:** **Frequência de Termo (TF)** - contagem absoluta de aparições.

**Visualização (Gráfico):**
![Nuvem de Palavras](nuvem.png)


Os dados extraídos confirmaram nossa hipótese de que o estilo de escrita de Gessinger é estruturalmente baseado em **binarismos e dicotomias**.

**Estatísticas Reveladoras:**

* **Tudo:** 275 ocorrências (1º lugar)  
* **Nada:** 163 ocorrências (3º lugar)  
* **Dia:** 165 ocorrências (2º lugar)  
* **Noite:** 111 ocorrências (10º lugar)

**Nossa Interpretação Estilística:**

1. **A Dialética do Tudo/Nada:** A presença massiva dessas duas palavras no topo da lista não é acidental. Concluímos que a banda constrói sua narrativa através do contraste constante, raramente afirmando algo absoluto sem apresentar o seu oposto.  
2. **A Obsessão Temporal:** Com "Dia", "Noite", "Sempre" (119) e "Tempo" dominando o ranking, definimos a banda, com base nos dados, como "Cronistas do Tempo". As letras focam na passagem do tempo e na efemeridade, mais do que em objetos ou cenários.  
3. **Relevância (TF-IDF):** Destacamos o termo "Gente" (Score 24.24) como altamente relevante. Isso nos indica que, apesar do isolamento ser um tema recorrente, a obra mantém um foco sociológico na observação do comportamento humano.

---

### **Experimento 2: Classificação Temática Intuitiva**

*Metodologia: Classificação via dicionário léxico expandido.*

**Objetivo:** Classificar automaticamente **toda a discografia** em três categorias temáticas: *Melancólica*, *Otimista* ou *Filosófica*.

**Metodologia:**
Desenvolvemos um classificador baseado em regras com um dicionário léxico expandido:
* **Léxico Melancólico:** *tristeza, solidão, dor, fim, vazio, choro...*
* **Léxico Otimista:** *esperança, luz, sol, vida, renascer, vitória...*
* **Léxico Filosófico:** *tempo, razão, ser, verdade, existência, universo...*

O algoritmo percorreu todas as músicas da base de dados, contabilizou as ocorrências e atribuiu a categoria dominante para cada canção.

**Resultados Quantitativos (Distribuição):**
O gráfico abaixo mostra a quantidade de músicas identificadas em cada categoria:

![Gráfico de Barras](grafico.png)

**Análise dos Resultados:**

* **A Predominância da Melancolia:** O fato de 35% das músicas serem classificadas como Melancólicas corrobora nossa percepção da estética *Cold Wave* e Pós-Punk que influenciou a banda.  
* **O "Falso" Otimismo:** Observamos que muitas músicas classificadas como "Otimistas" (como *Vida Real*) possuem letras que desafiam a realidade, sugerindo uma esperança de resistência, e não de alegria ingênua.  
* **Fronteiras Tênues:** O fato de a categoria "Filosófica" estar quase empatada com a "Melancólica" reforça nossa visão de que a tristeza na obra da banda não é passiva, mas sim **cerebral e reflexiva**.

---

### **Experimento 3: Similaridade Semântica (Embeddings)**

*Metodologia: Sentence-Transformers (paraphrase-multilingual-MiniLM-L12-v2) e Similaridade de Cosseno.*

**Objetivo:** Descobrir quais músicas tratam dos mesmos temas, mesmo que não usem as mesmas palavras.

* **Metodologia:** Utilizamos a biblioteca `sentence-transformers` com o modelo `paraphrase-multilingual-MiniLM-L12-v2`. Transformamos cada letra em um vetor vetorial (embedding) e calculamos a distância entre eles.
* **Métrica Utilizada:** **Similaridade de Cosseno** (Cosine Similarity), onde 1.0 significa idêntico e 0.0 significa totalmente diferente.

**Resultados Quantitativos:**
Para a música alvo **"Infinita Highway"**, o modelo identificou o seguinte Top 3 de similaridade:

1.  **[Cruzada]** — Score: `0.63`
2.  **[Deserto Freezer]** — Score: `0.61`
3.  **[A Promessa]** — Score: `0.52`
4.  **[Ando Só]** — Score: `0.52`

Ao analisarmos os vetores gerados, observamos que as conexões vão muito além da coincidência de palavras, revelando o "subtexto" das canções.

#### **Aprofundamento da música "O Papa é Pop"**

A análise desta faixa específica nos trouxe conexões surpreendentes que, sob nossa ótica, explicam a profundidade da crítica da banda.

**Top 3 Similaridades que Encontramos:**

1. **Outono em Porto Alegre** (0.57)  
2. **A Promessa** (0.57)  
3. **A Verdade a Ver Navios** (0.55)

Nossa Interpretação Crítica:  
Inicialmente, estranhamos a conexão de um hit pop explosivo ("O Papa é Pop") com baladas melancólicas. Porém, ao analisarmos as letras lado a lado, concluímos que:

* **A Conexão da "Ilusão":** Enquanto "O Papa é Pop" critica a superficialidade da fama e a mercantilização da fé, "A Verdade a Ver Navios" trata da ausência de verdade ("a verdade não está no porto"). Interpretamos que o algoritmo agrupou ambas pelo tema comum do **vazio de significado** na sociedade moderna.  
* **O Ceticismo:** A proximidade com "Outono em Porto Alegre" reforça nossa tese de que Gessinger é um cético. "Papa" grita sobre a banalidade externa, e "Outono" sussurra sobre a repetição cinza da vida. Para nós, isso evidencia que ambas as músicas compartilham um núcleo de **desencanto com a realidade**.

#### **Aprofundamento da música "Infinita Highway"**

* **Conexões:** *Cruzada* (0.63), *Deserto Freezer* (0.61).  
* **Nossa Análise:** Notamos que o modelo agrupou canções sobre **deslocamento e não-pertencimento**. Não se trata apenas do tema "estrada", mas da incapacidade do indivíduo de se fixar. Tanto em *Cruzada* quanto em *Infinita Highway*, identificamos a narrativa da **solidão em movimento**, validada pela alta similaridade vetorial.

---

## **4\. Reflexão Final: O que a Máquina "Entendeu"?**

Ao final desta investigação, nossa interpretação é que os algoritmos conseguiram, de fato, penetrar na camada semântica da obra de Humberto Gessinger, "entendendo" padrões que geralmente atribuímos à sensibilidade humana.

Destacamos três conclusões principais sobre o que a máquina percebeu:

1. A Máquina Entendeu a Ironia:  
   Ao conectar O Papa é Pop a músicas tristes e reflexivas, a inteligência artificial "percebeu" que a música não é uma celebração pop, mas uma crítica melancólica sobre ela. Para nós, isso prova que o modelo capturou o tom e a intenção por trás das palavras, e não apenas o vocabulário superficial.  
2. A Descoberta da "Fórmula" da Angústia:  
   Nós sabíamos intuitivamente que a banda falava sobre paradoxos. A máquina confirmou isso matematicamente ao colocar "Tudo" e "Nada" como os pilares estatísticos da discografia. Interpretamos isso como a validação de que a angústia na obra dos Engenheiros do Hawaii é estrutural, construída sobre uma lógica binária de oposição constante.  
3. A Solidão é Quantificável:  
   A alta similaridade entre músicas de épocas diferentes (Cruzada e Infinita Highway) nos mostrou que a máquina identificou a coerência temática do compositor. Para o algoritmo, a solidão não mudou de forma em 20 anos; ela manteve a mesma "assinatura vetorial".

Em suma, nossa conclusão é que a máquina não apenas contou palavras, ela **mapeou a arquitetura do desamparo** que define a banda. Os dados nos contaram a mesma história que as músicas: a de indivíduos solitários tentando encontrar sentido entre o tudo e o nada.