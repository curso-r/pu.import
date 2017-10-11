---
title: 'Introdução'
date: '2017-10-11'
---





Nesta seção, vamos introduzir os principais pacotes para importar dados para o R. Mostraremos como importar dados de arquivos de texto, de planilhas do excel, de extensões de outros programas estatísticos (SAS e SPSS, por exemplo), e como interagir com o SQL.

As funções que apresentaremos aqui carregam os dados em `tibbles`, que diferem dos data.frames em dois pontos importantes:

- imprime os dados na tela de uma forma muito mais organizada, resumida e legível; e

- permite a utilização de *list-columns*.

Se você não estiver familiarizado com o conceito de *list-columns*, não se preocupe. Trataremos melhor do assunto no tópico [Funcionais: o pacote purrr]().










# Importando arquivos de texto

Para importar arquivos de texto para R, como `.txt` ou `.csv`, utilizaremos o pacote `readr`.

Veja alguns exemplos:


```r
dados_txt <- readr::read_table2(file = "data/mtcars.txt")
## Error in loadNamespace(name): there is no package called 'readr'
dados_csv <- readr::read_csv(file = "data/mtcars.csv")
## Error in loadNamespace(name): there is no package called 'readr'
```

<div class='admonition note'>
<p class='admonition-title'>
Exercício relâmpago!
</p>
<p>
Descubra qual a diferença entre as funções "read_table()" e "read_table2()"; e as funções "read_csv()" e "read_csv2()".
</p>
</div>

Também é possível salvar objetos, como data.frames em um tipo especial de arquivos, o `.rds`. A vantagem dessa extensão é guardar a estrutura dos dados salvos, como a classe das colunas de um data.frame. Além disso, é uma boa alternativa para lidar com grandes bancos de dados, já que arquivos `.rds` serão bem mais compactos do que arquivos Excel.


```r
write_rds(mtcars, path = "data/mtcars.rds")
## Error in write_rds(mtcars, path = "data/mtcars.rds"): could not find function "write_rds"
dados <- read_rds(path = "data/mtcars.rds")
## Error in read_rds(path = "data/mtcars.rds"): could not find function "read_rds"
```










# Importando arquivos do Excel

O pacote `readxl` contém funções para ler dados de arquivos do Excel, como `.xls` e `xlsx`.


```r
readxl::read_xls(path = "data/mtcars.xls")
## Error in loadNamespace(name): there is no package called 'readxl'
readxl::read_xlsx(path = "data/mtcars.xlsx")
## Error in loadNamespace(name): there is no package called 'readxl'
```

A funçao `read_excel()` auto detecta a extensão do arquivo.


```r
read_excel(path = "data/mtcars.xls")
## Error in read_excel(path = "data/mtcars.xls"): could not find function "read_excel"
read_excel(path = "data/mtcars.xlsx")
## Error in read_excel(path = "data/mtcars.xlsx"): could not find function "read_excel"
```


