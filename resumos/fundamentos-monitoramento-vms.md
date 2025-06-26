# 📡 Monitoramento no Azure: Visibilidade e Resposta Proativa em VMs

O monitoramento eficaz de recursos no Azure é essencial para garantir **disponibilidade, desempenho e segurança** em ambientes de nuvem. Com foco em máquinas virtuais (VMs), este documento apresenta os principais conceitos, ferramentas e boas práticas.

## 🔍 Visão Geral

O Azure oferece uma série de serviços integrados para coleta, análise e resposta a eventos em tempo real. Os principais componentes incluem:

- **Azure Monitor**: Plataforma central de coleta de dados (métricas, logs e alertas)
- **Log Analytics**: Motor de análise com linguagem Kusto Query Language (KQL)
- **Activity Log**: Registro de operações administrativas feitas via portal, CLI, REST, etc.
- **Métricas**: Dados numéricos em tempo real, como uso de CPU, disco e rede
- **Action Groups**: Mecanismos de resposta automática (e-mail, webhook, runbooks)

## 📊 Diferença entre Logs e Métricas

| Tipo       | Características                            | Exemplos                            |
|------------|---------------------------------------------|-------------------------------------|
| **Métrica** | Dados em série temporal, frequência alta    | % de CPU, IOPS, taxa de transferência |
| **Log**     | Dados estruturados ou semi-estruturados     | Exclusão de VM, alertas, eventos de sistema |

## ⚠️ Tipos de Alertas

- **Baseado em Métricas**: disparado por limiares (ex: CPU > 90%)
- **Baseado em Logs**: disparado por eventos registrados (ex: exclusão de VM)

## 🧠 Exemplos de Consulta com KQL

```kusto
AzureActivity
| where OperationName == "Delete Virtual Machine"
| where ActivityStatusValue == "Succeeded"
| project TimeGenerated, ResourceGroup, Caller, OperationName
```

## 🧩 Boas Práticas
  * Habilitar diagnóstico em todos os recursos importantes

  * Armazenar logs no Log Analytics para consultas históricas

  * Configurar alertas para ações administrativas sensíveis

  * Usar **Action Groups** com múltiplos canais (e-mail + webhook)

## 📝 Recomendações
  * 🔐 Monitorar operações como delete, start, stop, update

  * 💬 Documentar alertas críticos no repositório de governança

  * 📦 Utilizar políticas Azure Policy para garantir que logs estejam habilitados por padrão
