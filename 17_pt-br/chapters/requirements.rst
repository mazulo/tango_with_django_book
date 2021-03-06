.. _requirements-label:

Preparando-se para o Tango
==========================
Vamos começar a instalação! Para dançar com Django, você precisará garantir que você tem tudo que você precisa instalado no seu computador e que você tem um bom entendimento do seu ambiente de desenvolvimento. Este capítulo leva você através do que você precisa e o que tem que saber.

Para este tutorial, você necessitará das seguintes peças-chave de software.

* Python versão 2.7.5+
* Django versão 1.7

Como Django é um framework para aplicações web escrito na linguagem de programação Python, você vai ser obrigado a ter um conhecimento prático de Python. Se você não tiver usando Python antes ou você deseja simplesmente aperfeiçoar suas habilidades, então nós recomendamos fortemente que você confira e trabalhe em um ou mais dos seguintes guias.

* **Um rápido tutorial** - Aprenda Python em 10 minutos, por Stavros, http://www.korokithakis.net/tutorials/.
* **O Tutorial Oficial de Python** em http://docs.python.org/2/tutorial/.
* **Um brilhante livro**: Pense Python: Como pensar como um Cientista da Computação, por Allen B. Downey, disponível online em http://www.greenteapress.com/thinkpython/.
* **Um curso online incrível**: Aprenda a programar, por Jennifer Campbell e Paul Gries em https://www.coursera.org/course/programming1.

Usando o Terminal
-----------------
A fim de criar seu ambiente, aprender como usar o *Interpretador em Linha de Comando (CLI)* fornecido pelo seu sistema operacional é realmente importante. Ao longo do curso deste tutorial, você estará interagindo com o CLI rotineiramente. Se você já está familiarizado com o uso da interface da linha de comando, você pode pular diretamente para a seção :ref:`Instalando o Software <installing-software>`.

Todos os Sistemas Operacionais baseados no UNIX usam um `terminal <http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html>`_ de aparência semelhante. Descendentes, derivador e clones do UNIX incluindo o `Apple's OS X <http://en.wikipedia.org/wiki/OS_X>`_ e as `muitas distribuições Linux <pt.wikipedia.org/wiki/Lista_de_distribuições_de_Linux>`_ disponíveis atualmente. Todos esses sistemas operacionais contêm um conjunto básico de comandos que ajudam você a navegar através do seu sistemas de arquivos e rodar programas, tudo sem a necessidade de qualquer interface gráfica. Esta seção fornece os comandos que você deve se familiarizar.

.. note:: Este tutorial é focado para usuários de sistemas operacionais baseados em UNIX ou dericados. Embora Python e Django possam rodar em um ambiente Windows, muitos dos comandos que nós usamos neste livro são paa terminais baseados em UNIX. Esses comandos podem, entretanto, serem repetidos no Windows usando a interface gráfica do usuário, `usando o comando relativo em um tela de comando Windows <http://www.ai.uga.edu/mc/winforunix.html>`_, ou usando `Windows PowerShell <http://technet.microsoft.com/en-us/library/bb978526.aspx>`_ que fornece um CLI similar ao terminal UNIX.

Após abrir uma nova instância do terminal, você será tipicamente apresentado com algo como:

.. code-block:: guess
	
	sibu:~ leif$

Isto é chamado de *prompt*, e indica quando o sistema está esperando para executar cada comando seu. O prompt que você vê varia dependendo do sistema operacional que você está usando, mas todos geralmente são muito parecidos. No exemplo acima, existem três peças chaves de informação para observar:

* seu nome de usuário (username) e o nome do computador (username do ``leif`` e o nome do computador ``sibu``);
* seu *diretório atual de trabalho* (o til, ou ``~``); e
* o privilégio da sua conta de usuário (o sinal de dólar, ou ``$``).

