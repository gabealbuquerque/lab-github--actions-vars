1. Secrets: O Mascaramento Automático
O GitHub possui um mecanismo de segurança chamado Redaction (Redação ou Mascaramento). Quando você define uma Secret:

Criptografia: O valor é armazenado de forma criptografada e só é descriptografado no momento em que o Runner (o servidor que executa o código) precisa utilizá-lo.

Varredura de Log: O Runner monitora tudo o que é enviado para o stdout (a saída padrão do terminal). Se ele detecta uma sequência de caracteres que corresponde exatamente ao valor de uma Secret, ele a substitui automaticamente por *** antes que o log seja gravado ou exibido na interface.

Objetivo: Evitar que dados sensíveis (senhas, tokens de API, chaves privadas) sejam expostos acidentalmente a qualquer pessoa que tenha acesso à visualização do repositório.

2. Variáveis: Transparência por Design
As Variáveis (Variables) são destinadas a dados de configuração que não são sensíveis:

Dados Públicos: Elas servem para guardar nomes de bancos de dados, URLs de endpoints de teste, nomes de arquivos ou configurações de ambiente (como NODE_ENV=production).

Sem Mascaramento: Como não há risco de segurança em exibir o nome de um servidor de homologação, o GitHub não gasta processamento filtrando esses valores. Eles aparecem no log para facilitar o debug (depuração), permitindo que você confirme se a automação está usando as configurações corretas.
