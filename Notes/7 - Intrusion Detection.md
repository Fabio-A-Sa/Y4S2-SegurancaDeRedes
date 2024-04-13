# Intrusion Detection (Systems)

Os intrusos podem ser detectados:

- No `Host`, olhando para os dados do sistema operativo e das aplicações usadas;
- Na `Network`, olhando para o tráfico da rede;

Podem ser ambos tratados na perspectiva de detecção e de prevenção.

Saber o que verificar para ocorrer ou não um ataque. Pode ser **knowledge-based**, já com conhecimento prévio (através de regras) ou **behavior-based**, aprendendo com os dados disponíveis (através de treinamento).

IPS são diferentes das Firewalls porque, embora ambas tenham regras, as firewalls também conseguem inspecionar *packet payloads*. Firewalls são na sua maioria baseadas em regras, que têm uma grande diferença das `behaviour-based`.

### Behavior-based IDS

para detecção de anomalias, através de *learning from data*: aprende o normal funcionamento com a normalidade da aplicação, e depois trata-se de um problema de classificação.

## Network data types

- `Packet traces`: 
- `Counters`: 
- `Flow data`: 
- `Others`: 

