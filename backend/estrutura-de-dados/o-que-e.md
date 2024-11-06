# 🎲 O que é estrutura de dados?

Imagine que você é o dono de uma loja e precisa organizar os produtos que você vende. Você pode armazenar esses produtos de diferentes maneiras, dependendo de como você deseja acessá-los e manipulá-los.
Uma estrutura de dados é como você organiza e armazena seus produtos na loja. Você pode pensar nela como um método de organização dos seus dados.
Por exemplo, você pode usar uma `lista (array em PHP)` para armazenar todos os seus produtos em uma ordem específica. Isso seria como colocar todos os produtos em prateleiras, um ao lado do outro. Você pode facilmente acessar um produto específico pelo seu índice na lista.
Outra opção seria usar um `dicionário (array associativo em PHP)`, onde cada produto tem uma "etiqueta" (chave) que o identifica. Isso seria como ter uma prateleira com caixas, cada uma com um rótulo diferente, e você pode acessar um produto específico procurando pelo seu rótulo.
Você também poderia usar uma `fila (queue em PHP)`, onde os produtos são adicionados no final e removidos do início, como em uma fila de espera no caixa da loja.
Ou então uma `pilha (stack em PHP)`, onde os produtos são adicionados e removidos do topo, como uma pilha de caixas que você empilha uma em cima da outra.
Cada uma dessas estruturas de dados tem suas próprias vantagens e desvantagens, dependendo de como você precisa acessar e manipular seus produtos. Da mesma forma, as estruturas de dados em programação têm diferentes usos e propriedades, dependendo das necessidades do seu sistema.
O importante é entender que as estruturas de dados são formas de organizar e armazenar informações, de modo que você possa acessá-las e manipulá-las de maneira eficiente. Escolher a estrutura de dados certa pode fazer uma grande diferença na eficiência e desempenho do seu sistema.

**Array (Lista):** Um array em PHP é uma estrutura de dados que armazena uma coleção ordenada de valores. Você pode acessar cada elemento do array pelo seu índice numérico. Por exemplo:

~~~php
$frutas = array("maçã", "banana", "laranja");
echo $frutas[0]; // Output: "maçã"
~~~

**Array Associativo (Dicionário):** Um array associativo em PHP é uma estrutura de dados que armazena pares de chave-valor. As chaves são usadas para acessar os valores correspondentes. Por exemplo:

~~~php
$pessoa = array(
"nome" => "João",
"idade" => 30,
"profissão" => "Engenheiro"
);
echo $pessoa["nome"]; // Output: "João"
~~~

**Queue (Fila):** Uma fila em PHP é uma estrutura de dados que segue o princípio FIFO (First-In, First-Out), onde os elementos são adicionados no final e removidos do início. Você pode usar as funções `array_push()` e `array_shift()` para adicionar e remover elementos da fila.

~~~php
// Criando uma fila
$fila = new SplQueue();

// Adicionando elementos à fila
$fila->enqueue("João");
$fila->enqueue("Maria");
$fila->enqueue("Pedro");

// Removendo elementos da fila
echo $fila->dequeue(); // Output: "João"
echo $fila->dequeue(); // Output: "Maria"

// Verificando o primeiro elemento da fila sem removê-lo
echo $fila->peek(); // Output: "Pedro"
~~~

**Stack (Pilha):** Uma pilha em PHP é uma estrutura de dados que segue o princípio LIFO (Last-In, First-Out), onde os elementos são adicionados e removidos do topo da pilha. Você pode usar as funções `array_push()` e `array_pop()` para adicionar e remover elementos da pilha.

~~~php
// Criando uma pilha
$pilha = new SplStack();

// Adicionando elementos à pilha
$pilha->push("Maçã");
$pilha->push("Banana");
$pilha->push("Laranja");

// Removendo elementos da pilha
echo $pilha->pop(); // Output: "Laranja"
echo $pilha->pop(); // Output: "Banana"

// Verificando o topo da pilha sem removê-lo
echo $pilha->top(); // Output: "Maçã"
~~~

**Vetores e Matrizes:** Vetores e matrizes são estruturas de dados que armazenam coleções de valores, semelhantes a arrays. A diferença é que eles são otimizados para operações matemáticas. Você pode usar a classe SplFixedArray em PHP para criar vetores e matrizes.

~~~php
// Criando um vetor
$vetor = new SplFixedArray(5);
$vetor[0] = 10;
$vetor[1] = 20;
$vetor[2] = 30;
echo $vetor[1]; // Output: 20

// Criando uma matriz
$matriz = new SplFixedArray(3);
for ($i = 0; $i < $matriz->getSize(); $i++) {
    $matriz[$i] = new SplFixedArray(3);
    for ($j = 0; $j < $matriz[$i]->getSize(); $j++) {
        $matriz[$i][$j] = rand(1, 100);
    }
}
echo $matriz[1][2]; // Output: um número aleatório entre 1 e 100
~~~

