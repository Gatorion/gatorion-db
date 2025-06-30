# Integridade, Desempenho e Crescimento do Projeto – Gatorion

### Integridade Referencial

O banco de dados do sistema Gatorion foi estruturado para garantir integridade entre os dados, evitando inconsistências. Algumas regras aplicadas:

- Cada perfil está sempre vinculado a um usuário válido.
- Cada postagem está ligada a um usuário existente.
- Cada comentário está relacionado a uma postagem válida.
- Cada curtida está vinculada a uma postagem válida.
- Cada usuário pode acessar apenas jogos e materiais registrados no sistema.

---

### Desempenho

Para garantir que o sistema funcione de forma eficiente e escalável, foram adotadas as seguintes práticas:

#### Nomes padronizados para facilitar buscas

- `usuario_email` (para login)
- `nome_usuario` (para exibir e buscar usuários)
- `nome_material` (para filtrar materiais)

#### Tipos de dados adequados

- `VARCHAR` com tamanhos bem definidos para textos
- `DATE` para registrar datas de criação de perfis, posts e comentários

#### Normalização de dados

- O modelo evita duplicação de informações, colocando cada tabela para informações especificas.
- As tabelas mantêm dados bem separados, por exemplo, a postagem armazena apenas o `id_usuario`, não o nome completo.
- Essa estrutura facilita manutenções futuras e melhora a consistência do banco.

---

### Segurança

- As senhas dos usuários são armazenadas com hash seguro (criptografadas).
- O acesso ao banco é controlado por permissões de usuário (ex: leitura apenas para relatórios).
- Backups automáticos são previstos para garantir a continuidade do serviço.

---

### Dados Coletados e Privacidade

A plataforma Gatorion coleta os seguintes dados no momento da criação de conta:

- E-mail
- Nome completo

Essas informações são utilizadas para:
- Identificar o usuário dentro da rede social
- Garantir segurança nas interações
- Personalizar a experiência do usuário

**Observação**: O perfil do usuário é visível publicamente dentro da plataforma.

Além disso, ao navegar no site, são coletados dados de interação e acesso, como páginas visitadas, para aprimorar a experiência geral.

---

### Crescimento e Escalabilidade do Projeto

O banco de dados foi planejado considerando a evolução da plataforma. Estão previstas:

- Suporte ao aumento no número de usuários, postagens e comentários sem perda de performance
- Possibilidade de adicionar novas tabelas ou funcionalidades sem impactar o funcionamento atual

---