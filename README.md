# ${DASHBOARD_TITLE}

Dashboard Grafana para monitoramento HTTP e ICMP via Blackbox Exporter + Prometheus.

## Pré-requisitos

- Grafana
- Prometheus
- Blackbox Exporter configurado com módulos `http_2xx` e `icmp`

## Como usar

### 1. Substitua as variáveis no JSON

Antes de importar, edite o arquivo `dashboard.json` e substitua:

| Placeholder | Descrição | Exemplo |
|---|---|---|
| `${DASHBOARD_TITLE}` | Nome do dashboard | `Meu Monitoring` |
| `${PROMETHEUS_DS_UID}` | UID do datasource Prometheus no seu Grafana | `abc123xyz` |
| `${INSTANCE_1}` | URL completa da primeira instância HTTP | `https://app.exemplo.com/login` |
| `${INSTANCE_2}` | URL completa da segunda instância HTTP | `https://painel.exemplo.com/login` |
| `${ICMP_INSTANCE_1}` | Hostname da primeira instância para ping | `app.exemplo.com` |
| `${ICMP_INSTANCE_2}` | Hostname da segunda instância para ping | `painel.exemplo.com` |
| `CHANGE_ME` | UID do dashboard (pode deixar vazio para gerar automático) | `meu-dashboard-01` |

> Para achar o UID do datasource Prometheus: **Grafana → Connections → Data sources → Prometheus → copie o UID da URL**.

### 2. Importe o dashboard

**Grafana → Dashboards → Import → Upload JSON file**

## Métricas monitoradas

- Ping (ICMP)
- HTTP Response Time
- HTTP Status Code
- Probe Success (UP/DOWN)
- Latência avg / p95 / p99
- Uptime 5m e 30d
- SSL Certificate Expiry
- TCP Connect Time
- DNS Resolution Time
- TLS Handshake Time
- HTTP Error Rate
- Incident History

## Observações

- O painel **Uptime 30d** requer que o Prometheus retenha pelo menos 30 dias de dados
- O dashboard atualiza a cada **5 segundos**
- Suporta múltiplas instâncias simultaneamente via seletor **Multi-value**
