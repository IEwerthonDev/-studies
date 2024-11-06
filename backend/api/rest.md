# ♟️ REST: Arquitetura e Funcionamento

REST (Representational State Transfer) é um estilo arquitetural de desenvolvimento de APIs que utiliza o protocolo HTTP para a comunicação entre cliente e servidor. Nessa abordagem, as APIs são projetadas para serem escaláveis, leves e de fácil manutenção.

Os principais princípios do REST são:

1. **Recursos**: Tudo em uma API REST é um recurso, identificado por uma URL única. Por exemplo, `/users`, `/products`, `/orders`.
2. **Verbos HTTP**: As operações são realizadas usando os métodos HTTP padrão: GET (leitura), POST (criação), PUT (atualização), DELETE (exclusão).
3. **Representação de dados**: Os dados são transferidos entre o cliente e o servidor no formato de representação, geralmente JSON ou XML.
4. **Stateless**: Cada requisição deve conter todas as informações necessárias para o servidor executar a ação, sem depender de informações de requisições anteriores.
5. **Hypermedia**: As respostas das APIs devem conter links para outros recursos relacionados, permitindo uma navegação mais intuitiva.

Exemplo de uma API REST em PHP:

```php
// Controller de Usuários
class UsersController
{
    // Listar todos os usuários (GET)
    public function index()
    {
        $users = User::all();
        return response()->json($users);
    }

    // Criar um novo usuário (POST)
    public function store(Request $request)
    {
        $user = User::create($request->all());
        return response()->json($user, 201);
    }

    // Exibir um usuário específico (GET)
    public function show($id)
    {
        $user = User::findOrFail($id);
        return response()->json($user);
    }

    // Atualizar um usuário (PUT)
    public function update(Request $request, $id)
    {
        $user = User::findOrFail($id);
        $user->update($request->all());
        return response()->json($user);
    }

    // Excluir um usuário (DELETE)
    public function destroy($id)
    {
        $user = User::findOrFail($id);
        $user->delete();
        return response()->json(null, 204);
    }
}
```