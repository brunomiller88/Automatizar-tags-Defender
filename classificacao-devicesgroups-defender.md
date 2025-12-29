como funciona a prioridade (Rank) dos Device Groups no Microsoft Defender for Endpoint

No Microsoft Defender for Endpoint, os Device Groups utilizam um mecanismo de prioridade chamado Rank para resolver conflitos quando um mesmo dispositivo pertence a mais de um grupo.

Objetivo do Rank

O Rank define qual grupo terá autoridade final sobre o comportamento de segurança do dispositivo.

![Criação do Device Group no Defender](001.png)

Quanto menor o número do Rank, maior a prioridade.

Rank 1 → prioridade máxima

Rank 5 → prioridade menor

Rank 10 → prioridade ainda menor

Regra fundamental do Defender

Um dispositivo só pode herdar configurações de UM Device Group por vez.

Quando um dispositivo está presente em vários grupos:

O Defender avalia os Ranks

Aplica somente o grupo com o MENOR Rank

Todos os demais grupos são ignorados para aquele dispositivo

Não existe soma, herança parcial ou mesclagem de configurações.

O que exatamente é decidido pela prioridade?

O Device Group vencedor (menor Rank) define como o Defender reage a incidentes naquele dispositivo, incluindo:

Remediation level

Full remediation

Semi (com aprovação)

No automated response

Automated Investigation & Response (AIR)

Se o Defender pode agir sozinho ou apenas alertar

Permissões administrativas

Quem pode isolar o dispositivo

Quem pode executar ações de resposta

Escopo operacional de segurança

Grupos críticos

Exceções

Ambientes sensíveis ou legados

Todas essas decisões vêm exclusivamente do grupo de maior prioridade.

O que a prioridade NÃO controla

O Rank não interfere em políticas aplicadas via Intune ou Entra ID, como:

BitLocker

ASR Rules

Firewall

Antivirus policies

Compliance policies

Essas configurações são avaliadas fora do conceito de Device Group do Defender.
