1° CorsConfig.java

Versão anterior: Só permitia requisições do http://localhost:8081 e permitia envio de credenciais (cookies, headers de autenticação).

Versão atual: Permite requisições de qualquer origem, mas não permite envio de credenciais.
Isso é útil para desenvolvimento, pois facilita testes de diferentes frontends.

2° DataIntializer.java

2.1 Criação de Usuários Padrão

Antes: Não havia criação automática de usuários padrão (admin/user).

Depois: Adicionou o método criarUsuariosPadrao() que cria dois usuários iniciais (admin e user) caso não existam no banco, antes de inserir os dados de robôs, eventos e entregas.

2.2 Dependências

Antes: Não tinha dependências para UsuarioRepository e PasswordEncoder.

Depois: Incluiu @Autowired UsuarioRepository e @Autowired PasswordEncoder para manipular usuários e criptografar senhas.

2.3 Fluxo de Inicialização

Antes: Inicializava apenas robôs, eventos sensoriais e entregas simuladas.

Depois: Inicializa usuários padrão antes de verificar e popular os dados de robôs, eventos e entregas.

3° application.properties

Adiciona:
jwt.secret=404E635266556A586E3272357538782F413F4428472B4B6250645367566B5970 (chave secreta para tokens JWT)
jwt.expiration=86400000 (tempo de expiração do token JWT em milissegundos)

4° pox.xml

4.1 Spring Security

Permite autenticação/autorização na aplicação.

4.2 JWT (JSON Web Token)

Permite geração e validação de tokens JWT.

4.3 Validação

Permite validação de dados (ex: anotações @Valid).

4.4 Resumo 

O primeiro pom.xml é básico, apenas para API REST e banco de dados.
O segundo pom.xml adiciona suporte para autenticação/autorização (Spring Security), autenticação JWT e validação de dados.

Essas mudanças permitem que o projeto trabalhe com login seguro, tokens JWT e validação automática de dados recebidos.