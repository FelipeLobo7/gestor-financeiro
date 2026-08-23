# Gestor do E-commerce

Sistema web com dois módulos:

- gestor financeiro sincronizado com Supabase;
- precificador Amazon para DBA, FBA, FBA Onsite e logística própria.

O site possui tema claro/escuro, opções avançadas recolhidas por padrão, comissão
zero promocional e tarifa fixa promocional do FBA configurável (R$ 6,00 por padrão).
Essas promoções devem ser desmarcadas quando deixarem de valer na conta Amazon.

## Ativação do precificador

1. Abra o SQL Editor do projeto no Supabase.
2. Copie todo o conteúdo de `criar_precificacoes.sql`.
3. Execute com **Run**. A mensagem esperada é `Success. No rows returned`.
4. Publique `index.html`, `precificador.css`, `precificador.js` e este SQL no GitHub.

O cálculo continua funcionando sem a nova tabela, mas salvar e reabrir produtos só
fica disponível depois da execução do SQL.

Para repetir os testes automáticos dos cálculos, execute no terminal:

```bash
node testar_precificador.js
```

## Segurança e atualização de tarifas

As precificações pertencem ao usuário autenticado e são protegidas por RLS no
Supabase. As tabelas do cálculo têm a data-base exibida na tela. Antes de publicar
um preço, confirme promoções, tarifas específicas da conta e a tributação vigente.