O sinal de dólar (``$``) geralmente indica que o usuário é uma conta de usuário padrão. Por outro lado, um jogo da velha (``#``) pode ser usado para significar que o usuário logado tem `privilégios root <http://pt.wikipedia.org/wiki/Superusu%C3%A1rio>`_. Seja qual for o símbolo, é usado para significar que o computador está esperando sua entrada.

Abra uma janela do terminal e veja como seu prompt parece.

Quando você usar o terminal, é importante saber onde você está no sistema de arquivos. Para descobrir onde você está, você pode executar o comando ``pwd``. Isto mostraá seu atual diretório. Por exemplo, cheque a interação no terminal abaixo.

.. code-block:: guess
	
	Last login: Mon Sep 23 11:35:44 on ttys003
	sibu:~ leif$ pwd
	/Users/leif
	sibu:~ leif$

Você pode ver que o diretório atual neste exemplo é: ``Users/leif``.

Você também notará que o prompt indica que meu diretório atual é ~. Isto é porque o til (``~``) representa seu *diretócial inicial* (que chamaremos de home). O diretório base em qualquer sistema de arquivos baseados em UNIX é o *diretório raiz* (que chamaremos de root). O caminho do diretório raiz é denoado por uma simples barra (``/``).

Se você não está no seu diretório home você pode mudar o diretório (``cd``) para ele ao executar o seguinte comando.

.. code-block:: guess
	
	$ cd ~

Vamos criar um diretório chamado ``code``. Para fazer isso, use o comando que cria diretórios (``mkdir``), como mostrado abaixo.

.. code-block:: guess
	
	$ mkdir code

Para mover para entrar no diretório ``code`` recentemente criado, digite ``cd code``. Se você agora checar seu diretório de trabalho atual, você notará que você estará em ``~/code/``. Isto Isto pode também ser refletido pelo seu prompt. Note no exemplo abaixo que o diretório de trabalho atual está impresso depois do nome do computador ``sibu``.

.. note:: Sempre que nos referirmos para ``<workspace>``, nós estaremos nos referindo para seu diretório ``code``.

.. code-block:: guess
	
	sibu:~ leif$ mkdir code
	sibu:~ leif$ cd code
	sibu:code leif$ 
	sibu:code leif$ pwd
	/Users/leif/code

Para listar os arquivos que estão no diretório, você pode executar o comando ``ls``. Você pode também ver arquivos ou diretórios ocultos - if você tiver algum - você pode executar o comando ``ls -a``, onde ``a`` significa *all*. Se você voltar para o diretório home (``cd ~``) e então executar ``ls``, você verá que tem algo chamado ``code`` no seu diretório home.

Para saber um pouco mais sobre o que está no seu diretório, execute um ``ls -l``. Isto fornecerá uma *listagem* mais detalhada dos seus arquivos e se é um diretório ou não (denotado por um ``d`` no começo da linha).

.. code-block:: guess
	
	sibu:~ leif$ cd ~ 
	sibu:~ leif$ ls -l 
	
	drwxr-xr-x   36 leif  staff    1224 23 Sep 10:42 code

A saída também contêm informações sobre `permissões associadas ao diretório <http://www.infowester.com/linuxpermissoes.php>`_, quem criou (``leif``), o grupo (``staff``), o tamanho, a data/hora em que o arquivo foi modificado, e, claro, o nome.

Você também pode achar útil ser capaz de editar arquivos dentro do seu terminal. Existem muitos editores que você pode usar - alguns dos quais pode já estar instalado no seu computador. O editor `nano <http://www.nano-editor.org/>`_ por exemplo, é um editor simples, ao contrário do `vi <http://pt.wikipedia.org/wiki/Vi>`_ que pode levar algum tempo para aprender. Abaixo está uma lista de comandos UNIX costumeiramente usados que você achará útil.

Comandos Básicos
****************
Todos os sistemas operacionais baseados em UNIX vêm com uma série de comandos embutidos - com o foco maior exclusivamente para gerenciamento de arquivos. Os comandos que você usará mais frequentemente estão listados abaixo, cada um com uma pequena explicação sobre o que eles fazem e como usá-los.

- ``pwd``: *Imprime* na tela do seu terminal seu diretório de trabalho atual. O caminho completo de onde você está é mostrado.
- ``ls``: Mostra no terminal uma lista dos arquivos no seu diretório atual. Por padrão, você não pode ver os tamanhos dos arqvuiso - isto pode ser conseguido ao adicionar ``-lh`` ao ``ls``, dando o comando ``ls -lh``.
- ``cd``: Em conjunto com um caminho, permite você *mudar* seu *diretório* de trabalho. Por exemplo, o comando ``cd /home/leif`` muda o diretório de trabalho atual para ``/home/leif/``. Você pode também subir um nível de diretório sem ter que fornecer o `caminho absoluto <http://www.uvsc.edu/disted/decourses/dgm/2120/IN/steinja/lessons/06/06_04.html>`_ ao usar dois pontos, por exemplo, ``cd ..``.
- ``cp``: copia arquivos e/ou diretório. Você precisa fornecer o *original* e o *destino*. Por exemplo, para fazer uma cópia de um arquivo ``input.py`` no mesmo diretório, você executaria o comando ``cp input.py input_backup.py``.

- ``mv``: Move arquivos ou diretórios. Você precisa fornecer o *original* e o *destino*. Este comando é também usado para renomear arquivos. Por exemplo, para renomear ``numbers.txt`` para ``letters.txt``, execute o comando ``mv numbers.txt letters.txt``. Para mover um arquivo para um diretório diferente, você iria fornecer ou um caminho absoluto ou relativo como parte do destino - algo como isto ``mv numbers.txt /home/david/numbers.txt``.

- ``mkdir``: Cria um diretório no seu diretório atual. Você precisa fornece um nome para o novo diretório depois do comando ``mkdir``. Por exemplo, se o seu diretório atual era ``/home/david/`` e você executou ``mkdir music``, você deverá então ter um diretório ``/home/david/music``. Você precisará, em seguida, executar um ``cd`` para entrar no diretório recentemente criado.

- ``rm``: Abreviação para *remoção*, este comando remove ou deleta arquivos do seu sistema de arquivos. Você precisa fornecer o(s) nome(s) do(s) arquivo(s) que você deseja remover. Após executar um comando ``rm``, você será perguntado se você deseja deletar os arquivos selecionados. Você também pode remover diretórios `usando a opção recursiva <http://www.computerhope.com/issues/ch000798.htm>`_, Seja cuidadoso com este comando - recuperação de arquivos deletados é muito difícil, se não impossível!

- ``rmdir``: Um comando alternativo para remover diretórios do seu sistema de arquivos. Forneça um diretório que você deseja remover. Novamente, seja cuidadoso: você não será perguntado para confirmar suas intenções ao apagar.

- ``sudo``: Um programa que permite que você rode comando com os privilégios de segurança de outro usuário. Geralmente, o programa é usado para rodar outros programas como ``root`` - o `super usuário <http://pt.wikipedia.org/wiki/Superusuário>`_ de qualquer sistema operacional baseado ou derivado do UNIX.

.. note:: Isto é apenas um resumo da lista de comandos. Confira a documentação do ubuntu em `Usando o terminal <https://help.ubuntu.com/community/UsingTheTerminal>`_ para uma visão mais detalhada, ou o `Cheat Sheet <http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/>`_ feito por FOSSwire para ser um rápido guia de referências.

.. _installing-software:

Instalando os Softwares
-----------------------
Agora que você tem um bom conhecimento de como interagir com o terminal, você pode começar a instalar os softwares requeridos para este tutorial.

Instalando Python
*****************
Então, como é que você vai instalar o Python 2.7.5 no seu computador? Você pode já ter Python instalado no seu computador - e se você estiver usando uma distribuição Linux ou OS X, você definitivamente já o tem instalado. Algumas das funcionalidades desses sistemas operacionais `estão implementadas em Python <http://en.wikipedia.org/wiki/Yellowdog_Updater,_Modified>`_, daí a necessidade de um interpretador.

Infelizmente, quase todos os sistemas operacionais modernos utilizam uma versão do Python que mais antiga do que a que nós estamos requerendo para este tutorial. Existem muitas maneiras diferentes nas quais você pode instalar Python, e muitas delas são, infelizmente, bastante complicadas de realizar. Nós demonstraremos a abordagem mais comumente usada, e fornecer links adicionais de leitura para mais informações.

.. warning:: Esta seção detalhará como rodar Python 2.7.5 *ao lado* da sua atual instalação do Python. É considerada como má prática remover do seu sistema operacional a instalação Padrão do Python e substitui-la por uma nova versão. Fazer isso pode quebrar as funcionalidades do seu sistema operacional!

Apple OS X
..........
A maneira mais simples de ter Python 2.7.5 instalado no seu Mac é baixando e rodando o simples instalador fornecido no site oficial Python. Você pode baixar o instalador ao visitar a página em http://www.python.org/getit/releases/2.7.5/.

.. warning:: Garanta que você baixou o arquivo ``.dmg`` que é relevante para sua versão do OS X!

#. Depois que você baixou o arquivo ``.dmg``, dê um clique duplo no `Finder <http://pt.wikipedia.org/wiki/Finder>`_.
#. O arquivo monta como um disco separado e uma nova janela do Finder é aprensetada para você.
#. Duplo clique no arquivo ``Python.mpkg``. Isto iniciará o instalador Python.
#. Continue através das diversas tela até o ponto onde você já está pronto para instalar o software. Você pode ter que fornecer sua senha para confirmar que você deseja instalar.
#. Uma vez completada, feche o instalador e ejete o disco Python. Você pode agora deleter o arquivo ``.dmg`` baixado.

Você deve ter agora uma versão atualizada do Python instalada, pronta para o Django! Fácil, né?

Distribuições Linux
...................

Infelizmente, existem muitas maneiras diferentes em que você pode baixar, instalar e rodar uma versão atualizada do Python na sua distribuição Linux. Para piorar a situação, metodologias variam de distribuições para distribuições. Por exemplo, as instruções para instalar Python no `Fedora <http://fedoraproject.org/>`_ pode diferenciar daquelas para instalar no `Ubuntu <http://www.ubuntu.com/>`_.

Entretanto, nem toda esperança está perdida. Uma ferramenta incrível (ou um *Gerenciador de ambiente Python*) chamado `pythonbrew <https://github.com/utahta/pythonbrew>`_ pode nos ajudar a resolver este problema. Ela fornece uma maneira fácil para instalar e gerenciar diferentes versões do Python, o que significa que você pode deixar a instalação padrão do Python no seu sistema operacional sozinha. Irrá!

Retirando as instruções fornecidas `da página do pythonbrew no Github <https://github.com/utahta/pythonbrew>`_ e `desta thread na página do Stack Overflow <http://stackoverflow.com/questions/5233536/python-2-7-on-ubuntu>`_, os seguintes passos irão instalar o Python 2.7.5 na sua distribuição Linux.

#. Abra uma nova instância do Terminal
#. Execute o comando ``curl -kL http://xrl.us/pythonbrewinstall | bash``. Isto irá baixar o instalador e executar executá-lo dentro do seu terminal para você. Isto instala o pythonbrew dentro do seguinte diretório ``~/.pythonbrew``. Lembre, o til (``~``) representa o seu diretório home!
#. Você precisa então editar o arquivo ``~/.bashrc``. Em um editor de texto (como o ``gedit``, ``nano``, ``vi`` ou ``emacs``), e adicione o seguinte em uma nova linha no final do arquivo ``~/.bashrc``: ``[[ -s $HOME/.pythonbrew/etc/bashrc ]] && source $HOME/.pythonbrew/etc/bashrc``
#. Uma vez que você salvou as alterações no arquivo ``~/.bashrc``, feche seu terminal e abra um novo. Isto permitirar que as alterações sejam então aplicadas.
#. Execute o comando ``pythonbrew install 2.7.5`` para instalar o Python 2.7.5.
#. Você precisa então *mudar* para o Python 2.7.5 para *ativar* a nova instalação. Faça isto executando o comando ``pythonbrew switch 2.7.5``.
#. Python 2.7.5 deverá agora estar instalado e pronto para uso.

.. note:: Diretórios e arquivos que começam com um ponto podem ser considerados equivalentes aos *arquivos ocultos* do Windows.`Arquivos com ponto <http://en.wikipedia.org/wiki/Dot-file>`_ normalmente não são visíveis no visualizador de diretórios, e são comumente usados para configurações de arquivos. Você pode usar o comando ``ls`` para visualizar arquivos ocultos ao adicionar o ``-a`` no final do comando, ficando da seguinte forma ``ls -a``.

.. _requirements-install-python-windows:

Windows
.......
Por padrão, o Microsoft Windows vem sem nenhuma instalação do Python. Isto significa que você não tem que se preocupar em deixar versões diferentes juntas; instalando do início deve funcionar bem. Você pode baixar uma versão 64-bit ou 32-bit do Python a partir do `site oficial Python <http://www.python.org/download/>`_. Se você não está certo sobre qual baixar, você pode descobrir se o seu computador é 32-bit ou 64-bit ao olhar nas instruções fornecidas `no site da Microsoft <http://windows.microsoft.com/en-gb/windows7/32-bit-and-64-bit-windows-frequently-asked-questions>`_.

#. Quando o instalador estiver baixado, abra o arquivo no local onde baixou.
#. Siga os passos na tela para instalar o Python.
#. Feche o instalador assim que completar a instalação, e delete os arquivos baixados.

Assim que o instalador terminou, você deve ter uma versão do Python pronta para uso. Por padrão, Python 2.7.5 está instalado na pasta ``C:\Python27``. Nós recomendamos que você deixe esse caminho como está.

Após a conclusão da instalação, abra um prompt de comando e execute o comando ``python``. Se você ver o prompt do Python, a instalação foi um sucesso. Entretanto, em algumas circunstâncias, o instalador pode não setar suas variáveis de ambiente do Windows no ``PATH`` corretamente. Isto resultará no comando ``python`` não ter sido encontrado. No Windows 7, você pode corrigir isto fazendo o seguinte:

#. Clique no *iniciar*, então com o botão direito clique em *Meu Computador* e selecione *Propriedades*.
#. Clique em *Avançado*.
#. Clique no botão *Variáveis de Ambiente*.
#. Na lista *Variáveis do Sistema*, procura a variável chamada *Path*, clique nela, e então clique no botão *Editar*.
#. No fim da linha, coloque ``;C:\python27;C:\python27\scripts``. Não esqueça do ponto e vírgula -  e certamente *não* adicione um espaço.
#. Cliquem em OK em cada janela para salvar suas mudanças.
#. Fecha qualquer janela do prompt de comandos aberta, e abra uma nova instância, e tenta agora rodar o comando ``python`` novamente.

Isto deve fazer a sua instalação do Python funcionar. No Windows XP, `tem instruções ligeiramente diferentes <http://www.computerhope.com/issues/ch000549.htm>`_, e `com o Windows 8 fazer desta forma <http://stackoverflow.com/a/14224786>`_.

Configurando o ``PYTHONPATH``
*****************************
Agora com Python instalado, nós precisamos verificar se a instalação foi bem sucedida. Para fazer isto, nós precisamos checar se a `variável de ambiente <http://pt.wikipedia.org/wiki/Vari%C3%A1vel_de_ambiente>`_ ``PYTHONPATH`` está configurada corretamente. ``PYTHONPATH`` fornece o interpretador Python com a localização dos `pacotes e módulos <http://stackoverflow.com/questions/7948494/whats-the-difference-between-a-python-module-and-a-python-package>`_ adicionais do Python que adicionam funcionalidades extras para a instalação base do Python. Sem a correta configuração do ``PYTHONPATH``, nós não seremos capazes de instalar e usar o Django!

Primeiro, vamos verificar se nossa variável ``PYTHONPATH`` existe. Dependendo da técnica de instalação que você escolheu, isto pode ou não ter sido feito pra você. Para fazer isto no seu sistema operacional baseado no UNIX, execute o seguinte comando no terminal.

.. code-block:: guess

	$ echo $PYTHONPATH

Em uma máquina Windows, abra o prompt de comando e execute o seguinte.

	$ echo %PYTHONPATH%

Se tudo funcionar, você deve então ver uma saída que parece com o exemplo abaixo. Em uma máquina Windows, você verá obviamente um caminho Windows, provavelmente proveniente da unidade C.

.. code-block:: guess
	
	/opt/local/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages:

Este é o caminho para o seu diretório ``site-packages`` da sua instalação Python, onde pacotes e módulos Python adicionais estão armazenados. Se você vê um caminho, você pode continuar para a próxima parte deste tutorial. Se, no entanto, você não vê nada, você precisará fazer um pequeno trabalho de detetive para descobrir o caminho. Em uma instalação Windows, isto deve ser um exercício trivial: ``site-packages`` está localizado dentro da pasta ``lib`` do diretório da sua instalação Python. Por exemplo, se você instalou Python em ``C:\Python27``, ``site-packages`` estará em ``C:\Python27\Lib\site-packages\``.

No entanto, sistemas operacionais baseados em UNIX requerem um pequeno trabalho de detetive para descobrir o caminho do seu ``site-packages`` na sua instalação. Para fazer isso, abra seu interpretador Python. A seguinte sessão no terminal demonstra os comandos que você deve executar.

.. code-block:: python
	
	$ python
	
	Python 2.7.5 (v2.7.5:ab05e7dd2788, May 13 2013, 13:18:45) 
	[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
	Type "help", "copyright", "credits" or "license" for more information.
	
	>>> import site
	>>> print site.getsitepackages()[0]
	
	'/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages'
	
	>>> quit()

Chamando ``site.getsitepackages()`` teremos como retorno uma lista de caminhos que apontam para o pacote Python adicional e os módulos armazenados. O primeiro normalmente retorna o caminho para o seu diretório ``site-packages`` - pode ser necessário mudar a posição do índice da lista depedendo da sua instalação. Se você receber uma mensagem de erro indicando que ``site-packages()`` não está presente dentro do módulo ``site``, verifique se você está rodando a versão correta do Python. A versão 2.7.5 deve incluir esta função. Versões anteriores da linguagem não incluem esta função.

A string que é mostrada como um resultado da execução do ``print site.getsitepackages()[0]`` é o caminho para o diretório ``site-packages`` da sua instalação. Tendo o caminho, nós agora precisamos adicioná-lo na sua configuração. Em um sistema operacional baseado ou derivado do UNIX, edit seu arquivo ``.bashrc`` mais uma vez, adicionando o seguinte ao final do arquivo.

.. code-block:: guess
	
	export PYTHONPATH=$PYTHONPATH:<PATH_TO_SITE-PACKAGES>

Substitua ``<PATH_TO_SITE-PACKAGES>`` com o caminho so seu diretório ``site-packages`` que você conseguiu anteriormente com a função ``site.getsitepackages()``. Salve o arquivo, e feche e abra uma nova instância do seu terminal.

Em um computador com Windows, você tem que seguir as instruções mostradas na Seção :num:`requirements-install-python-windows` para abrir a janela de configuração de variáveis de ambiente. Adicione uma variável ``PYTHONPATH`` com o valor a ser definido para a sua pasta ``site-packages``, que geralmente está em ``C:\Python27\Lib\site-packages\``.

Usando Setuptools e Pip
***********************
Instalar e configurar seu ambiente de desenvolvimento é uma parte realmente importante de qualquer projeto. Embora seja possível instalar pacotes Python como o Django separadamente, isso pode levar a numerosos problemas e dificuldades mais tarde. Por exemplo, como você compartilharia sua configuração com outro desenvolvedor? Como você configuraria o mesmo ambiente em uma máquina nova? Como você atualizaria para a última versão do pacote? Usando um gerenciador de pacotes remove muitos dos problemas envolvidos em instalar e configurar seu ambiente. Ele também garantirá que os pacotes que você instala é correto para a versão do Python que você está utilizando, juntamente com a instalação de qualquer outro pacote que seja dependência de algum pacote que você queira instalar.

Neste livro, nós estaremos usando o *Pip*. Pip é um gerenciador de pacotes amigável envolta do *Setuptools*. Por causa do Pip depender do Setuptools, somos obrigados a garantir que ambos estão instalados no seu computador.

Para começar, nós devemos baixar o Setuptools do `site oficial de pacotes Python <https://pypi.python.org/pypi/setuptools/1.1.6>`_. Você pode baixar o pacote em um arquivo compactado ``tar.gz``. Usando seu programa favorito para extrair, extraia os arquivos. Todos eles devem aparecer em um diretório chamado ``setuptools-1.1.6`` - onde ``1.1.6`` representa o número da versão do Setuptools. A partir do terminal, você pode então entrar no diretório e executar o script ``ez_setup.py`` como mostrado abaixo.

.. code-block:: guess
	
	$ cd setuptools-1.1.6
	$ sudo python ez_setup.py

No exemplo acima, nós também usamos ``sudo`` para permitir que as mudanças sejam feitas em todo o sistema. O segundo comando deve instalar o Setuptools para você. Para verificar se a instalação foi um sucesso, você deve ser capaz de ver uma saída parecida com a mostrada abaixo.

.. code-block:: guess
	
	Finished processing dependencies for setuptools==1.1.6

Claro que, ``1.1.6`` é substituido com a versão do Setuptools que você está instalando. Se esta linha aparecer, você pode então instalar o pip. Esse é um processo trivial, e pode ser completado com um simples comando. A partir do terminal, entre com o seguinte comando.

.. code-block:: guess
	
	$ sudo easy_install pip

Este comando deve baixar e instalar o Pip, novamente com acesso ao todo o sistema. Você deve ver a seguinte saída, verificando que o Pip foi instalado com sucesso.

.. code-block:: guess
	
	Finished processing dependencies for pip

Após ver esta saída, você deve ser capaz de iniciar o Pip no seu terminal. Para fazer isso, apenas digite ``pip``. Ao invés de um erro de comando desconhecido, você deve ser apresentado ao uma lista de comandos e chaves que o Pip aceita. Se você ver isso, você está pronto para seguir em frente!

.. note:: Em computadores com Windows, siga os mesmos processos básicos. Entretanto, você não precisa entrar com o comando ``sudo``.

Instalando Django
*****************
Uma vez que o gerenciador de pacotes Pip está instalado com sucesso no seu computador, instalar Django é fácil. Abra uma janela do terminal, e execute o seguinte comando.

.. code-block:: guess
	
	$ pip install -U django==1.7

Se você está usando um sistema operacional baseado em UNIX e receber alertas sobre permissões insuficientes, você precisará rodar o comando com privilégios elevados usando o comando ``sudo``. Se for este o caso, você deve então rodar o seguinte comando no lugar.

.. code-block:: guess
	
	$ sudo pip install -U django==1.7

O gerenciador de pacotes irá baixar o Django e instalar no lugar correto para você. Após a conclusão, Django deverá estar instalado com sucesso. Note, se você não incluir o ``==1.7``, então uma versão diferente do Djando pode ser instalada.

instalando o Python Imaging Library
***********************************
Durante o curso de construção do Rango, nós estaremos fazendo upload e manipulando imagens. Isto significa que nós precisaremos do apoio do `Pillow (Python Imaging Library) <https://pillow.readthedocs.org/en/latest/>`_. Para instalar este pacote, execute o seguinte comando.

.. code-block:: guess
	
	$ pip install pillow

Novamente, use ``sudo`` se for preciso.

Instalando outros pacotes Python
********************************
Vale a pena norta que pacotes Python adicionais podem ser facilmente baixados usando a mesma maneira. O `O índice de pacotes Python <https://pypi.python.org/pypi>`_ fornecem uma lista de todos os pacotes Python disponíveis pelo pip.

Para obter uma lista dos pacotes instalados, você pode rodar o seguinte comando.

.. code-block:: guess
	
	$ pip list

Compartilhando sua lista de pacotes
***********************************
Você também pode pegar uma lista de pacotes instalados em um formato que pode ser compartilhado com outros desenvolvedores. Para fazer isso, execute o seguinte comando.

.. code-block:: guess
	
	$ pip freeze > requirements.txt

Se você examinar o ``requirements.txt`` usando o comando ``more``, ``less`` ou ``cat``, você verá a mesma informação mas em um formato ligeiramente diferente. Isso é incrivelmente útil para configurar seu ambiente ou outro computador, por exemplo.

.. code-block:: guess
	
	$ pip install -r requirements.txt

Ambiente de desenvolvimento Integrado (IDE)
-------------------------------------------
Embora não seja absolutamente necessário, um bom ambiente de desenvolvimento integrado (chamaremos de IDE) em Python pode ser muito útil durante seu processo de desenvolvimento. Existem vários, como o JetBrains da `PyCharm <http://www.jetbrains.com/pycharm/>`_ e o *PyDev* (um plugin da IDE `Eclipse <http://www.eclipse.org/downloads/>`_) destacam-se como os mais populares na escolha. A `Python Wiki <http://wiki.python.org.br//IdesPython>`_ fornece uma lista atualizada das IDEs Python.

Pesquise qual dessas é melhor para você, e esteha ciente que alguns podem requerer que você compre uma licença. De preferẽncia, você irá querer selecionar uma IDE que suporte integração com Django. Tanto PyCharm quanto PyDev surportam integração com Django por padrão - embora você terá que apontar para a IDE para a versão do Python que você está usando.

Ambientes Virtuais
******************
Nós estamos com quase tudo pronto para começar! No entanto, antes de nós continuarmos, é importante ressaltar que enquanto esta configuração está boa para iniciar, existem algumas desvantagens. E se você tiver outra aplicação Python que precise de uma versão diferente para rodar? Ou você queira trocar para uma nova versão do Django, mas quer continuar mantendo seu projeto Django 1.7?

A solução para isso é usar `ambientes virtuais <http://www.arruda.blog.br/programacao/python/usando-virtualenvwrapper/>`_. Ambiente virtuais permitem que diferentes instalações do Python e seus pacotes relevantes existam em harmonia. Esta é geralmente a abordagem aceita para configurar uma instalação Python hoje em dia.

Eles são fáceis de instalar, uma vez que você tenha pip instalado, e saiba o comando certo. Você precisa instalar um par de pacotes adicionais.

.. code-block:: guess
	
	$ pip install virtualenv
	$ pip install virtualenvwrapper
	
O primeiro pacote fornece a infraestrutura para criar um ambiente virtual. Veja `uma introduçãoao Pip e Virtualenv para iniciantes Python <http://dabapps.com/blog/introduction-to-pip-and-virtualenv-python/>`_ por Jamie Matthews, para mais detalhes sobre o uso de virtualenv. No entanto, usando apenas o *virtualenv* é bastante complicado. O segundo pacote fornece um container (wrapper) para as funcionalidades no virtualenv, tornando a vida bem mais fácil.

Se você está usando algum sistema baseado no UNIX, para usar este wrapper você precisa chamar o seguinte script shell na sua linha de comando:

.. code-block:: guess

	$ source virtualenvwrapper.sh

É uma boa ideia adicionar isso ao seu script bash do perfil. Então você não terá que rodar isso cada vez que você quiser usar os ambientes virtuais.

No entanto, se você está usando Windows, então instale o pacote `virtualenvwrapper-win <https://pypi.python.org/pypi/virtualenvwrapper-win>`_:

.. code-block:: guess

	$ pip install virtualenvwrapper-win
	

Agora você deve estar com tudo pronto para criar um ambiente virtual:

.. code-block:: guess

	$ mkvirtualenv rango

Você pode listar os ambientes virtuais criados com ``lsvirtualenv``, e você pode ativar um ambiente virtual da seguinte forma:

.. code-block:: guess

	$ workon rango
	(rango)$

Seu prompt irá mudar mostrando o ambiente virtual atual, como no exemplo anterior, rango. Agora dentro deste ambiente você será capaz de instalar todos os pacotes que você quiser, sem interferir com seu ambiente padrão ou qualquer outro criado. Tente ``pip list`` para ver que você não tem Django ou o Pillow instalado no seu ambiente virtual. Você pode agora instalá-los com o pip, e então eles só existirão no seu ambiente virtual.

Mais tarde, quando nós formos fazer deploy da aplicação, nós iremos passar por um processo similar. Veja o Capítulo :ref:`Fazendo Deploy da sua aplicação<virtual-environment>` e configure um ambiente virtual no PythonAnywhere.

Repositório de Códigos
**********************
Devemos também ressaltar que quando você está desenvolvendo, você deve sempre abrigar seu código dentro de um repositório controlador de versão, tal como o `SVN <http://subversion.tigris.org/>`_ ou o `GIT <http://git-scm.com/>`_. Nós não passaremos por esse assunto agora, para que possamos estar focados em desenvolver a aplicação em Django. No entanto, nós fornecemos um :ref:`Curso Intensivo sobre GIT <git-crash-course>`. Nós recomendamos fortemente que você configure um repositório GIT para seus próprios projetos. Fazendo isso você pode acabar se salvando de umd desastre.

Exercícios
----------
Para ficar confortável com seu ambiente, tente realizar os seguintes exercícios.

* Instalar Python 2.7.5+ e Pip.
* Brinque com seu terminal/linha de comando (CLI) e crie um diretório chamado ``code``, que nós usaremos para criar nosso projeto nele.
* Instalar os pacotes do Django e Pillow.
* Configurar seu ambiente virtual
* Configurar sua conta no GitHub
* Baixar e configurar um Ambiente de Desenvolvimento Integrado (IDE) (como o PyCharm)
* Nós fizemos o código para o livro e a aplicação que você irá construir e disponibilizamos no GitHub, para ver acesse `Tango With Django Book <https://github.com/leifos/tango_with_django_book>`_ e `Rango Application <https://github.com/leifos/tango_with_django>`_ .
	* Se você notar qualquer erro ou problemas com o livro, você pode fazer uma mudança e submetê-la!
	* Se você tiver qualquer problema com os exercícios, você pode checar o repositório e ver como nós completamos eles.
