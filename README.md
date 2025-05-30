# Projeto de Cibersegurança: Phishing para captura de senhas do Facebook

Este projeto faz parte de um curso de cibersegurança e tem como objetivo demonstrar e entender o funcionamento de um ataque de Phishing, especificamente um Credential Harvester (coleta de credenciais), utilizando a ferramenta Social-Engineer Toolkit (SEToolkit) no Kali Linux. O ataque simula a criação de uma página falsa do Facebook para enganar usuários e capturar suas credenciais de login.

**Disclaimer:** Este projeto é apenas para fins educacionais e de demonstração. A utilização indevida das técnicas aqui apresentadas é ilegal e antiética.

## Ferramentas Utilizadas

* **Kali Linux:** Distribuição Linux focada em segurança e pentest.
* **Social-Engineer Toolkit (SEToolkit):** Ferramenta de engenharia social que permite a criação de diversos tipos de ataques, incluindo o Credential Harvester.

## Cenário do Ataque (Exemplo)

Neste projeto, simulamos a criação de uma página falsa de login do Facebook para demonstrar como as credenciais podem ser capturadas por meio de um ataque de phishing.

## Passo a Passo

A seguir, descrevo os passos executados, ilustrados pelas imagens fornecidas no diretório `/images`:

### 1. Acesso ao SEToolkit

Para iniciar o SEToolkit, primeiro obtemos privilégios de root e depois executamos a ferramenta.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_001.jpg)

- Mostra o terminal do Kali Linux. Entramos como usuário comum e então usamos `sudo su -` para obter privilégios de root. Em seguida, executamos o comando `setoolkit`.

### 2. Menu Principal do SEToolkit

Após a execução, o SEToolkit apresenta seu menu principal.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_002.jpg)

- Exibe o menu principal do SEToolkit (versão 8.0.3, codinome 'Maverick'). Optamos pela opção `1` para "Social-Engineering Attacks" (Ataques de Engenharia Social).

### 3. Opções de Ataques de Engenharia Social

Dentro das opções de ataques de engenharia social, escolhemos a categoria para a qual queremos direcionar nosso ataque.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_003.jpg)

- Mostra o submenu de "Social-Engineering Attacks". Selecionamos a opção `2` para "Website Attack Vectors" (Vetores de Ataque a Websites).

### 4. Métodos de Ataque Web

O SEToolkit oferece diversos métodos para ataques baseados em web. Para o Credential Harvester, selecionamos a opção apropriada.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_004.jpg)

- Exibe os diferentes métodos de ataque web. Escolhemos a opção `3` para "Credential Harvester Attack Method" (Método de Ataque de Coleta de Credenciais).

### 5. Configuração do Credential Harvester

Nesta etapa, definimos como o ataque de coleta de credenciais será realizado.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_005.jpg)

- Apresenta as opções para o método Credential Harvester. Optamos pela opção `2` para "Site Cloner" (Clonador de Site), que nos permite clonar uma página web existente.

### 6. Clonando a Página do Facebook

Aqui, especificamos o IP do atacante (Kali Linux) e a URL do site a ser clonado.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_006.jpg 
e 
![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_007.jpg)

- Nestas imagens, o SEToolkit nos pede o IP para o POST back (neste caso, `192.168.1.7`, que seria o IP do nosso Kali Linux) e a URL para ser clonada. Inserimos `http://www.facebook.com`. O SEToolkit então inicia o processo de clonagem da página de login do Facebook (`https://login.facebook.com/login.php`). A ferramenta informa que o Credential Harvester está rodando na porta 80 e que as informações serão exibidas conforme forem recebidas.

### 7. Simulação do Ataque e Captura de Credenciais

Com a página falsa no ar, simulamos um usuário inserindo suas credenciais.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_008.jpg)

- Esta imagem mostra duas janelas:
    * À esquerda, o terminal do Kali Linux exibindo o output do SEToolkit, aguardando conexões e credenciais.
    * À direita, um navegador web exibindo a página clonada do Facebook (observe a URL `192.168.1.7` no navegador, indicando que é a página servida pelo nosso Kali). Um usuário de teste (`usuarioteste@gmail.com`) e uma senha (`********`) são inseridos no formulário de login falso.

### 8. Visualizando as Credenciais Coletadas

Após o usuário "tentar" fazer login na página falsa, as credenciais são capturadas pelo SEToolkit.

![image](https://github.com/ronaldoramos85/cibersecurity-desafio-phishing/blob/master/images/setoolkit_009.jpg)

- Esta imagem exibe o resultado do ataque.
    * Na janela da esquerda, o SEToolkit mostra os dados capturados, incluindo o `email` (usuarioteste@gmail.com) e a `pass` (senha digitada), confirmando a coleta de credenciais.
    * Na janela da direita, é possível ver que o SEToolkit gerou um relatório do ataque em formato XML, localizado em `/root/.set/reports/2025-05-27-20-17-59.91430.xml`.

## Conclusão

Este projeto demonstrou como um ataque de Phishing para Credential Harvester pode ser realizado usando o SEToolkit, clonando uma página web (neste caso, o Facebook) e capturando informações de login. A conscientização sobre essas técnicas é fundamental para o desenvolvimento de defesas eficazes contra ataques de engenharia social.

## Como Executar (Apenas para Fins de Estudo)

1.  Certifique-se de ter o Kali Linux instalado.
2.  Abra um terminal e obtenha privilégios de root: `sudo su -`
3.  Execute o SEToolkit: `setoolkit`
4.  Siga as opções do menu conforme descrito no passo a passo acima (1 -> 2 -> 3 -> 2).
5.  Quando solicitado, forneça o IP do seu Kali Linux e a URL do site que deseja clonar (por exemplo, `http://www.facebook.com`).
6.  Acesse a página clonada a partir de outra máquina na mesma rede ou de uma VM separada (usando o IP do Kali Linux no navegador).
7.  Após inserir credenciais na página clonada, o SEToolkit exibirá as informações capturadas no terminal.

Lembre-se: Este procedimento deve ser realizado apenas em ambientes controlados e com permissão explícita.
