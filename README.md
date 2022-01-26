# Sz_Desafio

Ambos os arquivos desafio_priceav.csv e desafio_details.csv foram introduzidos, tratados e analisados no https://colab.research.google.com/.  foi utilizado programação Python, com importação das seguintes bibliotecas:
import numpy as np
import pandas as pd
!pip install dataprep
import dataprep
from dataprep.eda import create_report
from dataprep.eda import plot
import datetime


      desafio_priceav.csv: Foi dividido em 5 colunas: airbnb_listing_id, booked_on, date, price_string e occupied. A coluna “unnamed: 0” e “unnamed: 1” foram excluídas por (ao que parece) se tratar de uma organização de index anterior.
 	Na coluna “booked_on”, os espaços que não estavam marcadas com datas, estavam marcadas como “Blank”. Entretanto, o arquivo de desafio PDF (seazone_code_challenge_data_science) se refere ao “Blank” como “Null”. Por isso, foi adotado o padrão “Null” neste arquivo.
      Outro ponto a ser abordado é a coluna “ocuppied”, que se refere à coluna “available” no desafio do arquivo PDF. Note que se tentarmos alterar o termo “occupied” por “available”, haverá uma interpretação oposta dos dados booleanos desta coluna. De certa forma, esta alteração também influenciaria na interpretação da coluna “booked_on” e os resultados seriam interpretados erroneamente. Por isto, foi preferível permanecer o termo “occupied” para evitar mais transformações na tabela. Em adição, se torna mais relevante realizar a alteração do termo “available” para “occupied” no arquivo PDF. 

      desafio_details.csv: Foi dividido em 8 colunas: airbnb_listing_id, location, ad_name, number_of_bedrooms, number_of_bathrooms, star_rating, is_superhost e number_of_reviews. A coluna “unnamed: 0” foi excluída por se tratar de uma organização de index anterior.
 	O termo da coluna “suburb” foi substituído por “location”, pois é mais apropriado e para corroborar com o termo utilizado no desafio PDF. Fora isso, nenhum outro título das colunas da tabela CSV foi alterada. 

Respostas:

1. Ordene os bairros em ordem crescente de número de listings.
R: para acessar os bairros em ordem crescente de número de listings, execute num_listing_cres. 


2. Ordene os bairros em ordem crescente de faturamento médio dos listings.
 R: Para acessar os bairros em ordem crescente de faturamento médio dos listings, execute fm_location_cres. 


3. Existem correlações entre as características de um anúncio e seu faturamento?
a. Quais? Explique.
R: Dentre as características de um anúncio, existe correlações claras entre os títulos de um anúncio (coluna ad_name) e bairros (coluna location). Note que o bairro com maior locação, e por consequência, maior faturamento é o bairro Ingleses com 51.46% (2.04x maior que o segundo bairro) do total de locações do Airbnb de Florianópolis – SC. Canavieiras é o segundo bairro mais locado, com 25.29% do total de locações, seguido respectivamente pelos bairros Jurerê (11.43%), Lagoa da Conceição (6.40%) e Centro (5.41%). 
      Este resultado se reflete no título dos anúncios, pois dentre as locações efetuadas, foi visto que as palavras mais frequentes são: praia (5.08%), apartamento (4.98%), Ingleses (3.98%) e mar (3.49%). Em conclusão, neste conjunto de dados observamos que os clientes do Airbnb em Florianópolis têm preferência por locação de apartamento perto de praias, especialmente no bairro Ingleses.
      Para acessar estas informações, execute create_report(corr_fat_anun)
      Para mais informações, acesse a opção Variables (location e ad_name) e clique em Show Details. 


4. Qual a antecedência média das reservas?
a. Esse número é maior ou menor para finais de semana?
R: A antecedência média das reservas é de 32 dias, 08 horas, 26 minutos e 27 segundos. 
      Execute med_antec_reservas.mean() para visualizar.
      Este número é maior em finais de semana em comparação com os dias da semana. O dia da semana que mais possui antecedência média de reservas é o sábado (15.49%), seguido por domingo (14.59%) e sexta (14.58%).
      Se estivermos contabilizando sábado e domingo como finais de semana, ambos somam 30.08% do total de antecedência média das reservas. Já se estivermos contabilizando sexta, sábado e domingo como finais de semana, somamos 44.66% do total de antecedência média das reservas. 
      Execute plot(reserva_semana) para visualizar.
      Obs: Em Python, os dias da semana podem ser contabilizados de 0 a 6. A segunda começa no 0 e termina no domingo, com número 6. 


