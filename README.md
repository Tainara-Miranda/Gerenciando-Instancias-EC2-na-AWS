# Gerenciando-Instancias-EC2-na-AWS
Desafio do Bootcamp Code Girls 2025 da DIO

Este desafio consiste em criar uma arquitetura, realizada pelo Drawio, para praticar conceitos fundamentais de gerenciamento de instâncias EC2 na AWS com foco em criação e utilização de AMIs (Amazon Machine Images) e Snapshots EBS.

Para este desafio, pensou-se na seguinte case: 🥣 Eu sou uma confeiteira e quero um site que sirva como um portfólio para o meu trabalho. Nesse site terá algumas páginas estáticas (Início, Sobre, Contato) e uma página dinâmica (sempre haverá alterações) sendo a galeria com meus produtos. Dentro deste site há também como um possível cliente preencher um formulário para que possam entrar em contato comigo. 

‼️Vamos análisar como a arquitetura funciona:

⭐ Site Principal (EC2 e EBS) 

⭐ Galeria com os Produtos (S3) 

⭐ O formulário de Contato (Lambda) 

------------------------------------------------------

**Site Principal (EC2 e EBS)**

O EC2 é o meu servidor web principal, onde irei hospedar as páginas estáticas do site. Já o EBS é o disco rígido do servidor EC2, onde todos os arquivos estáticos do site e o software do servidor web são armazenados. 

**Galeria com os Produtos (S3)**

Armazenar todas as fotos dos meus produtos no EBS pode tornaro sistema lento, a solução é utilizar o S3. Cada foto será carregada diretamente para um bucket S3 e no código HTML da galeria será inserido um link para a foto no S3, assim, quando um visitante clicar para ver a foto em um tamanho maior, a requisão será feita diretamente ao S3, otimizando o serviço ao se tratar de arquivos grande, reduzindo custos e aliviando a carga do EC2.

**O formulário de Contato (Lambda)**

Quando um visitando preencher os campos do formulário (Ex: Nome, e-mail, mensagem), e clicar em "Enviar", podemos ter um código JavaSripit na página que fará uma chamada de API para o Lambda. Assim, o Lambda é ativado lendo todos os dados enviados pelo formulário. A função pode, por exemplo, salvar a mensagem em um arquivo de texto no bucket S3 ou me enviar um e-mail e assim que a tarefa é concluída, o Lambda pode retornar uma resposta de "Sucesso" para a página, confirmando o envio.

------------------------------------------------------

💁 O case apresentado pode ser de certa forma simples, apenas para aplicar os conceitos e formar uma arquitetura, mas é o suficiente para entendermos os conceitos e funcionamento das instâncias EC2 na AWS e também o armazenamento por EBS e S3, ainda encaixando a função LAMBDA.
