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


**Descrição da tabela:**

*A tabela contém quatro colunas:<br>
a primeira informa o código do município, de acordo com o padrão do IBGE;<br>
a segunda, o nome do município;<br>
a terceira, o período - que corresponde ao ano da apuração;<br>
a quarta e última, o valor - que corresponde à taxa de homicídios apurada.*

### Cálculo da taxa de homicídios

A taxa de homicídios é um indicador calculado de acordo com a fórmula:<br>
<center>$$\left(Óbitos/População * 100.000\right)$$<br><br>

Utilizou-se a tabela de população divulgada pelo [IBGE](https://www.ibge.gov.br/estatisticas/sociais/populacao/22827-censo-demografico-2022.html?edicao=37225&t=resultados) correspondente ao censo demográfico realizado em 2022.




