# 🖇️ **CDN (Content Delivery Network)**
Uma CDN é uma rede de servidores distribuídos globalmente, que cacheia e entrega conteúdo estático (como imagens, CSS e JavaScript) para usuários de forma rápida e eficiente, baseada na localização geográfica. Isso melhora a velocidade de carregamento e diminui a latência.

---

Para melhorar a entrega de conteúdo estático, você pode usar uma CDN para armazenar e distribuir arquivos, como imagens, CSS e JavaScript. Basta configurar a URL dos arquivos para apontar para a CDN. Não há necessidade de PHP para isso.

### Exemplo de Uso com HTML e CDN

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Exemplo com CDN</title>

    <!-- CSS carregado de uma CDN -->
    <link rel="stylesheet" href="https://cdn.exemplo.com/css/estilo.css">
</head>
<body>
    <h1>Minha Página com CDN</h1>

    <!-- Imagem carregada da CDN -->
    <img src="https://cdn.exemplo.com/images/logo.png" alt="Logo">
</body>
</html>
```

Neste exemplo, o CSS e a imagem são carregados de uma CDN, o que acelera o tempo de carregamento para usuários geograficamente distantes do servidor original.
