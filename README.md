# Scope Recon

Framework Python para inventário de superfície de ataque em **CTFs, laboratórios próprios e auditorias formalmente autorizadas**.

> Descubra ativos no escopo, registre evidências e gere um relatório estruturado. Sem exploração, brute force ou ações destrutivas.

## O que ele faz

- Valida o alvo contra uma lista explícita de escopo autorizado.
- Executa inventário de portas e versões com o Nmap instalado localmente.
- Converte o resultado XML em JSON limpo.
- Organiza evidências, falhas de execução e orientações de correção.
- Exporta relatórios para auditoria.

## Segurança por padrão

- Alvos fora do escopo são bloqueados antes de qualquer comando.
- Não inclui exploração, brute force, evasão, SQL injection ou persistência.
- Use apenas em ativos próprios, CTFs ou ambientes com autorização documentada.

## Estrutura

```text
src/scope_recon/
  cli.py          # entrada de linha de comando
  scope.py        # validação do escopo
  scanner.py      # execução limitada do Nmap
  nmap_parser.py  # XML para JSON
  report.py       # relatório e auditoria
```

## Uso

```bash
python -m pip install -e .
cp config.example.json config.json
scope-recon run --config config.json --target lab.example.test
```

## Exemplo de configuração

```json
{
  "authorized_domains": ["lab.example.test"],
  "output_directory": "reports",
  "nmap_arguments": ["-sV", "--open", "-T3"]
}
```

## Contribuir

Contribuições para testes, parsers, relatórios e documentação defensiva são bem-vindas. Módulos voltados a exploração ou uso fora de escopo não são aceitos.

## Licença

MIT