**Hash Tables (Tabelas de Hash):** Uma tabela de hash em PHP é uma estrutura de dados que armazena pares de chave-valor, semelhante a um array associativo. A diferença é que as tabelas de hash usam uma função de hash para calcular o índice de cada chave, permitindo acesso rápido aos valores.

~~~php
// Criando uma tabela de hash
$hash = new ArrayObject();

// Adicionando elementos à tabela de hash
$hash["nome"] = "João";
$hash["idade"] = 30;
$hash["profissão"] = "Engenheiro";

// Acessando valores na tabela de hash
echo $hash["nome"]; // Output: "João"
echo $hash["idade"]; // Output: 30

// Iterando sobre os elementos da tabela de hash
foreach ($hash as $chave => $valor) {
    echo "Chave: $chave, Valor: $valor\n";
}
// Output:
// Chave: nome, Valor: João
// Chave: idade, Valor: 30
// Chave: profissão, Valor: Engenheiro

// Verificando se uma chave existe na tabela de hash
if ($hash->offsetExists("idade")) {
    echo "A chave 'idade' existe na tabela de hash.";
} else {
    echo "A chave 'idade' não existe na tabela de hash.";
}

// Removendo um elemento da tabela de hash
$hash->offsetUnset("profissão");

// Verificando o número de elementos na tabela de hash
echo "Número de elementos na tabela de hash: " . $hash->count();
// Output: Número de elementos na tabela de hash: 2
~~~

**Árvores:** Uma árvore é uma estrutura de dados hierárquica, onde cada nó pode ter zero ou mais nós filhos. Em PHP, você pode usar a classe `SplTrees` para trabalhar com estruturas de árvore.

~~~php
// Criando uma árvore binária
$arvore = new SplBinaryTree();
$arvore->insert(10);
$arvore->insert(5);
$arvore->insert(15);
$arvore->insert(3);
$arvore->insert(7);
$arvore->insert(12);
$arvore->insert(20);

// Percorrendo a árvore em ordem
$arvore->rewind();
while ($arvore->valid()) {
    echo $arvore->current() . " o-que-e.md";
    $arvore->next();
}
// Output: 3 5 7 10 12 15 20
~~~

**LIFO (Last-In, First-Out) - Pilha (Stack):**
A estrutura de dados LIFO, também conhecida como pilha (stack), segue o princípio de que o último elemento adicionado é o primeiro a ser removido.
Imagine uma pilha de pratos. Quando você adiciona um novo prato, ele vai para o topo da pilha. Quando você precisa pegar um prato, você sempre pega o que está no topo. Esse é o funcionamento de uma pilha.
As principais operações em uma pilha são:

~~~
push():Adiciona um novo elemento no topo da pilha.
pop(): Remove e retorna o elemento no topo da pilha.
top() (ou peek()): Retorna o elemento no topo da pilha, sem removê-lo.
~~~

Pilhas são úteis em situações em que você precisa realizar operações "último a entrar, primeiro a sair", como desfazer (undo) ações, avaliar expressões matemáticas, implementar funcionalidades de navegação em aplicativos, etc.

**FIFO (First-In, First-Out) - Fila (Queue):**
A estrutura de dados FIFO, também conhecida como fila (queue), segue o princípio de que o primeiro elemento adicionado é o primeiro a ser removido.
Imagine uma fila de pessoas em um banco. A primeira pessoa a chegar é a primeira a ser atendida. Esse é o funcionamento de uma fila.
As principais operações em uma fila são:

~~~
enqueue(): Adiciona um novo elemento no final da fila.
dequeue(): Remove e retorna o elemento no início da fila.
peek(): Retorna o elemento no início da fila, sem removê-lo.
~~~

Filas são úteis em situações em que você precisa realizar operações "primeiro a entrar, primeiro a sair", como gerenciar solicitações em ordem de chegada, implementar sistemas de agendamento, processamento de tarefas, etc.
Em resumo:

**LIFO (Pilha):** Último a entrar, primeiro a sair.
**FIFO (Fila):** Primeiro a entrar, primeiro a sair.

Essas propriedades de acesso e remoção de elementos são fundamentais para a compreensão e aplicação correta das estruturas de dados de pilha e fila em programação.

Cada uma dessas estruturas de dados tem suas próprias características e usos específicos, dependendo das necessidades do seu sistema. Por exemplo, arrays são ótimos para armazenar listas de itens, enquanto tabelas de hash são eficientes para pesquisas rápidas. Pilhas e filas são úteis para processamento de dados em ordem, e árvores são importantes para representar estruturas hierárquicas.
O importante é entender as propriedades e os casos de uso de cada estrutura de dados, para que você possa escolher a mais adequada para o seu problema.