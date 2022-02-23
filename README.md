# Criando um Banco de Dados no Autonomous Databases
O Oracle Autonomous Database permite criar um banco de dados no Oracle Cloud. Esse texto irá orientar, passo a passo, como criar um novo banco de dados autônomo (Autonomous Data Warehouse - ADW e Autonomous Transaction Processing - ATP). Vale ressaltar que, embora esse tutorial crie um ADW, as etapas são as mesmas para um banco de dados ATP.

> **OBS:** Esse tutorial foi traduzido do inglês e adaptado a partir da Oracle. Você pode acessar o site do tutorial no original  [aqui](https://oracle.github.io/learning-library/data-management-library/autonomous-database/shared/adb-quickstart-workshop/freetier/?lab=adb-provision-conditional)

## Definindo ADW ou ATP

1. Faça login na Oracle.

2. Clique no **painel de serviços do Oracle** localizado no canto superior esquerdo do site que mostra as opções de navegação de nível superior.

![Alt text: Print do painel de serviços da Oracle Cloud na aba Home com um quadrado,de contorno vermelho e sem preenchimento, destacando um ícone com três linhas horizontais, uma em cima da outra e com uma seta vermelha apontando para ele. Esse ícone dá acesso ao painel de serviços.](https://i.imgur.com/5KT88lq.png)
 
3. Clique em **Oracle Database** e depois em **Autonomous Data Warehouse**

![Alt text: Print do painel de serviços da Oracle Cloud na aba Oracle Database com um retângulo, de contorno vermelho sem preenchimento, destacando a opção Oracle Database no canto esquerdo da imagem. Dentro da aba Oracle Database, a opção Autonomous Data Warehouse também está destacada com um retângulo de contorno vermelho e sem preenchimento.](https://i.imgur.com/D2fl2lA.png)

> Nota: Para criar um ATP clique em **Autonomous Transaction Processing**

4. Na conta mostrada abaixo contém dois bancos de dados já criados que terão seus dados preservados. Se não existirem bancos a sua conta terá a frase *No items* na tabela de Display do Autonomous Database. Certifique-se que em **List Scope**, no canto esquerdo do site, a opção **compartment** está definida com o compartimento adequado.

![Alt text: Print da aba Autonomous Database contendo o nome do compartment e os Databases borrados. No canto inferior esquerdo da imagem abaixo, da seção List Scope, a opção Compartment está destacada com um retângulo de contorno vermelho sem preenchimento e o conteúdo selecionado nessa opção está borrado.](https://i.imgur.com/elnLnWf.png)

> Nota: Evite o uso do `ManagedCompartmentforPaaS` nessa opção, pois ele é um padrão Oracle usado para *Oracle Platform Services*.

5. Defina os valores na aba **Filters**. Nesse tutorial serão definidos ***Data Warehouse* em Workload Type** e ***Any state* em State**.

![Alt text: Print da aba Autonomous Database contendo o nome do compartment e os Databases borrados. No canto inferior esquerdo da imagem abaixo da seção Filters, a opção Workload Type que está destacada com um retângulo em vermelho e tem a opção Data Warehouse selecionada, bem como a opção State que está destacada com um retângulo de contorno vermelho sem preenchimento e tem a opção Any state selecionada.](https://i.imgur.com/rCpDZWy.png)

6. Se estiver usando uma conta **Free Trial** ou **Always Free** e quiser usar os **Always Free Resources** (ou recursos sempre gratuitos) do Autonomous Database, será necessário estar em uma região onde esse recurso esteja disponível. Você pode ver sua região padrão atual no canto superior direito da página.

![Alt text: Print da aba Autonomous Database contendo o nome do compartment borrado, a opção da região US East (Ashbum) destacado com um retângulo de contorno vermelho sem preenchimento.](https://i.imgur.com/NeMqmSt.png)

## Crie uma instância do Oracle Autonomous Database

1. Clique no botão **Create Autonomous Database** para iniciar o processo de criação da instância.

![Alt text: Print da aba Autonomous Database contendo o nome do compartment e os Databases borrados. O botão Create Autonomous Database está destacado com um retângulo de contorno vermelho sem preenchimento](https://i.imgur.com/vVC3yt0.png)

2. Ao clicar no botão, você será levado para a aba **Create Autonomous Database** para que possa especificar os dados da nova instância.

![Alt text: Print da aba Create Autonomous Database do Oracle.](https://i.imgur.com/fRXzLIV.png)

3. Especifique em *Provide basic information for the Autonomous Database* informações básicas para o banco de dados autônomo:
    * **Compartiment** - o seu compartimento padrão.
    * **Display name** - insira um nome memorável para o banco de dados para fins de exibição. Nesse tutorial, usaremos ADW Tutorial.
    * **Database name** - A palavra escolhida deve ser composta por apenas letras e números, na qual deve começar por uma letra. O comprimento máximo é de 14 caracteres. Para este tutorial, usaremos dbADW.


![Alt text: Print da aba Create Autonomous Database do Oracle. Na seção Provide basic information for the Autonomous Database, o dado contido em Compartment está borrado. A opção Display name está destacada com um retângulo de contorno vermelho sem preenchimento e tem o nome ADW Tutorial contido na caixa de diálogo. Já a opção Database name está destacada com um retângulo de contorno vermelho sem preenchimento e tem a o nome dbADW contido na caixa de diálogo](https://i.imgur.com/3ev0aZa.png)

4. Escolha um tipo de **workload type** e **deployment type** para seu banco de dados nas opções:
    * **Data Warehouse** - para este tutorial, escolhemos Data Warehouse como o tipo de workload type por já ter sido a opção indicada em passos anteriores.
    * **Shared Infrastructure** - escolhemos Shared Infrastructure como o tipo deployment type que vai rodar o Database em uma estrutura de compartilhamento.

![Alt text: Print da aba Create Autonomous Database do Oracle. Entre a seção Provide basic information for the Autonomous Database e Configure the database, onde a opção Data Warehouse está selecionada e destacada com um retângulo de contorno vermelho sem preenchimento. Mais abaixo, temos a opção Shared Infrastructure que  também está selecionada e destacada com um retângulo de contorno vermelho sem preenchimento](https://i.imgur.com/Xnt6wSD.png)

5. Na seção *Configure the database*:
    * **Always Free** - se sua conta de nuvem for uma conta Always Free, você pode selecionar esta opção para criar um banco de dados autônomo sempre gratuito. Esse tipo de banco de dados vem com 1 CPU e 20 GB de armazenamento. Neste tutorial, não será marcada a opção a Always Free.
    * **Choose database version** - selecione uma versão do banco de dados entre as versões disponíveis. Vamos utilizar a 19c.
    * **OCPU count** - Número de CPUs para seu serviço. Para este tutorial, especifique 1 CPU. Se escolher um banco de dados Always Free, ele já vem com 1 CPU selecionada.
    * **Storage (TB)** - selecione sua capacidade de armazenamento em terabytes (TB). Especificaremos 1 TB de armazenamento. Mas, se você escolher um banco de dados Always Free, ele já vem com 20 GB de armazenamento.
    * **OCPU auto scaling** - mantenha o auto Scaling habilitado para permitir que o sistema use automaticamente até três vezes mais recursos de CPU para atender à demanda de carga de trabalho. Caso a opção Always Free esteja habilitada, essa opção não estará disponível para ser selecionada.
    * **New Database Preview** - Se uma caixa de seleção com nome New Database Preview estiver disponível para visualizar uma nova versão do banco de dados, NÃO a marque.

![Alt text: Print da aba Create Autonomous Database do Oracle. Na seção Configure the database, a opção Always Free não está selecionada e é destacada com um retângulo de contorno vermelho sem preenchimento. Mais abaixo, temos a opção Choose database version também destacada com um retângulo de contorno vermelho sem preenchimento.](https://i.imgur.com/T47RGda.png)

> Nota: Não é possível aumentar/diminuir as configurações na versão Always Free do banco.

6. Na seção *Create administrator credentials* você vai definir as credenciais para acesso do seu banco de dados:
    * **Password** - especifique a senha para o usuário ADMIN da instância de serviço. A senha deve atender aos seguintes requisitos:
        * A senha deve ter entre 12 e 30 caracteres e deve incluir pelo menos uma letra maiúscula, uma letra minúscula e um caractere numérico.
        * A senha não pode conter o nome de usuário.
        * A senha não pode conter o caractere de aspas duplas (").
        * A senha deve ser diferente das últimas 4 senhas usadas.
        * A senha não deve ser a mesma que você definiu há menos de 24 horas.
    * **Confirm Password** - digite novamente a senha para confirmá-la. Anote-a.

![Alt text: Print da aba Create Autonomous Database do Oracle. Na seção Create administrator credentials, as opções Password e Confirm Password estão preenchidas com uma senha em pontos para visualização. Existem duas setas vermelhas de mesma origem que apontam para Password e Confirm Password.](https://i.imgur.com/IHURlsI.png)

7. Na seção *Choose network access*:
    * Para este tutorial, marque a opção **Secure access from everywhere**.
    * Se deseja restringir o acesso a endereços IP e VCNs definidos, selecione **Secure access from allowed IPs and VCNs only**. Você pode controlar e restringir o acesso ao seu Autonomous Database definindo listas de controle de acesso à rede (ACLs). Também  pode selecionar entre 4 tipos de notação IP: IP Address (Endereço IP), CIDR Block, Virtual Cloud Network (Rede Virtual na Nuvem), Virtual Cloud Network OCID (Rede Virtual na Nuvem OCID).
    * Se quiser um endpoint privado, para habilitar o tráfego somente da VCN que você especificar e para bloquear o acesso ao banco de dados de todos os IPs ou VCNs públicos, selecione **Private endpoint access only** na seção *Choose network access area*.
    * Se selecionar **Secure access from allowed IPs and VCNs only** ou **Private endpoint access only**, você poderá usar a caixa de seleção para exigir autenticação mútua TLS (mTLS) para autenticar conexões com seu banco de dados. Se não marcar essa caixa de seleção, TLS ou mTLS podem ser usados.


![Alt text: Print da aba Create Autonomous Database do Oracle. Na seção Choose network access, a opção Secure access from everywhere está selecionada e destacada com um retângulo de contorno vermelho sem preenchimento](https://i.imgur.com/2VdSzLL.png)

8. Na seção *Choose a license type*:
    * **Bring Your Own License (BYOL)** - selecione essa opção quando sua organização tiver licenças de banco de dados existentes.
    * **License Included** - neste tutorial, essa opção será selecionada. Faça isso quando quiser assinar novas licenças de software de banco de dados e o serviço de nuvem de banco de dados.


![Alt text: Print da aba Create Autonomous Database do Oracle. Na seção Choose a license type, a opção License Included está selecionada e destacada com um retângulo de contorno vermelho sem preenchimento](https://i.imgur.com/R1MTrrw.png)

9. Clique no botão **Create Autonomous Database** no canto inferior esquerdo para criar seu banco de dados.

![Alt text: Print do fim da aba Create Autonomous Database do Oracle. Nela temos  o botão Create Autonomous Database destacado com um retângulo de contorno vermelho sem preenchimento ao redor dele e uma seta vermelha na vertical apontada para o mesmo botão](https://i.imgur.com/1wqB3JN.png)

Por fim, você será direcionado para o seu novo banco de dados. Depois de alguns segundos, ele estará disponível para ser utilizado!
