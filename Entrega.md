# T2: Programação Paralela Multithread 

Nome: Gabriel Cortez Mazzardo

Disciplina: Programação Paralela

## Parte 1 : Pthreads

**Resposta questão 1:**

TODO

**Resposta questão 2:** 

Considerando que o tempo de execução no primeiro caso (com apenas 1 thread) foi de 7212172 microssegundos, e no segundo caso (com 2 threads) foi de 3864718 microssegundos, a aceleração obtida foi de 1.86615737552x.

<img src="https://i.imgur.com/kTF3qIL.png" width="250">



**Resposta questão 3:** 

Variando-se o número de repetições para valores de 2000, 4000 e 8000 e mantendo-se constantes o número de threads utilizadas em 4 e o tamanho do vetor em 250000, houve uma aceleração de 2.00143864705x ao diminuir-se o número de repetições pela metade (8000 para 4000), e de 1.99613816271x ao diminuir-se novamente pela metade (4000 para 2000), o que demonstra que o número de repetições afeta sim a aceleração, e que esta se sustentou diante dos diferentes números de repetições.

Variando-se o número de threads utilizadas entre 1, 2 e 4 e mantendo-se constantes o número de repetições em 1000000 (igualmente repartido entre as n threads) e o tamanho do vetor em 2000, houve uma aceleração de 2.0434521389 quando o número de threads passou de 1 para 2, e de 2.4987135202x quando passou de 2 para 4, o que demonstra que o número de threads afeta sim a aceleração, e que esta se sustentou diante dos diferentes números de threads.

Variando-se o tamanho dos vetores utilizados para valores de 250000, 500000 e 1000000 e mantendo-se constantes o número de threads em 4 e o número de repetições em 2000, houve uma aceleração de 1.99604134843x ao diminuir-se o tamanho dos vetores pela metade (1000000 para 500000), e de 1.98543134967x ao diminuir-se novamente pela metade (500000 para 250000), o que demonstra que o tamanho do vetor afeta sim a aceleração, e que esta sustentou-se diante dos diferentes tamanhos de vetor utilizados.

Todos os casos de execução (variando-se tanto o número de repetições, tamanho do vetor ou número de threads) foram executados 10 vezes para o cálculo da média de tempo de processamento. Tabelas e gráficos com os dados obtidos estão disponíveis na resposta da **questão 4**, logo abaixo.

**Resposta questão 4:**

Abaixo, estão as tabelas com os dados obtidos durante a execução dos casos requeridos na questão 3, logo acima. Além disso, também constam gráficos em barra, que demonstram a mudança no tempo de processamento entre os diferentes cenários analisados, o que nos mostra a aceleração obtida com o aumento do número de threads/dimunuição de valores para o tamanho dos vetores ou número de repetições.

-> Variando-se o número de repetições:

|nthreads|size|repetitions|usec|
|-----------------|----------------|--------------------|-----------|
|4                |250000          |8000                |11512139   |
|4                |250000          |4000                |5751932    |
|4                |250000          |2000                |2881530    |

<img src="https://i.imgur.com/z3CqDa7.png" width="250">


-> Variando-se o tamanho do vetor:

|nthreads|size|repetitions|usec|
|-----------------|----------------|--------------------|----------------------------|
|4                |1000000         |2000                |11462491                    |
|4                |500000          |2000                |5742612                     |
|4                |250000          |2000                |2892375                     |

<img src="https://i.imgur.com/3zHJyXz.png" width="250">


-> Variando-se o número de threads:

|nthreads|size|repetitions|usec|
|-----------------|----------------|--------------------|-----------|
|1                |1000000         |2000                |7346566    |
|2                |500000          |2000                |3595174    |
|4                |250000          |2000                |1438810    |

<img src="https://i.imgur.com/eR9sv2n.png" width="250">


**Resposta questão 5:**

As duas linhas a mais que a versão completa do programa possui são responsáveis por tratar da exclusão mútua, que assegura o acesso exclusivo (de leitura e escrita) a um recurso compartilhado por duas ou mais Threads, que nesse caso é a variável "dot_data.c". Sem as linhas de mutex, o programa "pthreads_dotprod2.c" não garante que o resultado final da execução será correto, pois mais de uma thread pode ter acesso à região crítica ao mesmo tempo e ler/escrever um valor indevido na variável "dot_data.c".

## Parte 2: OpenMP

**Resposta questão 1:**

O arquivo da implementação está na pasta raíz do repositório, com o nome de "OPENMP_dotprod.c" :).

**Resposta questão 2:**

O desempenho do programa OpenMP implementado foi analisado utilizando-se os mesmos testes aplicados na **questão 3 da Parte 1** do trabalho, com os mesmos valores distintos de número de threads, tamanhos de vetores e número de repetições. As tabelas e gráficos abaixo foram gerados com base nos resultados obtidos, e demonstram o desempenho do programa implementado em OpenMP. No geral, observa-se, tanto pelos valores vistos nas tabelas e gráficos abaixo, quanto pelo arquivo "results.csv" que possui um compilado dos resultados dos testes, que o programa implementado em OpenMP obteve tempos de processamento um pouco menores que o equivalente em POSIX e, portanto, um melhor desempenho.


-> Variando-se o número de repetições:

|nthreads|size  |repetitions|usec    |
|--------|------|-----------|--------|
|4       |250000|8000       |11472043|
|4       |250000|4000       |5739137 |
|4       |250000|2000       |2865963 |

<img src="https://i.imgur.com/wwREOOf.png" width="250">


-> Variando-se o tamanho do vetor:

|nthreads|size  |repetitions|usec    |
|--------|------|-----------|--------|
|4       |1000000|2000       |11443664|
|4       |500000|2000       |5720374 |
|4       |250000|2000       |2871369 |

<img src="https://i.imgur.com/JEVqGlM.png" width="250">


-> Variando-se o número de Threads:

|nthreads|size  |repetitions|usec    |
|--------|------|-----------|--------|
|1       |1000000|2000       |7043961 |
|2       |500000|2000       |3195422 |
|4       |250000|2000       |1398253 |

<img src="https://i.imgur.com/koRodXH.png" width="250">


## Referências

- [Executando OpenMP](http://www.inf.ufsc.br/~bosco.sobral/ensino/ine5645/Conceitos_OpenMP.pdf)
- [Guide into OpenMP: Easy multithreading programming for C++](https://bisqwit.iki.fi/story/howto/openmp/)
- [POSIX Threads Programming](https://computing.llnl.gov/tutorials/pthreads/)


