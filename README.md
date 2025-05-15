# AVA1-Spotify-Popularity-Tracks
Avaliação Prática – Análise de Faixas Musicais com a API do Spotify (Tracks)

- Disciplina: Análise Musical com Dados Digitais
- Ambiente: Google Colab + Python
- Fonte de Dados: https://api.spotify.com/v1/tracks

## Objetivo da Avaliação 
Você deverá desenvolver um projeto em Python que:
- Consuma dados de diversas faixas musicais a partir de seus IDs usando o endpoint /v1/tracks da API do Spotify;
- Extraia os atributos: nome da faixa, popularidade, duração, nome do artista, nome do álbum e data de lançamento;
- Calcule estatísticas e categorias baseadas nos metadados (tempo médio, faixa longa ou curta, faixa popular ou não);
- Classifica as faixas em perfis com base em critérios de duração e popularidade;
- Treine um modelo Naive Bayes para prever o tipo de perfil de uma nova faixa com base em seus atributos;
- Exporte os dados e apresente gráficos que representem a distribuição das faixas por classe;

## Etapas esperadas da atividade 
1. Autenticação OAuth2 com a API do Spotify 
2. Coleta de dados de pelo menos 50 faixas usando seus track_ids no endpoint /v1/tracks 
3. Extração dos campos: name, popularity, duration_ms, album.release_date, artists, explicit 
4. Conversão de duração de milissegundos para minutos 
5. Criação de variáveis categóricas com base nos critérios: 
   - Faixa curta: menos de 2 minutos
   - Faixa padrão: entre 2 e 5 minutos
   - Faixa longa: mais de 5 minutos
   - Popularidade alta: > 75
   - Popularidade moderada: entre 40 e 75
   - Popularidade baixa: < 40
6. Combinação das variáveis em classes como: 'Popular Longa', 'Curta e Moderada', etc. 
7. Normalização das features e separação entre treino e teste 
8. Treinamento de classificador GaussianNB 
9. Avaliação com classification_report e confusion_matrix 
10. Visualizações: histogramas de duração e popularidade e gráfico de barras por classe de faixa

## Exemplo de estrutura esperada do DataFrame 
1. Campos esperados: track_id | name | duration_min | popularity | album | release_year | classe_faixa
2. Definição do Target: classe_faixa
3. Target categórico com base em regras combinadas de duração e popularidade: 
   - Popular Longa → duração > 5 min e popularidade > 75 
   - Popular Curta → duração < 2 min e popularidade > 75 
   - Moderada Padrão → duração entre 2 e 5 min e popularidade entre 40 e 75 
   - Nicho Curta → duração < 2 min e popularidade < 40 
   - Nicho Longa → duração > 5 min e popularidade < 40
