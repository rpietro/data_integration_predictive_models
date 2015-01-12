
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






















