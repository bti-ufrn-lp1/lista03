# Lista 3: Programação orientada a objetos em C++
<sub>Última atualização: 22/06/2022</sub>

## Sumário
- [Visão geral e objetivos](#visão-geral-e-objetivos)  
- [Tarefa](#tarefa)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Requisitos](#requisitos)
- [Compilação do programa](#compilação-do-programa)
- [Boas práticas de programação](#boas-práticas-de-programação)
- [Autoria e política de colaboração](#autoria-e-política-de-colaboração)
- [Entrega](#entrega)
- [Avaliação](#avaliação)
- [Dúvidas e informações](#dúvidas-e-informações)

## Visão geral e objetivos
O objetivo desta lista de exercícios é colocar em prática as habilidades de **interpretar especificações de problemas e realizar abstrações** para projetar e implementar um programa na linguagem de programação C++, utilizando o paradigma de **programação orientada a objetos**. Para tanto, esta lista explora elementos fundamentais desse paradigma em C++, como classes, objetos, construtores e destrutores, herança e classes abstratas, além de outros recursos tradicionais da linguagem.

## Tarefa
A tarefa central a ser realizada neste trabalho consiste em projetar e implementar, em C++, um programa para simular o rendimento de contas em um banco. Uma conta define a interface principal para qualquer tipo de conta bancária, possuindo, além das informações comuns a uma conta bancária, as seguintes operações:

| Operação   | Descrição |
| :--------- | :-------- |
| `deposito` | Realiza o depósito de uma quantia na conta, incrementando o seu saldo |
| `saque`    | Realiza o saque de uma quantia na conta, decrementando o seu saldo |
| `saldo`    | Informa o saldo atual da conta |
| `juros`    | Atualiza a taxa de juros a ser aplicada |
| `atualiza` | Aplica os juros sobre a conta, atualizando o saldo |

Utilizando a conta anteriormente definida como base, pode-se definir dois tipos de conta, *conta corrente* e *conta poupança*, cada um com as seguintes características:

| Tipo de conta  | Características |
| :------------- | :-------------- |
| Conta corrente | <ul><li>Possui um atributo menor que zero chamado `limite`, como se fosse o cheque especial. Saques que levem o saldo para abaixo deste valor são recusados. Esta definição não implica que o saldo tenha que estar sempre acima do limite.</li><li>O valor de limite é definido na criação da conta.</li><li>Permite saldo negativo</li><li>A taxa de juros é igual a zero, ou seja, não há rendimento</li> |
| Conta poupança | <ul><li>Possui uma data de aniversário, sendo que só neste dia é que se atualiza juros mensalmente</li><li>Os juros acrescentados são referentes ao saldo após a última computação, o que significa que depósitos intermediários não rendem juros</li><li>Admite apenas saldo maior ou igual a zero</li>
  
Além de permitir a criação e operação sobre contas correntes e contas poupança, o programa principal deve apresentar uma opção de simular uma data futura, através do qual deverá ser informada uma data no tempo a ser considerada como data atual. Isso fará com que todas as contas sejam devidamente atualizadas, levando em consideração a lógica interna de atualização de cada tipo de conta.

## Estrutura do projeto

Primando pela modularização, a definição e a implementação das classes deverão ser separadas em arquivos cabeçalho (`.h`) e de corpo (`cpp`). **Necessariamente**, os arquivos de cabeçalho deverão estar presentes no diretório `include` e os arquivos de corpo no diretório `src`. Além desses arquivos, o arquivo `main.cpp` correspondente à implementação da função principal do programa deverá **necessariamente** estar também presente no diretório `src`. Dessa forma, os arquivos deste projeto deverão estar organizados de acordo com a seguinte estrutura:

```
+─lista03             ---> Nome do diretório do projeto
  ├─── CMakeLists.txt ---> Script de configuração do cmake
  ├─── build          ---> Diretório onde os arquivos executáveis serão gerados
  ├─── include        ---> Diretório que contém os arquivos cabeçalho (.h)
  └─── src            ---> Diretório que contém os arquivos corpo (.cpp)
       └─── main.cpp  ---> Arquivo fonte contendo a implementação da função principal do programa
```

Nesta atividade, o *script* de configuração do `cmake` `CMakeLists.txt` **não está sendo fornecido de antemão**, ou seja, é de responsabilidade da equipe criar esse arquivo por conta própria. Todavia, sugere-se utilizar como base *scripts* de configuração de projetos anteriores feitos na disciplina, como neste [exemplo](https://github.com/bti-ufrn-lp1/dnaprofiler/blob/master/CMakeLists.txt). **O nome do programa executável a ser gerado deverá ser necessariamente `banco`.**

## Requisitos
Para a realização desta atividade, os seguintes elementos devem estar devidamente instalados no ambiente de desenvolvimento:

- [Git](https://git-scm.com), como sistema de controle de versões
- [*GNU Compiler Collection*](https://gcc.gnu.org) (a qual inclui o compilador `g++`), [`clang`](https://clang.llvm.org/) ou qualquer outro compilador para a linguagem C++, e;
- [`cmake`](https://cmake.org/), para gerar *makefiles* automaticamente e de forma otimizada para o projeto.

## Compilação do programa

Os seguintes comandos devem ser executados no terminal do sistema operacional para compilar o programa:

```bash
mkdir build
cd build
cmake ..
cmake --build .
```

Com isso, o executável `banco` resultante da compilação do programa será gerado dentro do diretório `build`.

## Conhecimentos necessários

- Entrada e saída padrão
- Classes e objetos
- Visibilidade de membros de classes
- Herança
- Classes abstratas e métodos virtuais
- *Containers* da [*Standard Template Library* (STL)](https://www.cplusplus.com/reference/stl/)

## Boas práticas de programação
Boas práticas de programação deverão ser constantemente aplicadas no desenvolvimento do programa em questão, o qual deverá ser codificado de forma legível (com indentação de código fonte, nomes consistentes, etc.) e documentado adequadamente na forma de comentários. O código fonte deverá ainda ser anotado para dar suporte à geração automática de documentação utilizando a ferramenta [Doxygen](https://www.doxygen.nl/). O documento de apoio disponível neste [*link*](https://drive.google.com/file/d/1YA1KxASCNY3B8APowD2V0sL-kAso9g86/view) contém algumas instruções acerca do padrão de documentação e uso do Doxygen.

O programa deverá ser desenvolvido com qualidade, garantindo que ele funcione de forma correta e eficiente. Deve-se também pensar nas possíveis entradas que poderão ser utilizadas para testar apropriadamente o programa, além de serem tratadas adequadamente possíveis entradas consideradas inválidas.

## Autoria e política de colaboração
Este trabalho poderá ser realizado individualmente ou em equipe composta de dois estudantes, sendo importante, neste último caso, dividir as tarefas igualmente entre os integrantes da equipe. O arquivo [`author.md`](author.md) presente no repositório deverá ser editado preenchendo as informações de identificação dos integrantes da equipe, na seção [Informações de Autoria](author.md#identificação-de-autoria). 

O trabalho em cooperação entre estudantes da mesma turma ou de outras turmas é estimulado, sendo admissível a discussão de ideias e estratégias. Contudo, tal interação não deve ser entendida como permissão para utilização de (parte de) código fonte de colegas, o que pode caracterizar situação de plágio. Trabalhos copiados no todo ou em parte de outros colegas ou da Internet serão anulados e receberão nota zero.

## Entrega
O sistema de controle de versões [Git](https://git-scm.com) e o serviço de hospedagem de repositórios [GitHub](https://git-scm.com) serão utilizados para possibilitar a entrega da implementação realizada. Para possibilitar a associação de repositórios Git para cada equipe e reuni-los sob uma mesma infraestrutura, foi criada uma atividade (*assignment*) no GitHub Classroom. Cada integrante de equipe deverá acessar este [*link*](https://classroom.github.com/a/nt2leRbI), aceitar o convite para ingressar no GitHub Classroom e finalmente seguir as instruções em tela para acessar a atividade e ingressar em uma equipe existente ou criar outra. Este [vídeo](https://youtu.be/ObaFRGp_Eko) demonstra como ocorre esse processo.

No momento de criação de uma equipe, o GitHub Classroom cria um repositório Git privado acessível unicamente pelos integrantes da equipe e pelo docente, sob a organização [`bti-ufrn-lp1`](https://github.com/bti-ufrn-lp1). Esse repositório segue a mesma estrutura de diretórios presentes neste repositório, o qual serve de *template*. Todos os arquivos deverão constar no repositório obedecendo **estritamente** a divisão em diretórios. A fim de garantir a boa manutenção do repositório, deve-se ainda configurar corretamente o arquivo `.gitignore` para desconsiderar arquivos que não devam ser versionados, a exemplo do diretório `build` e seus arquivos, resultantes do processo de compilação com o `cmake`.

A implementação do programa proposto neste trabalho deverá ser realizada **até as 23h59 do dia 27 de junho de 2022** no respectivo repositório Git da equipe. Para fins de registro, o endereço do repositório também deverá ser enviado através da opção *Tarefas* na Turma Virtual do SIGAA. **Não serão aceitos envios por outros meios ou repositórios que não sejam os descritos nesta especificação.**

## Avaliação

A avaliação da implementação deste trabalho contabilizará nota de até 10,0 pontos. A implementação será avaliada de acordo com os seguintes critérios:

- utilização correta dos recursos providos pela linguagem de programação C++;
- modelagem adequada de classes e utilização correta de objetos, inclusive via herança;
- corretude da execução do programa implementado, que deve apresentar saída em conformidade com a especificação e as entradas de dados fornecidas;
- aplicação de boas práticas de programação, incluindo legibilidade, organização e documentação de código fonte, e;
- correta utilização do repositório Git, no qual deverá ser registrado todo o histórico da implementação por meio de *commits*.

O não cumprimento de algum dos critérios de avaliação especificados poderá resultar nos seguintes decréscimos, aplicados sobre a nota obtida até então na avaliação da implementação:

| Falta | Decréscimo |
| :--- | ---: |
| Falta de comentários no código fonte e/ou de documentação gerada com Doxygen | -10% |
| Uso inadequado de controle de versão com Git | -20% |
| Falta de especificação ou especificação incorreta da autoria do trabalho (arquivo [`author.md`](author.md)) | -20% |
| Implementação na linguagem C ou resultante de mistura entre as linguagens C e C++ | -30% |
| Código fonte com legibilidade prejudicada (por exemplo, com identação ou nomenclatura inadequada) | -40% |
| Programa compila com mensagens de aviso (*warnings*) | -50% |
| Modelagem orientada a objetos inadequada | -50% |
| Programa apresenta erros de compilação, não executa ou apresenta saída incorreta | -70% |
| Plagiarismo | -100% |

## Dúvidas e informações

Caso haja qualquer dúvida, questionamento ou necessidade de informação adicional, é possível:

- enviar *e-mail* para o endereço everton.cavalcante@ufrn.br;
- enviar mensagem privada diretamente ao docente, utilizando o servidor Discord;
- enviar mensagem no canal de texto `#geral-dim0120-t02`, especificamente associado à turma no servidor Discord;
- enviar mensagem no canal de texto `#duvidas` no servidor Discord, comum a todas as turmas da disciplina;
- realizar encontros síncronos presenciais, no horário e local de aula;
- agendar encontros síncronos por videoconferência, ou;
- agendar encontros síncronos pelo canal de áudio `Fale com Prof. Everton` no servidor Discord.
