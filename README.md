'# Scope Recon

Framework Python para inventário de superfície de ataque em **CTFs, laboratórios próprios e auditorias formalmente autorizadas**.

> Descubra ativos no escopo, registre evidências e gere um relatório estruturado. Sem exploração, brute force ou ações destrutivas.

## O que ele faz

1. Valida um alvo contra uma lista explícita de escopo autorizado.
2. Coleta subdomínios usando um provedor local configurável.
3. Executa inventário de portas e versões com o Nmap instalado localmente.
4. Converte o resultado XML para JSON limpo.
5. Associa serviços a referências públicas de correção, sem baixar exploits.
6. Exporta relatório e log de auditoria.

## Princípios de segurança

- Rode apenas em ativos que você possui ou tem autorização documentada para testar.
- O escopo é obrigatório: alvos fora dele são bloqueados antes de qualquer execução.
- Não há módulos de brute force, exploração, SQL injection ou persistência.
- Resultados servem para priorizar correções, não para atacar sistemas.

## Estrutura

```text
scope-recon/
├── src/scope_recon/
│   ├── cli.py          # comando de entrada
│   ├── scope.py        # validação de escopo
│   ├── collectors.py   # adaptadores de descoberta autorizada
│   ├── nmap_parser.py  # XML para JSON
│   └── report.py       # relatório e log
├── tests/
├── config.example.json
└── README.md
```

## Começo rápido

```bash
python -m pip install -e .
cp config.example.json config.json
scope-recon run --config config.json --target lab.example.test
```

Exemplo de `config.json`:

```json
{
  "authorized_domains": ["lab.example.test", "example.internal"],
  "output_directory": "reports",
  "max_workers": 4,
  "nmap_arguments": ["-sV", "--open", "-T3"]
}
```

## Saída

Cada execução gera um JSON com alvo, horário, ativos encontrados, portas abertas, serviços identificados, referências de correção e erros registrados. Guarde o relatório como evidência da auditoria.

## Roadmap

- [ ] Adaptadores de descoberta por fontes passivas
- [ ] Parser XML de Nmap com testes
- [ ] Inventário com concorrência limitada
- [ ] Catálogo local de orientações de correção por serviço
- [ ] Relatórios JSON e Markdown
- [ ] Modo simulado para ensino e demonstração

## Contribuir

Pull requests são bem-vindos para melhorar qualidade de código, testes, parsers e documentação defensiva. Não serão aceitos módulos de exploração, evasão, brute force ou uso fora de escopo.

## Licença

MIT
','display_status':'Escrevendo documentação inicial# scope-recon
Framework Python de reconhecimento de superfície de ataque para escopos autorizados
