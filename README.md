# Degrees-AI
**(Descrição em Português)**

Um programa de IA que determina quantos "graus de separação" existem entre dois atores.

Neste programa, estamos interessados em encontrar o caminho mais curto entre dois atores escolhendo uma sequência de filmes que os conectem. Por exemplo, o caminho mais curto entre Jennifer Lawrence e Tom Hanks é 2: Jennifer Lawrence está conectada a Kevin Bacon por ambos atuarem em "X-Men: Primeira Classe" e Kevin Bacon está conectado a Tom Hanks por ambos atuarem em "Apollo 13".

O código de distribuição contém dois conjuntos de arquivos de dados CSV: um conjunto no diretório grande(large) e um conjunto no diretório pequeno(small). Cada um contém arquivos com os mesmos nomes e a mesma estrutura, mas o conjunto pequeno é um conjunto de dados muito menor para facilitar os testes. (dentro do diretório large, compactei o arquivo people.csv em uma pasta zip pois o arquivo era muito grande para carregar aqui, maior que 25MB)

Cada conjunto de dados consiste em três arquivos CSV.

Abra small/people.csv. Você verá que cada pessoa tem um id único, correspondendo ao id dela no banco de dados do IMDb. Elas também têm um nome e um ano de nascimento. 

Em seguida, abra small/movies.csv. Você verá aqui que cada filme também tem um id único, além de um título e o ano em que o filme foi lançado. 

Agora, abra small/stars.csv. Este arquivo estabelece uma relação entre as pessoas em people.csv e os filmes em movies.csv. Cada linha é um par de valores person_id e movie_id. A primeira linha (ignorando o cabeçalho), por exemplo, indica que a pessoa com id 102 estrelou no filme com id 104257. Checando isso em people.csv e movies.csv, você descobrirá que essa linha está dizendo que Kevin Bacon estrelou no filme “A Few Good Men.” 

Em seguida, dê uma olhada em degrees.py. No topo, várias estruturas de dados são definidas para armazenar informações dos arquivos CSV. O dicionário names é uma forma de procurar uma pessoa pelo nome: ele mapeia nomes para um conjunto de ids correspondentes(porque é possível que múltiplos atores tenham o mesmo nome). O dicionário de pessoas mapeia o id de cada pessoa para outro dicionário com valores para o nome da pessoa, ano de nascimento e o conjunto de todos os filmes em que ela atuou. E o dicionário de filmes mapeia o id de cada filme para outro dicionário com valores para o título do filme, ano de lançamento e o conjunto de todas as estrelas do filme. A função load_data carrega os dados dos arquivos CSV nessas estruturas de dados. 

A função principal neste programa primeiro carrega os dados na memória (o diretório de onde os dados são carregados pode ser especificado por um argumento de linha de comando). Em seguida, a função solicita que o usuário digite dois nomes. A função person_id_for_name recupera o id de qualquer pessoa (e lida com a solicitação ao usuário para esclarecer, no caso de múltiplas pessoas terem o mesmo nome). A função então chama a função shortest_path para calcular o caminho mais curto entre as duas pessoas e imprime o caminho.

rode degrees.py para testar



**(English Description)**

An AI program that determines how many "degrees of separation" apart two actors are.

In this program, we're interested in finding the shortest path between any two actors by choosing a sequence of movies that connects them. For example, the shortest path between Jennifer Lawrence and Tom Hanks is 2: Jennifer Lawrence is connected to Kevin Bacon by both starring in "X-Men: First Class" and Kevin Bacon is connected to Tom Hanks by both starring in "Apollo 13".

The distribution code contains two sets of CSV data files: one set in the large directory and one set in the small directory. Each contains files with the same names, and the same structure, but small is a much smaller dataset for ease of testing and experimentation. (inside the large directory, I compressed the file people.csv into a zip folder because the file was too large to upload here, larger than 25MB)

Each dataset consists of three CSV files.

Open up small/people.csv. You’ll see that each person has a unique id, corresponding with their id in IMDb’s database. They also have a name, and a birth year.

Next, open up small/movies.csv. You’ll see here that each movie also has a unique id, in addition to a title and the year in which the movie was released.

Now, open up small/stars.csv. This file establishes a relationship between the people in people.csv and the movies in movies.csv. Each row is a pair of a person_id value and movie_id value. The first row (ignoring the header), for example, states that the person with id 102 starred in the movie with id 104257. Checking that against people.csv and movies.csv, you’ll find that this line is saying that Kevin Bacon starred in the movie “A Few Good Men.”

Next, take a look at degrees.py. At the top, several data structures are defined to store information from the CSV files. The names dictionary is a way to look up a person by their name: it maps names to a set of corresponding ids (because it’s possible that multiple actors have the same name). The people dictionary maps each person’s id to another dictionary with values for the person’s name, birth year, and the set of all the movies they have starred in. And the movies dictionary maps each movie’s id to another dictionary with values for that movie’s title, release year, and the set of all the movie’s stars. The load_data function loads data from the CSV files into these data structures.

The main function in this program first loads data into memory (the directory from which the data is loaded can be specified by a command-line argument). Then, the function prompts the user to type in two names. The person_id_for_name function retrieves the id for any person (and handles prompting the user to clarify, in the event that multiple people have the same name). The function then calls the shortest_path function to compute the shortest path between the two people, and prints out the path.

run degrees.py to test the program
