#GIT ou GITHUB

- **Github é servidor(nuvem)**
- **Git é local**



## Linha de comando(cmd)

#####WINDOWS(shell)	-	UNIX(linux)(bash)

**cd			-	cd**			escolher reposiorio(pasta) que sera trabalhado		

​								"cd /" vai para pasta C: "cd Windows" pasta C:\Windows

dir			-	ls			pastas dentro do repositorio
mkdir		-	mkdir		cria repositorio 
rmdir /s /q	-	rm -rf		deleta repositorio "/s /q" e "-rf"  - flag(complemento do comando) forçar 
								apagar tudo que tem dentro do repositorio
del							deleta arquivos   ex: vai na pasta que esta o arquivo "del nome.formato"
cd..			-	cd ..		voltar repositorio
tab(tecla)					completa o comando
Scls			-	crtl+L(clear)	apagar terminal

​			-	sudu su		permissao para programa que imita o linux

echo						print
criar arquivo 				echo dados > nome.formato	ex: echo asaph vai viajar > reveillon.txt

​			-	pwd       mostra o endereço da pasta

​			-	ls -a 	mostra arquivos ocultos na pasta

​			-	mv		mover arquivomv nome.formato ./destino		ex: mv strogonoff.md ./receitas

GIT

COMANDOS
criar commit
	git init 						iniciar criar repositorio .git
	git add * 					mover arquivos, versionar...
	git commit -m "commit inicial" 	criar commit
	
	git status 							diz se o arquivo esta UNMODIFIED, MODIFIED ou STAGED
	git config --list						lista seu email, nickname ...
	git config --global user.name	nome			criar nome que vai no commit
	git config --global user.email "asaph@h...	criar email que vai no commit(global torna padrao para todos os commits)
	git config --global --unset user.email		apaga email cadastrado (quando for fazer um commit, ele vai pedir)
	git config --global --uset user.name		apaga o nome cadastrado
	git remote add origin 'url'				mandar para github e nomear a url de "origin"					
	git remote -v							listar o que esta no repositorio remoto
	git push origin maste					mandar para github


**SHA1** - algoritmo de segurança (criptografia). encriptaçao identifica o arquivo com uma chave especifica
salvar arquivo com a encriptacao com 40 caracteres
	openssl sha1 "nome do arquivo"
####Objetos fundamentais (tornam o sist. distribuido seguro)

	blob -aramazena metadados do arquivo(tamanho, conteudo, nome..)
		retorna o sha1 do arquivo
			echo 'texto ou arquivo' | git hash-object --stdin
	
	tree - armazena tipos de blobs diferentes e outras trees, tem outro sha1 proprio, um arquivo se alterado muda o seu blob e sua tree
	
	commit- tem todas as informações, comporta tree e blob, armazena o texto, autor... e um novo sha1
####Chave SSH - conexao confiavel entre sua maquina e a central github, passando informacoes e projetos pubicos

	gerando chave no gitbash - ssh-keygen
		ele vai criar em uma pasta 2 chaves(publica e privada)
	confirmar que criou
		cd /c/users/usuario/.ssh (ele da esse local quando cria)
		ls (igual dir)
	mandando chave publica para github
		no gitbash escreve 
			cat id_rsa.pub				(esse id estava no ls anterior)
		vai no github 
			seetings, ssh keys, new ssh key, nomeia e cola o codigo gerado no gitbash
		no gitbash escreve
			eval $(ssh-agent -s)
				vai dar o agent pid "xxxx"
			passar chave pro agente
				ssh-add id_rsa
	
	clonar repositorio do github para sua maquina
		vai no repositorio escolhido no github, code<>, ssh, copia e vai no git bash
		No git bash
			git clone "cola o texto copiado no github"
			yes
			vai estar na pasta que voce estava antes de executar os comandos

​	

####AULA SOBRE NOMES USADOS NO GIT

	Tracked - git tem conhecimento dos arquivos
		Unmodified - ainda nao foi modificado 
		Modified - arquivo ja modificado(alterado)
		Staged - Arquivos que serao unidos em um novo tipo de agrupamento
	
	Untracked - git nao tem ciencia da existencia do arquivo (acabou de ser criado - antes do "git add *")
	
		ENTAO
			criou ariquivo depois do git init, ele é UNTRACKED, git add * ele é TRACKED STAGED, commit ele é UNMODIFIED
			alterou o arquivo ele é MODIFIED
			rodar o git add * no arquivo MODIFIED ele volta pra STAGE
			removeu o arquivo UNMODIFIED ele vira UNTRACKED
	
			GIT POSSUI 2 AREAS(AMBIENTES)
				SERVIDOR (github) 
					REMOTE REPOSITORY - vem o arquivo commitado do LOCAL REPOSITORY
				AMBIENTE DE DESENVOLVIMENTO (seu notebook)
					alterar arquivos aqui nao vai diretamento pro servidor, a nao ser que voce 					queira
						WORKING DIRECTORY(diretorio de trabalho) - pastas onde criamos arquivos
						STAGING AREA - arquivos depois do git add *
						LOCAL REPOSITORY - arquivos apos o commit que pode ser lancado no SERVIDOR - REPOSITORIO REMOTO

GITHUB
AsaphPevidor
Pevidor13
ideal é ter o mesmo email e nickname do git, facilita na manipulacao dos programas
	Criar um repositorio 
		link do perfil(canto superior direito)
		your repositories
		new
		create apos preencher
		copia url (ex: https://github.com/AsaphPevidor/livro.receitas.git)
		abre o git bash na pasta que possui arquivos e pastas com arquivos que deseja mandar
		git remote add origin https://github.com/AsaphPevidor/livro.receitas.git
			origin é uma variavel atrelada a url, para nao escrever a url sempre que quiser exportar os arquivos para github
		git remote -v lista remotos cadastrados 

