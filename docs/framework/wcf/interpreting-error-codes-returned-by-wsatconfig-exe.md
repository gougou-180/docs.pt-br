---
title: Interpretando os códigos de erro retornados pelo wsatConfig.exe
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 0a65bea68f595e5e28c05a142ecdd9589f12bed5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321042"
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interpretando os códigos de erro retornados pelo wsatConfig.exe
Este tópico lista todos os códigos de erro gerados pelo utilitário de configuração WS-AtomicTransaction (wsatConfig. exe) e as ações recomendadas a serem executadas.  
  
## <a name="list-of-error-codes"></a>Lista de códigos de erro  
  
|Código do erro|Descrição|Ação recomendada a ser executada|  
|----------------|-----------------|------------------------------------|  
|0|A operação foi bem-sucedida|Nenhum|  
|1|Erro inesperado|Contate a Microsoft|  
|2|Ocorreu um erro inesperado ao tentar contatar o MSDTC para recuperar suas configurações de segurança.|Verifique se o serviço MSDTC não está desabilitado e resolva todos os problemas listados na exceção retornada.|  
|3|A conta sob a qual o WsatConfig. exe foi executado não tinha permissões suficientes para ler as configurações de segurança de rede.|Execute WsatConfig. exe em uma conta de usuário administrador.|  
|4|Habilite "acesso de DTC de rede" para o MSDTC antes de tentar habilitar o suporte WS-AT.|Habilite "acesso de DTC de rede" para o MSDTC e execute novamente o utilitário.|  
|5|A porta inserida estava fora do intervalo. O valor deve estar no intervalo de 1 a 65535.|Corrigir o `-port:<portNum>`<br /><br /> opção de linha de comando, conforme indicado na mensagem de erro.|  
|6|Um certificado de ponto de extremidade inválido foi especificado na linha de comando.  Não foi possível encontrar o certificado ou ele não passou na verificação.|Corrija a opção de linha de comando `-endpointCert`. Verifique se o certificado tem uma chave privada, se destina a ser usado para clientauthentication válido e autenticação, está instalado no repositório de certificados LocalMachine\MY e é totalmente confiável.|  
|7|Um certificado de contas inválido foi especificado na linha de comando.|Corrija a opção de linha de comando `-accountsCerts`. O certificado especificado foi especificado incorretamente ou não pôde ser encontrado.|  
|8|Um tempo limite padrão foi especificado fora do intervalo de 1 a 3600 segundos.|Insira um valor de tempo limite padrão correto, conforme indicado.|  
|10|Ocorreu um erro inesperado ao tentar acessar o registro.|Verificar a mensagem de erro e o código de erro para itens acionáveis|  
|11|Não é possível gravar no registro.|Verifique se a chave listada na mensagem de erro é capaz de dar suporte ao acesso do registro da conta WsatConfig. exe foi executada em.|  
|12|Ocorreu um erro inesperado ao tentar acessar o repositório de certificados.|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|13|Falha na configuração de http. sys. Não é possível criar uma nova reserva de porta HTTPS para o MSDTC.|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|14|Falha na configuração de http. sys. Não é possível remover a reserva de porta HTTPS anterior para o MSDTC.|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|15|Falha na configuração de http. sys. Já existe uma reserva de porta HTTPS anterior para a porta especificada.|Outro aplicativo já assumiu a propriedade da porta específica. Altere para uma porta diferente ou desinstale ou reconfigure o aplicativo atual.|  
|16|Falha na configuração de http. sys. Não é possível associar o certificado especificado à porta.|Use o código de erro retornado na mensagem de erro para mapear para o erro de sistema apropriado|  
|17|Falha na configuração de http. sys. Não é possível desassociar o certificado SSL da porta anterior.|Use o código de erro retornado na mensagem de erro para mapear para o erro de sistema apropriado. Se necessário, use Httpcfg. exe ou netsh. exe para remover as reservas de porta erradas.|  
|18|Falha na configuração de http. sys. Não é possível associar o certificado especificado à porta porque já existe uma associação SSL anterior.|Outro aplicativo já assumiu a propriedade da porta específica. Altere para uma porta diferente ou desinstale ou reconfigure o aplicativo atual.|  
|19|Falha ao reiniciar o MSDTC|Reinicie manualmente o MSDTC, se necessário. Se o problema persistir, contate a Microsoft.|  
|20|O WinFX não está instalado no computador remoto ou não está instalado corretamente.|Instale o WinFX no computador.|  
|21|A configuração remota falhou devido à operação atingir o tempo limite.|A chamada para configurar o WS-AT no computador remoto deve levar mais de 90 segundos.|  
|22|O WinFX não está instalado no computador remoto ou não está instalado corretamente.|Instale o WinFX no computador.|  
|23|A configuração remota falhou devido a uma exceção no computador remoto.|Verificar a mensagem de erro para itens acionáveis|  
|26|Um argumento inválido foi passado para WsatConfig. exe.|Verifique se há erros na linha de comando.|  
|27|A opção de linha de comando `-accounts` era inválida.|Corrija a opção de linha de comando-`accounts` para especificar corretamente uma conta de usuário.|  
|28|A opção de linha de comando `-network` era inválida.|Corrija a opção de linha de comando `-network` para especificar corretamente "habilitar" ou "Desabilitar".|  
|29|A opção de linha de comando `-maxTimeout` era inválida.|Corrija a opção de linha de comando `-maxTimeout`, conforme indicado.|  
|30|A opção de linha de comando `-timeout` era inválida.|Corrija a opção de linha de comando `-timeout`, conforme indicado.|  
|31|A opção de linha de comando `-traceLevel` era inválida.|Corrija a opção de linha de comando `-traceLevel` para especificar um valor válido a partir dos seguintes,<br /><br /> -Desativado<br />-Erro<br />–   Crítica<br />-Aviso<br />-Informações<br />-Detalhado<br />-Todos|  
|32|A opção de linha de comando `-traceActivity` era inválida.|Corrija a opção de linha de comando `-traceActivity` especificando "habilitar" ou "Desabilitar".|  
|33|A opção de linha de comando `-traceProp` era inválida.|Corrija a opção de linha de comando `-traceProp` especificando "habilitar" ou "Desabilitar".|  
|34|A opção de linha de comando `-tracePII` era inválida.|Corrija a opção de linha de comando `-tracePII` especificando "habilitar" ou "Desabilitar".|  
|37|WsatConfig. exe não pôde determinar o certificado exato da máquina. Isso pode acontecer quando há mais de um candidato, ou quando não existe nenhum.|Especifique um par de impressão digital ou Issuer\SubjectName de certificado para identificar corretamente o certificado exato a ser configurado.|  
|38|O processo ou o usuário não tem permissões suficientes para alterar a configuração do firewall.|Execute WsatConfig. exe em uma conta de usuário administrador.|  
|39|WsatConfig. exe encontrou um erro ao atualizar a configuração do firewall.|Verifique a mensagem de erro para itens acionáveis.|  
|40|WsatConfig. exe não é capaz de conceder acesso de leitura de MSDTC ao arquivo de chave privada do certificado|Execute WsatConfig. exe em uma conta de usuário administrador.|  
|41|Nenhuma instalação do WinFX foi encontrada ou a versão encontrada não corresponde ao que a ferramenta é capaz de configurar.|Verifique se o WinFX está corretamente instalado e use a ferramenta WsatConfig. exe que veio com essa versão do WinFX para configurar o WS-AT.|  
|42|Um argumento foi especificado mais de uma vez na linha de comando.|Especifique apenas cada argumento uma vez ao executar WsatConfig. exe.|  
|43|WsatConfig. exe não poderá atualizar as configurações do WS-AT se WS-AT não estiver habilitado.|Especifique `-network:enable` como um argumento de linha de comando adicional.|  
|44|Um hotfix necessário está ausente e WS-AT não pode ser configurado até que o hotfix seja instalado.|Consulte as notas de versão do WinFX para obter instruções sobre como instalar o hotfix necessário.|  
|45|A opção de linha de comando `-virtualServer` era inválida.|Corrija a opção de linha de comando `-virtualServer` especificando o nome de rede do recurso de cluster no qual configurar.|  
|46|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|47|O processo ou o usuário não tem permissões suficientes para habilitar a sessão de rastreamento ETW.|Execute WsatConfig. exe em uma conta de usuário administrador.|  
|48|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Contate a Microsoft.|  
|49|Não é possível criar um novo arquivo de log devido a espaço insuficiente no% systemdrive%|Verifique se o% systemdrive% tem espaço adequado para o arquivo de log.|  
|51|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Contate a Microsoft.|  
|52|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Contate a Microsoft.|  
|53|O backup do arquivo de log da sessão ETW anterior não foi bem-sucedido.|Verifique se o% systemdrive% tem espaço adequado para o arquivo de log e o backup do arquivo de log anterior (se houver). Remova o arquivo de log anterior manualmente, se necessário.|  
|55|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Contate a Microsoft.|  
|56|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Contate a Microsoft.|  
  
## <a name="see-also"></a>Consulte também

- [Utilitário de configuração de WS-AtomicTransaction (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
