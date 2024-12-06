Como acessar o sistema EmbryoAll em uma máquina nova:
baixar o composer -> https://getcomposer.org/
instalar o composer, clicar duas vezes no arquivo executável, atenção a versão do PHP, deve ser maior que 8
no VisualCode digitar: composer install
 baixar o node.js: https://nodejs.org/en/download
 Rodar o arquivo executavel que baixou
Abrir o CMD para verificar se o node.js foi instalado: node -v
Verificar se o NPM foi instalado: npm -v
abrir o VisualCode->Terminal e digitar: npm install
Dar o git clone no projeto (caso seja o sistema novo) farlengeraldo/embryoall_laravel_1
Rodar as migration -> php artisan migrate
Se precisar criar um usuário no banco novo.insert into users (name,email,password,menu,perfil_usuario_id,users,perfisusuarios,clinicas,consulta) values ('ADMINISTRADOR','admin@gmail.com','$2y$10$RbZmfXxVzXmkxHp4kH5no..rPqdZlJvTxFFVJqeHxXREos9XBMjnq',',configuracoes,',1,',index,create,edit,',',index,create,edit,',',index,create,edit,','index,create,edit,delete');


Comandos e arquivos necessários para criar uma nova tela:


Criar de forma simplificada o model e o controller com o resource:
php artisan make:model SaidaMaterialMedicamento -c --resource

ou então faça:
php artisan make:model Paciente
 -> sempre no singular sem underline ex(TipoTratamento)

editar o model	-> adiciona campos no fillable (sempre minusculo)
				-> add o softDelete
				-> add storeRules e updateRules

e

php artisan make:controller UserController --resource (resource quando for fazer o crud completo)


cria rotas no Routes/web.php
 -> rota sempre no plural

criar migration para adicionar campo de permissão para a nova rota
php artisan make:migration alter_table_users_add_permissao_xxxxx

	Schema::table('users', function(Blueprint $table){
            $table->text('xxxxxx')->after('menu')->nullable();
        });
(xxxxxx -> nome da rota)

Criar uma migrate para adicionar os campos do softDelete na tabela que for trabalhar.

php artisan make:migration alter_table_nomeTabela_add_softDeletes_timestamps

Colar dentro do up e alterar users pela tabela que deseja criar os campos:
        Schema::table('users', function(Blueprint $table){
            $table->timestamps();
            $table->softDeletes();
        });


Alterar no componente do menu para add submenu da rota index (caso essa tela nessecite de ser adicionada no menu da rota index)
AuthenticatedLayout.vue

Adicionar validação de permissão

 v-if="$page.props.auth.user.usuarios.includes('index')"

 (o texto da permissão é sempre a rota )

Adicionar gate para rota no Providers/AuthServiceProvider.php

Incluir no controller a validação do gate
$this->authorize('clinicas-create');

criar uma pasta para os arquivos front em resources/js/Pages

criar arquivos :
 - Index.vue -> rota index (listar todos)
 - Create.vue -> rota create e edit
 (seguir padrão do User, sempre começa com letra maiscula)






Tudo sobre Bolo de Cenoura:
O bolo de cenoura é uma opção simples e prática para o café da manhã, lanche da tarde ou para uma ocasião especial com famílias e amigos. Essa receita é feita no liquidificador e fica pronta em menos de 1 hora. É ideal para quando você está com pouco tempo para cozinhar.

Fácil de fazer, o bolo de cenoura leva ingredientes que você provavelmente tem em casa: farinha de trigo, açúcar, óleo, fermento, cenoura e ovos. Para finalizar, você pode preparar cobertura com chocolate em pó. Confira como fazer!
