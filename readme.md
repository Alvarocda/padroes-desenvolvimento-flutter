![image info](https://lh3.googleusercontent.com/proxy/9YaFtSkgS9y4FNUo3mSKxltZpRNSEkZ1Kop3iitxXIlI8Whbr0RiMBytZHPNK2rE41acKRimJOrgWt7NkTZi_jp5LZC2zw65hyBm1W_epVhG1rlxCxXdoVTRyQ)

# Estrutura de projetos mobile

| Data | Nome | Email |  Ação | 
| --- | --- | --- | --- |
|19/03/2021 | Álvaro Claro | alvarocda@gmail.com | Criação |


1. Estrutura de pasta
   1. Model
      1. usuario.dart
      2. pessoa.dart
      3. suspeito.dart
      4. municipio.dart
      5. estado.dart
   2. Screens
      1. login_screen.dart
      2. principal_screen.dart
      3. duvida_screen.dart
   3. consumers
      1. municipio_consumer.dart
      2. estado_consumer.dart
   4. repositories
      1. pessoa_repository.dart
      2. usuario_repository.dart
      3. suspeito_repository.dart
   5. utils
      2. extensions.dart
      3. connection_utils.dart
   6. abstract
      1. entity_base.dart
      2. connection_base.dart
      3. repository_base.dart
    
2. Explicação das pastas
   1. Model
      - Na pasta model, teremos todos os objetos que serão utilizados  
       no aplicativo, todos os models deverão conter os métodos  
       **fromJson, toJson, toMap e fromMap**  
       e também deverão extender a classe entity_base.dart
   2. Screens
       - Nessa pasta, serão armazenadas todas as telas que serão  
         utilizadas na aplicação, todas as telas deverão ter o 
         nome finalizando com Screen
   3. Consumers
      - Nessa pasta devem ficar as classes responsáveis por consumir recursos externos ao aplicativo, Ex: uma API.  
      Os consumers devem ser responsáveis por interagir com apenas 1 model, Ex:  
        O Consumer de município não pode ter nenhum método para consumir dados do cliente  
        De preferência, o consumer deve retornar um objeto unico ou uma lista conforme  
        o tipo da classe e não o map que veio da API
   4. Repositories
      - Nessa pasta deve ficar as classes responsáveis por ler e escrever 
        informações nos bancos de dados locais dos aplicativos
        Todos os repositories devem implementar a classe abstrata repository_base.dart  
   5. Utils
      - Nessa pasta devem ficar todas as classes que possam facilitar de alguma maneira o desenvolvimento código
    Ex: uma classe especializada em extensões.
   6. Abstract
      - Nessa pasta deve ficar todas as classes abstratas do projeto.
3. Peculiaridades do código
   1. Analysis Options
      - Esse arquivo é serve para criar regras que a IDE irá exigir de todos os  
        programadores que estão trabalhando com esse projeto.  
        Para fazer o analysis_options funcionar, primeiro é necessário adicionar ao projeto  
        uma lib chamada Pendantic (https://pub.dev/packages/pedantic) e então, criar na raiz do projeto  
        um arquivo chamado analysis_options.yaml e dentro desse arquivo, deve ser colocado o texto abaixo  
        ```yaml
         include: package:pedantic/analysis_options.yaml      
         linter:
           rules:
             always_specify_types: true
             always_declare_return_types: true
             omit_local_variable_types: false
             prefer_typing_uninitialized_variables: true
             always_use_package_imports: true
             avoid_types_as_parameter_names: true
             annotate_overrides: true
             empty_constructor_bodies: true
             lines_longer_than_80_chars: false
             prefer_if_null_operators: true
         ```
        Ao fazer isso, perceberá que a IDE irá mostrar vários avisos, todos eles devem ser corrigidos  
        para que o código fique padronizado.
   2. Instalação de libs no pubspec
      - Ao instalar uma nova lib no projeto, você precisa se atentar aos pontos abaixo
         - Não usar ^ na frente da versão, o ^ significa que estamos permitindo que o pacote  
           se atualize automaticamente, e isso não pode acontecer, tirando o ^ nos teremos  
           sempre a certeza de que o pacote esta naquela versão especifica, e caso precisarmos  
           atualizar o pacote, vamos pessoalmente no pub.dev e verificamos o que há de novo  
           e damos uma olhada no repositorio git da lib para verificarmos as issues e ver  
           se não há nenhum bug que pode quebrar tudo ao atualizar o pacote.
         - Ao instalar uma nova lib, coloque em cima dela o link do pacote no pub dev. Ex:
           ```yaml
           # https://pub.dev/packages/pedantic/install
           pedantic: 1.11.0
           # https://pub.dev/packages/firebase
           firebase 9.0.1
            ```
   3. Arquivos, classes e metodos
      1. Todos os arquivos devem ser nomeados utilizando o padrão **snake_case**
      2. O nome das classes deve ser escritos em **UpperCamelCase** e devem ter o mesmo nome do arquivo
      3. O nome dos metodos devem ser escritos em **lowerCamelCase**
   
      
   