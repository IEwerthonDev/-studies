# 👨🏿‍💻 **Client Side Caching (Cache no Lado do Cliente)**
O cache no lado do cliente é o armazenamento temporário de conteúdo no dispositivo do usuário (navegador ou cache local), permitindo que o navegador carregue rapidamente recursos já baixados anteriormente. O cache do lado do cliente pode ser configurado através de cabeçalhos HTTP, como `Cache-Control` e `Expires`.

---

O cache do lado do cliente permite que dados persistam no navegador do usuário para reduzir carregamentos futuros. Podemos usar o `localStorage` do navegador para armazenar dados persistentes ou `sessionStorage` para dados temporários.

### Exemplo de Implementação com JavaScript e `localStorage`

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Exemplo com Cache no Cliente</title>
</head>
<body>
    <h1>Exemplo de Caching no Cliente</h1>

    <div id="dados"></div>

    <script>
        // Verificar se os dados estão no cache do cliente (localStorage)
        let dados = localStorage.getItem('usuarios_dados');

        if (!dados) {
            // Se não está no cache, buscar dados do servidor
            fetch('/api/usuarios') // Endereço de uma API fictícia
                .then(response => response.json())
                .then(data => {
                    // Armazenar os dados no cache do cliente por 1 hora
                    localStorage.setItem('usuarios_dados', JSON.stringify(data));
                    localStorage.setItem('cacheTime', Date.now());

                    exibirDados(data);
                });
        } else {
            // Verificar se o cache expirou (1 hora)
            const cacheTime = localStorage.getItem('cacheTime');
            const umaHora = 60 * 60 * 1000;

            if (Date.now() - cacheTime < umaHora) {
                // Exibir dados do cache se não expirou
                exibirDados(JSON.parse(dados));
            } else {
                // Se expirou, limpar o cache
                localStorage.removeItem('usuarios_dados');
                localStorage.removeItem('cacheTime');
                location.reload();
            }
        }

        function exibirDados(data) {
            const div = document.getElementById('dados');
            div.innerHTML = data.map(usuario => `Nome: ${usuario.nome} | Email: ${usuario.email}`).join('<br>');
        }
    </script>
</body>
</html>
```

Nesse exemplo, o JavaScript verifica se os dados dos usuários estão no `localStorage`. Se não estão, ele faz uma solicitação à API `/api/usuarios` e armazena os dados por 1 hora.
