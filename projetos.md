## GRUPO 1 - Mãos que Criam - Marketplace de Artesanato

Marketplace multi-vendedor focado em artesanato feminino. Cada artesã tem sua vitrine, gerencia seus produtos e recebe pedidos. A plataforma intermedia compras, avaliações e comissão.

### Problemática

Artesãs da região do Alto Solimões produzem peças de alto valor cultural, mas vendem majoritariamente em feiras locais ou via redes sociais, sem vitrine profissional, sem controle de pedidos, sem histórico de vendas e sem alcance fora da região. Plataformas genéricas (Mercado Livre, Shopee) cobram comissões altas, não valorizam a identidade do artesanato local e diluem a artesã em meio a produtos industriais. Falta um espaço digital que dê visibilidade coletiva preservando a identidade individual de cada artesã.

### Escopo

- Cadastro de artesãs com vitrine própria (foto, bio, localização)
- Cadastro de produtos com múltiplas imagens, categorias e estoque
- Catálogo público navegável por categoria, artesã ou busca
- Carrinho de compras e checkout (pagamento simulado)
- Fluxo de pedido: criação → pagamento → preparação → envio → entregue
- Avaliação de produto e de artesã pós-compra
- Cálculo de comissão da plataforma sobre cada venda
- Painel da artesã: vendas, pedidos pendentes, faturamento
- RBAC: admin, artesã, cliente

**Entidades:** `users`, `customers`, `artisans`, `shops`, `addresses`, `categories`, `products`, `product_images`, `carts`, `cart_items`, `orders`, `order_items`, `payments`, `reviews`.

---

## GRUPO 2 - SGA - Sistema de Gestão de Almoxarifado

Sistema para controlar entradas, saídas e requisições de materiais de uma instituição (ex.: o próprio CETAM). Almoxarifes registram movimentações; setores fazem requisições; aprovadores liberam.

### Problemática

Instituições públicas e privadas frequentemente gerenciam seus almoxarifados em planilhas Excel ou cadernos físicos, gerando perda de itens, divergência entre saldo registrado e saldo real, requisições sem rastreabilidade, falta de visibilidade sobre itens em ruptura ou em excesso, e impossibilidade de auditoria. Não há controle de quem solicitou, quem aprovou e quando o material foi entregue, comprometendo a transparência no uso de recursos públicos.

### Escopo

- Cadastro de itens com categoria, unidade de medida, estoque mínimo e máximo
- Cadastro de fornecedores e setores
- Registro de movimentações de entrada (compra, doação) e saída (consumo, descarte)
- Fluxo de requisição: solicitante cria → aprovador libera → almoxarife entrega
- Saldo atualizado automaticamente via trigger
- Alerta de itens abaixo do estoque mínimo
- Histórico completo de movimentações por item
- Relatórios: consumo por setor, itens críticos, giro de estoque
- RBAC: admin, almoxarife, aprovador, solicitante

**Entidades:** `users`, `sectors`, `suppliers`, `categories`, `units`, `items`, `stock_movements`, `requisitions`, `requisition_items`, `approvals`.

---



## GRUPO 3 - Mesa Digital - Cardápio e Comandas

Cardápio digital via QR code na mesa. Cliente abre comanda, faz pedidos com modificadores (sem cebola, ponto da carne), cozinha acompanha o status, garçom fecha conta com possibilidade de divisão.

### Problemática

Restaurantes de pequeno e médio porte ainda dependem de comandas em papel e anotações manuais do garçom, gerando pedidos errados, atrasos na cozinha, dificuldade de fechamento de conta (especialmente quando dividida entre vários clientes), retrabalho na hora de cobrar e ausência de dados sobre os itens mais vendidos. O cliente, por sua vez, espera o garçom para tudo: ver cardápio, pedir, pedir a conta. Em horários de pico, isso vira gargalo e prejudica a experiência.

### Escopo

- Cardápio público acessível via QR code da mesa
- Customização de pedidos com modificadores (ex.: ponto da carne, sem cebola)
- Abertura de comanda por mesa (múltiplos clientes na mesma comanda)
- Fluxo de pedido com status: solicitado → em preparo → pronto → entregue
- Painel da cozinha em tempo real
- Fechamento de conta com divisão por pessoa ou por item
- Pagamento parcial e múltiplos pagamentos por comanda
- Histórico de vendas e itens mais pedidos
- RBAC: gerente, garçom, cozinha, cliente (anônimo via QR)

**Entidades:** `users`, `tables`, `menu_categories`, `menu_items`, `modifiers`, `item_modifiers`, `tabs`, `orders`, `order_items`, `order_item_modifiers`, `payments`, `bill_splits`.

---

## GRUPO 4 Manganga - Plataforma do Coletivo

Plataforma do coletivo Manganga: cadastro de membros, geração de carteirinha digital com QR validável, catálogo público dos produtos dos membros e gestão de eventos com inscrição.

### Problemática

O coletivo Manganga reúne membros com perfis diversos (artesãs, voluntárias, colaboradoras) e realiza ações regulares (eventos, feiras, ações sociais), mas opera hoje sem sistema próprio: cadastros em planilhas, comunicação por WhatsApp, inscrições em eventos por formulário avulso, e nenhum mecanismo formal de identificação dos membros. Falta uma plataforma única que dê identidade ao coletivo, valide quem é membro ativo, exponha publicamente o trabalho dos integrantes e organize a participação em eventos — preservando a história e a memória institucional do grupo.

### Escopo

- Cadastro de membros com categoria (artesã, voluntária, colaboradora, fundadora)
- Histórico de filiação (ingresso, afastamento, reativação)
- Geração de carteirinha digital com número único e QR code
- Validação pública da carteirinha (qualquer pessoa escaneia e confirma se é membro ativo)
- Catálogo público de produtos vinculados aos membros
- Gestão de eventos com capacidade limitada e lista de espera
- Inscrição de membros em eventos com confirmação de presença
- Painel administrativo do coletivo (membros ativos, eventos, estatísticas)
- RBAC: admin, coordenador, membro, visitante

**Entidades:** `users`, `members`, `member_categories`, `memberships_history`, `cards`, `product_categories`, `products`, `product_images`, `event_categories`, `events`, `enrollments`, `attendances`.
