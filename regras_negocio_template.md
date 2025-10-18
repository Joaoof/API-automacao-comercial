# 📘 Documento de Requisitos & Regras de Negócio — v0.1

## 1. Visão Geral
- **Nome do Projeto:**  
- **Descrição Curta:**  
- **Objetivo do Sistema:**  
- **Data / Versão do Documento:**  
- **Autores / Contato:**  

---

## 2. Stakeholders
| Papel | Nome | Contato | Observações |
|-------|------|----------|--------------|
| Dono da Loja |  |  |  |
| Caixa / Operador |  |  |  |
| Contabilidade / Financeiro |  |  |  |
| Equipe Técnica |  |  |  |

---

## 3. Escopo
- **Incluído no MVP:**  
  -  
- **Fora do Escopo (por enquanto):**  
  -  

---

## 4. Visão de Alto Nível / Fluxos Principais
Descreva cada fluxo principal:
- **Venda via Cielo → registro automático:**  
- **Venda em dinheiro → operador fecha caixa:**  
- **Fluxo de Estorno / Chargeback:**  
- **Geração e envio do relatório diário:**  

> (Desenhe os fluxos ou anexe um diagrama depois)

---

## 5. Requisitos Funcionais (RF)
| ID | Descrição | Prioridade | Critério de Aceite | Usuário Afetado |
|----|-------------|-------------|--------------------|-----------------|
| RF-001 |  | Must |  |  |
| RF-002 |  | Should |  |  |

**Perguntas guia:**
- O que precisa ser automatizado?
- Quais operações são manuais no MVP?
- Existem níveis de permissão?
- Precisamos de histórico / reversão de ações?

---

## 6. Requisitos Não-Funcionais (RNF)
- **Disponibilidade:**  
- **Performance:**  
- **Segurança:**  
- **Escalabilidade:**  
- **Backup / RPO / RTO:**  
- **Formato de Moeda / Localidade:**  

---

## 7. Regras de Negócio (RN)
### RN-001 — Nome da Regra
- **Descrição:**  
- **Regra Formal (if/then):**  
- **Exemplo:**  
- **Exceções / Notas:**  

### RN-002 — Nome da Regra
- **Descrição:**  
- **Fórmula (se aplicável):**  
- **Critério de Aceite:**  

**Perguntas guia:**
- Como classificar pagamentos?  
- Como calcular lucro líquido?  
- Quando gerar o relatório diário?  
- Como lidar com estornos, taxas e parcelas?

---

## 8. Modelagem de Dados (Entidades / Campos)
### Loja
- id  
- nome  
- cnpj  
- timezone  
- owner_id  
- configs  

### Usuário
- id  
- nome  
- role  
- email  
- telefone  

### Transação / Venda
- id  
- loja_id  
- cielo_tx_id  
- data_hora  
- valor_total  
- tipo_pagamento  
- taxa_cielo  
- status  

### Saída (Despesa)
- id  
- loja_id  
- data  
- valor  
- categoria  
- observação  

### Relatório Diário
- id  
- loja_id  
- data  
- entradas_total  
- saídas_total  
- lucro_liquido  
- breakdown_pagamentos  

---

## 9. Integrações / APIs Externas
| Integração | Tipo | Objetivo | Dados Recebidos | Dados Enviados | Autenticação |
|-------------|------|-----------|-----------------|----------------|---------------|
| Cielo | REST / Webhook | Registrar vendas automáticas |  |  |  |
| WhatsApp (Twilio/Z-API) | REST | Enviar relatórios |  |  |  |

---

## 10. Webhooks & Eventos
| Evento | Tipo | Descrição | Payload Exemplo |
|---------|------|------------|-----------------|
| transaction.approved | Receber | Notificação de venda aprovada |  |
| report.generated | Emitir | Relatório diário gerado |  |

---

## 11. Relatórios / Templates
**Relatório Diário**
- Data:  
- Loja:  
- Entradas:  
  - Cartão:  
  - Dinheiro:  
  - Pix:  
- Saídas:  
- Lucro Líquido:  
- Variação vs Dia Anterior:  
- Observações:  

---

## 12. Regras de Notificação & SLA
- Quando enviar alerta de caixa negativo?  
- Quem recebe notificações críticas?  
- SLA de processamento (ex: 99% em <2min):  

---

## 13. Permissões & Segurança
| Role | Pode Ver | Pode Editar | Pode Excluir | Observações |
|------|-----------|--------------|---------------|--------------|
| Admin | ✅ | ✅ | ✅ |  |
| Gerente | ✅ | ✅ | ❌ |  |
| Operador | ✅ | ❌ | ❌ |  |

- Autenticação (ex: JWT / OAuth2 / 2FA):  
- Logging / Auditoria:  

---

## 14. Erros Comuns & Tratamento
| Erro | Causa | Estratégia de Tratamento |
|------|--------|--------------------------|
| Falha webhook Cielo | Timeout | Retry automático (x3, 5s backoff) |
| Transação duplicada | Payload repetido | Deduplicar por `cielo_tx_id` |

---

## 15. Métricas & KPIs
- Tempo médio de sincronização da Cielo  
- Taxa de conciliação automática (%)  
- Tempo médio para gerar relatório diário  
- Número de transações por dia  

---

## 16. Requisitos Operacionais / Deploy
- Ambientes: dev / staging / prod  
- Backup diário / semanal  
- Monitoramento (Sentry, Prometheus, etc)  
- Política de rollback  

---

## 17. Perguntas em Aberto
-  
-  
-  

---

## 18. Glossário
| Termo | Definição |
|--------|------------|
| Entrada |  |
| Saída |  |
| Lucro Líquido |  |
| Conciliação |  |

---

## 19. Anexos / Referências
- [Link da documentação da Cielo](https://developercielo.github.io/)  
- Payloads de exemplo  
- Prints de telas ou diagramas

---

✅ **Checklist Final**
- [ ] Todas as regras de negócio enumeradas  
- [ ] Entidades com campos definidos  
- [ ] Endpoints/integrações documentados  
- [ ] Critérios de aceite claros  
- [ ] Perguntas em aberto listadas
