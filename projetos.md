## GRUPO 1 - Mãos que Criam - Marketplace de Artesanato Feminino

Marketplace exclusivo para mulheres artesãs do Alto Solimões. Cada artesã tem sua vitrine, gerencia seus produtos e recebe pedidos. A plataforma valoriza o protagonismo feminino na economia criativa local, intermedia compras, avaliações e comissão.

### Problemática

Mulheres artesãs da região do Alto Solimões — muitas delas chefes de família, indígenas, ribeirinhas e mães solo — produzem peças de alto valor cultural que sustentam suas casas, mas vendem majoritariamente em feiras locais ou via redes sociais, sem vitrine profissional, sem controle de pedidos, sem histórico de vendas e sem alcance fora da região. Plataformas genéricas (Mercado Livre, Shopee) cobram comissões altas, não valorizam a identidade do artesanato local e diluem a artesã em meio a produtos industriais. Há ainda a invisibilidade histórica do trabalho feminino artesanal: o ofício é passado de mãe para filha há gerações, mas raramente é reconhecido como atividade econômica formal. Falta um espaço digital que dê visibilidade coletiva ao trabalho dessas mulheres, preserve a identidade individual de cada artesã, gere autonomia financeira e fortaleça a rede de mulheres produtoras da região.

### Escopo

- Cadastro de artesãs com vitrine própria (foto, bio, história pessoal, localização, técnica/ofício)
- Destaque para artesãs em situação de vulnerabilidade (mães solo, indígenas, ribeirinhas)
- Cadastro de produtos com múltiplas imagens, categorias e estoque
- Catálogo público navegável por categoria, artesã, técnica ou busca
- Página "Conheça a artesã" com história e processo de produção
- Carrinho de compras e checkout (pagamento simulado)
- Fluxo de pedido: criação → pagamento → preparação → envio → entregue
- Avaliação de produto e de artesã pós-compra
- Cálculo de comissão da plataforma sobre cada venda
- Painel da artesã: vendas, pedidos pendentes, faturamento, evolução mensal
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

## GRUPO 4 - Olho na Rua - Plataforma de Denúncias de Descarte Irregular

Plataforma cívica para denúncia de descarte irregular de resíduos. Qualquer cidadão registra a denúncia com foto e geolocalização; agentes públicos recebem, atendem e atualizam o status; toda a comunidade acompanha em um mapa público as denúncias e resoluções na cidade.

### Problemática

O descarte irregular de lixo, entulho, móveis velhos, eletrônicos e resíduos químicos é um problema crônico em cidades brasileiras, com impacto direto na saúde pública (foco de dengue, leptospirose), no meio ambiente (contaminação de igarapés, várzeas e nascentes na Amazônia) e na drenagem urbana (alagamentos). Os canais atuais de denúncia — telefone 156, WhatsApp da prefeitura, redes sociais — são fragmentados, não fornecem rastreabilidade, raramente dão retorno ao denunciante e não geram dados consolidados que permitam ao poder público identificar pontos críticos recorrentes. O cidadão sente que denunciar não muda nada; o fiscal não tem fila organizada de atendimento; o gestor não tem mapa de calor das ocorrências. Falta uma plataforma única, transparente e georreferenciada que conecte denunciante, fiscalização e sociedade.

### Escopo

- Registro de denúncia com foto, descrição, geolocalização e tipo de resíduo
- Denúncia anônima ou identificada (denunciante autenticado)
- Categorização do resíduo (entulho, lixo doméstico, eletrônico, químico, orgânico, móveis)
- Mapa público de denúncias com filtros por tipo, status e período
- Atribuição automática ou manual do caso ao fiscal responsável pela zona
- Fluxo de status: recebida → em análise → em atendimento → resolvida / arquivada / improcedente
- Histórico completo de mudanças de status e comentários públicos do agente
- Galeria "antes e depois" da resolução
- Painel do fiscal: casos atribuídos, fila por prioridade, mapa da zona
- Painel administrativo: estatísticas por zona, tipos mais frequentes, tempo médio de resolução, ranking de pontos críticos
- RBAC: admin, fiscal, cidadão, visitante (anônimo)

**Entidades:** `users`, `citizens`, `agents`, `zones`, `waste_categories`, `reports`, `report_images`, `report_status_history`, `report_comments`, `assignments`.
