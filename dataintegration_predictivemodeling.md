# Impacto de técnicas de integração de dados em performance de modelos preditivos de classificação e regressão



## Sumário

<!-- escrever ao final -->

## Introdução

* integração utilizada com frequencia cada vez maior para enriquecimento de bancos locais - exemplos medicare, HCUP e outros grandes bancos americanos
    * potencial para melhorar a performance de modelos preditivos
* no entanto parâmetros de qualidade frequentemente não são especificados e portanto medidos já que não existe um padrão ouro, ou a possibilidade de comparar os dados integrados vs. dados reais 
* revisão sobre métodos comuns de integração
* revisão sobre métodos para mensuração de performance em modelos preditivos
* objetivo é utilizar modelos de predição de classificação e regressão como medidas de qualidade de integração de dados

## Métodos

- Enriquecimento do BigData Local com o BigData Publico
- Modelos Preditivos
    - Paralelização do processamento do modelo preditivo
    - Comparação dos modelos preditivos com/sem a incorporação de variáveis públicas



### Técnicas de integração
#### Artigo 1: Semântica manual (rule-based) com variáveis âncora

estabelece camada semântica manualmente
padrão outro

#### Artigo 2: NLP e modelos preditivos para variáveis âncora

NLP gera probabilidade de que dois campos sejam um match
utiliza thresholds de aceitação diferentes em relação ao que seja um matching aceitável

### Técnicas de modelagem


#### Princípio teórico

Usar modelos de regressão e classificação com ou seu variáveis integradas e as suas variações em relação a tipo de matching e observar performance de modelos.
Por exemplo, adicionar uma variavel integrada como variável dependente pode melhorar a performance se ela trouxer informação relevante ou pode degradar performance caso a integração seja espúria.

1. partindo do principio de que pacientes que tenham alto custo levem a um prejuizo e um dilema moral porque os caras nao tem pra onde ir, um modelo possivel seria predizer quais caracteristicas pre-internação levam a um alto custo. esse modelo poderia ser tanto de regressao (custo) quando de classificação (categorias de custo)
2. eu acredito que o diagnostico seja o principal determinante, mas o diagnostico em si não conta a estoria inteira, porque condições socio-economicas e outros fatores devem aumentar o custo por uma serie de motivos indo desde a gravidade da doença (quanto mais pobre, maior a dificuldade de acesso a atendimento, pior a gravidade quando finalmente consegue ser atendido) quanto problemas relacionados a alta (quanto mais pobre, menor a probabilidade de que o paciente possa ser cuidado adequadamente em casa e portanto mantem no hospital mais tempo)


#### Artigo 3 - utilização de um padrão ouro em um banco reduzido 

<!-- eu nao tinha pensado nessa possibilidade até ter visto que voce tem um monte de variaveis comuns no banco local e publico, o que abre a possibilidade  -->

banco com algo em torno de 10.000 observações extraídas de maneira aleatória <!-- dados critérios de inclusão/exclusão - use o que voce achar mais relevante em termos de custo -->


a. monta um modelo completo so com variaveis locais - esse é o padrão ouro
b. retira algumas variaveis e roda de novo
c. tenta enriquecer o banco local trazendo as variaveis que foram retiradas no passo b acima dos bancos publicos e roda um modelo
d. compara os modelos em a, b e c - o modelo em a vai ser melhor, mas a pergunta é em que situações o modelo em c pode ser melhor do que b


#### Artigo 4 - utilização de integração sem um padrão ouro

a. monta um modelo completo só com variaveis locais
b. enriquece com variaveis externas que nao existam localmente mas que em teoria sejam importantes pra predição - no exemplo de modelos sobre alto custo isso seria alguma coisa relacionada a status socio economico - e roda o modelo
c. avalia as situações em que o modelo em b tenha melhor performance do que em a. se isso acontecer voce valida que o enriquecimento levou a uma melhora, mesmo sem ter um padrão ouro

### Artigo 5 - técnicas de paralelização em Big Data

<!-- prometer 5 artigos é um monte e então talvez voce possa querer cortar os artigos e numero 2 e 5 e ficar so com 1, 3 e 4. uma coisa a ser discutida com o massad -->


<!-- 


# Dicionario de Dados

## Base Publica

Eu só estou considerando as bases PUBLICAS de INTERNACOES e não as AMBULAtoRIAIS que juntas dao mais de 300 milhóes de linhas em um único ano.


### Internaçoes (AIHFULL) Total de Observaçoes: 11.511.582

    Esta base de dados reune todos o cabecalho da internacao, contendo os motivos da internaçao ( cirurgica/clinica ). Esta base esta de-identificada, embora tenha informações do CEP 

- ANO_CMPT, ano de competencia
- Mes_cmpt, mes de competencia
- tipo de internacao ( urgencia/emergencia e clínica/cirurgica)
- dados do logradouro ( estado, municipio e cep)
- n_aih, numero do documento ( número único do pacote de billing)
- sexo, sexo do paciente
- nasc, data de nascimento
- qt_diarias, qtde de diarias
- qt_utis ( total de diarias de UTI)
- proc_rea, procedimento realizado ( código do SUS - Tabela de Referencia  )
- val_tot, ( valor total da internaçao enviada para o SUS)
- dt_inter, data de Internacao
- dt_saida, data de Alta
- diag_princ, diagnostico principal
- diag_seg , diagnostico secundário


### Procedimentos (AIH_SP) Total de Observacoes ( 114.287.763 )

    Esta base é filha da tabela de Internacoes ( o campo n_aih é a chave estrangeira). Cada linha da tabela AIHFULL pode ter várias linhas na tabela AIH_SP. 

- n_aih ( numero do documento)
- procedimento realizado ( exames, procedimento cirurgico, procedimentos especiais) 
- qt_de procedimentos
- valor do item



## Base Local

Tenho as mesmas coisas que as informações acima, mas como eu tenho a identificação do paciente, tenho muito mais detalhes que não necessariamente precisam ser enviadas para o SUS. Alem disto, tenho todas as informações do tratamento, exemplo: um determinado paciente foi atendido "n" vezes no ambulatorio, fez "n" cirurgias além dos exames X e Y clinicos e de imagem. Tenho acesso as evoluções e prescrições, sendo que as evoluções estão em texto livre e são realizadas apenas nas enfermarias.

A base de faturamento não representa exatamente o que foi feito da assistencia, tendo e vista que muita coisa não é cobrada e,portanto, não é registrada, mas é uma base que utiliza as regras do Ministério de Saúde e é utilizada para estudos epidemiológicos e populacionais.

 -->