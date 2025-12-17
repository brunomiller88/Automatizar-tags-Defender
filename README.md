# Automatizar-tags-Defender
A aplicação manual de Device Tags no Microsoft Defender XDR pode se tornar inviável em ambientes médios e grandes, principalmente quando há segmentação por área, criticidade ou função do dispositivo.
📌 Contexto

A aplicação manual de Device Tags no Microsoft Defender XDR pode se tornar inviável em ambientes médios e grandes, principalmente quando há segmentação por área, criticidade ou função do dispositivo.

Para resolver esse problema, é possível automatizar totalmente a aplicação dessas tags utilizando políticas de configuração no Microsoft Intune, garantindo:

Padronização

Escalabilidade

Governança

Redução de esforço operacional

Este repositório demonstra como implementar essa automação de ponta a ponta, utilizando OMA-URI oficialmente suportada pela Microsoft.

🎯 Objetivo

Automatizar a aplicação de Device Tags no Microsoft Defender por meio de:

Políticas de configuração no Microsoft Intune

Associação com grupos do Entra ID

Consumo automático dessas tags nos Device Groups do Defender XDR

🧩 Visão geral da solução

Fluxo da automação:

Criar um perfil de configuração personalizado no Intune

Definir a OMA-URI de Device Tagging do Defender

Atribuir o perfil a um grupo do Entra ID

Aguardar a replicação nos dispositivos

Criar ou ajustar Device Groups no Defender XDR com base na tag

Validar os dispositivos automaticamente tagueados

🛠️ Pré-requisitos

Microsoft Intune ativo

Microsoft Defender for Endpoint onboardado

Dispositivos Windows 10 ou posterior

Permissões administrativas no Intune e Defender

Grupos de usuários ou dispositivos no Entra ID

🚀 Passo a passo
1️⃣ Criar o perfil de configuração no Intune

No Centro de administração do Microsoft Intune:

Caminho:

Dispositivos → Configuração → Criar perfil

Configuração:

Plataforma: Windows 10 e posterior

Tipo de perfil: Modelos

Modelo: Personalizado

![tag001](tag001.png)


2️⃣ Configurar o OMA-URI de Device Tagging

Dentro do perfil Personalizado, adicione uma nova configuração OMA-URI:

Nome: (exemplo) TECNOLOGIA DA INFORMACAO - 2207

Descrição: mesma nomenclatura (recomendado)

OMA-URI:

./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/DeviceTagging/Group

Tipo de dados: Cadeia de caracteres (String)

Valor:

TECNOLOGIA DA INFORMACAO - 2207

📌 Boa prática:
Utilizar exatamente a mesma nomenclatura para nome, descrição e valor facilita:

Governança

Leitura

Auditoria

Criação dos Device Groups no Defender

![tag001](tag002.png)

![tag001](tag003.png)


3️⃣ Atribuir o perfil a um grupo do Entra ID

Na etapa Atribuições:

Inclua o grupo do Entra ID desejado
(ex: TI - Adubos Real)

![tag001](tag004.png)

![tag001](tag005.png)


Finalize a criação do perfil.

4️⃣ Validar a aplicação no Intune

Após a replicação da política:

Acesse o perfil criado

Verifique o status de check-in

Confirme que o dispositivo recebeu a política com sucesso

![tag001](tag006.png)


ℹ️ A replicação pode levar alguns minutos, dependendo do ambiente.

5️⃣ Criar ou ajustar o Device Group no Defender XDR

No Microsoft Defender XDR:

Caminho:

Configurações → Ponto de extremidade → Device groups

Crie um novo grupo ou edite um existente:

Filtro:

Campo: Device tag

Operador: Equals

Valor: TECNOLOGIA DA INFORMACAO - 2207

Clique em Show preview para validar os dispositivos.

![tag001](tag007.png)

![tag001](tag008.png)


6️⃣ Validar os dispositivos tagueados

Por fim:

Acesse Devices no Defender

Abra um dispositivo que recebeu a política

Confirme a Device Tag aplicada automaticamente

![tag001](tag009.png)

![tag001](tag010.png)


✅ Resultado final

Os dispositivos passam a ser automaticamente tagueados

Os Device Groups do Defender passam a ser populados sem ação manual

A hierarquia e automação de resposta funcionam corretamente

Escalabilidade garantida para novos dispositivos

🔐 Boas práticas

Sempre mantenha nomenclatura padronizada

Utilize grupos do Entra ID bem definidos

Posicione corretamente os Device Groups no Defender (ordem hierárquica)

Evite múltiplas tags conflitantes por dispositivo

📚 Referência oficial

Documentação Microsoft:

Use device tags to create and manage device groups

WindowsAdvancedThreatProtection CSP

🧠 Considerações finais

Essa abordagem elimina completamente a necessidade de:

Taguear dispositivos manualmente

Ajustar grupos constantemente

Manter controles paralelos fora do Defender

Além disso, melhora:

Governança

Secure Score

Capacidade de resposta a incidentes

Organização do ambiente

📌 Este repositório pode ser adaptado para qualquer área, departamento ou criticidade apenas alterando o valor da tag e o grupo de atribuição.
