# Atlas da Violência 2024

## Análise de dados na linha de comando 

### Introdução

Jupyter Lab é uma ferramenta formidável, com ela você pode utilizar kernels de diferentes linguagens. Já testei kernels do Python, Octave e Bash.

Em meu último experimento, empreguei **awk** para analisar a série histórica das taxas de homicídio fis municípios brasileiros, produzida pelo Instituto de Pesquisa Econômica Aplicada (IPEA), 
em parceria com o Fórum Brasileiro de Segurança Pública (FBSP). 

Para instalar o JupyterLab no Ubuntu 22.04, utilizei este tutorial do [*Real Python*](https://realpython.com/using-jupyterlab/#linux-1).

Para instalar o kernel do Bash no JupyterLab, segui as dicas deste blog da [SaturnCloud](https://saturncloud.io/blog/how-to-use-bash-commands-in-jupyter-notebook/).

### Recursos

[Atlas da Violência 2024](https://www.ipea.gov.br/atlasviolencia/publicacoes)

[Censo 2022](https://www.ibge.gov.br/estatisticas/sociais/populacao/22827-censo-demografico-2022.html?edicao=37225&t=resultados)

### Objetivo

Com o intuito de demonstrar a eficácia do **awk** para processamento de dados, utilizamos como exemplo as estatísticas do Atlas da Violência 2024. 

De acordo com notícia veiculada pelo [G1 Bahia](https://g1.globo.com/ba/bahia/noticia/2024/06/18/atlas-da-violencia-2024-santo-antonio-de-jesus.ghtml#:~:text=A%20cidade%20de%20Santo%20Ant%C3%B4nio,de%20Seguran%C3%A7a%20P%C3%BAblica%20(FBSP).), Santo Antônio de Jesus, município situado no recôncavo baiano, possui a maior taxa de homicídios do Brasil, em 2022.

Então fomos conferir o resultado.

### Processamento

Com um ligeiro intervalo, as séries históricas vão de 1989 a 1995 e de 2000 a 2022:

![image](https://github.com/guiajf/atlas/assets/152413615/3d2fcb48-6dae-4cab-92b6-1954cb9625e8)

A tabela da série histórica possui a seguinte estrutura:

![image](https://github.com/guiajf/atlas/assets/152413615/715a609c-5a0e-4d72-96dc-d3ea3320aa94)


**Descrição da tabela de homicídios:**

*A tabela contém quatro colunas:<br>
a primeira informa o código do município, de acordo com o padrão do IBGE;<br>
a segunda, o nome do município;<br>
a terceira, o período - que corresponde ao ano da apuração;<br>
a quarta e última, o valor - que corresponde à taxa de homicídios apurada.*

### Cálculo da taxa de homicídios

A taxa de homicídios é um indicador calculado de acordo com a fórmula:<br>
<center>Óbitos/População * 100.000</center><br><br>

Utilizou-se a tabela de população divulgada pelo [IBGE](https://www.ibge.gov.br/estatisticas/sociais/populacao/22827-censo-demografico-2022.html?edicao=37225&t=resultados) correspondente ao censo demográfico realizado em 2022.

### Tabela do censo demográfico 2022

![image](https://github.com/guiajf/atlas/assets/152413615/bdd8dc17-6811-44f5-98c3-1a2d7870e7d0)

Removemos a primeira, a sexta e a sétima colunas e substituímos o separador de milhar.

Listamos os municípios menos populosos:

![image](https://github.com/guiajf/atlas/assets/152413615/6eaa5cb4-eb14-44bf-8312-9344cee2b402)

Listamos os municípios mais populosos (metrópoles):

![image](https://github.com/guiajf/atlas/assets/152413615/0070241e-e5db-437c-aed7-aa94874e290c)

### Junção das tabelas

Na tabela "taxa_homicidios_2024.csv", os dois primeiros dígitos do código do município contém o Código da UF, de acordo com a tabela do IBGE. Na tabela do Censo 2022, os códigos da UF e do Município são apresentados em colunas separadas.

Primeiro, salvamos as modificações anteriores em um arquivo temporário:

![image](https://github.com/guiajf/atlas/assets/152413615/8f913c32-e789-4cb7-a5bf-455ba6ecb069)

Depois, unificamos os códigos da UF e Município em uma nova coluna, para padronizar a disposição das duas tabelas:

![image](https://github.com/guiajf/atlas/assets/152413615/ff75aaba-026b-4e61-8640-72eb2aadecf1)

Salvamos a saída em um novo arquivo e removemos o arquivo temporário:

![image](https://github.com/guiajf/atlas/assets/152413615/d8cf2ee2-84b5-4ff1-8803-4efec96a4fd6)

Adicionamos a coluna "pop_total" da tabela do Censo 2022 ao arquivo que contém a tabela da taxa de homicídios:

![image](https://github.com/guiajf/atlas/assets/152413615/d248c1fc-3176-420a-8ab9-bd506ef8fe93)

Salvamos a saída em um novo arquivo:

![image](https://github.com/guiajf/atlas/assets/152413615/52dbc6d4-253b-45ad-a82e-d599f4bcebe1)


### Classificação

Quando ordenamos os municípios do Estado da Bahia em ordem descendente, pela taxa de homicídios, para o ano de 2022, os dados apresentam anomalias:

![image](https://github.com/guiajf/atlas/assets/152413615/ea79b36e-a85a-4cd8-befd-a643f8248049)

O "campeão" nacional nessa triste estatística é outro:

![image](https://github.com/guiajf/atlas/assets/152413615/0d818c7e-0071-42af-9205-e4e3f2db401a)

Dentre os municípios com população de 50 a 100 mil habitantes, o mais violento seria Santa Inês/MA:

![image](https://github.com/guiajf/atlas/assets/152413615/d5be12f5-494a-422d-b0cd-918973c34e37)

### Considerações finais

Acreditamos que possa haver alguma inconsistência na formatação da saída ou no cálculo da taxa para alguns municípios, que não conseguimos identificar.




















