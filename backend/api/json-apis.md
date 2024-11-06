# 📥 JSON API

JSON API é um padrão de especificação para APIs que utilizam JSON como formato de intercâmbio de dados. Ele define um conjunto de convenções e melhores práticas para criar APIs RESTful de maneira consistente e legível.

Algumas das principais características do JSON API:

1. **Estrutura de Recursos**: Os dados são organizados em recursos, com seus devidos relacionamentos e metadados.
2. **Requisições e Respostas Padronizadas**: As requisições e respostas seguem um formato padrão, facilitando a interoperabilidade.
3. **Paginação, Filtragem e Ordenação**: O padrão define formas consistentes de realizar essas operações nos recursos.
4. **Tratamento de Erros**: Os erros são retornados de maneira estruturada e informativa.

Exemplo de uma resposta JSON API em PHP:

```php
// Controlador de Usuários
class UsersController extends Controller
{
    public function index(Request $request)
    {
        $users = User::query();

        // Filtragem
        if ($request->has('filter')) {
            $users->where('name', 'like', '%' . $request->input('filter') . '%');
        }

        // Paginação
        $page = $request->input('page.number', 1);
        $limit = $request->input('page.size', 10);
        $users = $users->paginate($limit, ['*'], 'page[number]', $page);

        return JsonApiResponse::make()
            ->data($users)
            ->links([
                'self' => route('users.index', $request->all()),
                'first' => route('users.index', array_merge($request->all(), ['page' => 1])),
                'last' => route('users.index', array_merge($request->all(), ['page' => $users->lastPage()])),
                'prev' => $users->previousPageUrl(),
                'next' => $users->nextPageUrl(),
            ])
            ->meta([
                'total' => $users->total(),
                'per_page' => $users->perPage(),
                'current_page' => $users->currentPage(),
                'last_page' => $users->lastPage(),
            ]);
    }
}
```

Neste exemplo, a resposta JSON API inclui os dados dos usuários, metadados sobre a paginação e links para navegação entre as páginas.