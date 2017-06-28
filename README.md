# xml_parser

Processa a fila de arquivos XMLs, via cron.d, de duas categorias:
 1 - XMLs OfficeTrack
 2 - XMLs ServiceNow
 
Na categoria 1 processa os arquivos encontrados em /opt/files/xmls/to_process/OfficeTrack/
movendo o arquivo para a pasta onde será lido pelo OdooImporter e com o seguinte formato:
  CCC_SSS_VVV_XXXXXXXXXXXXX_AAAAMMDD_HHMMSS_BRT_ID.xml

  Onde:
    CCC = código que identifica o tipo de formulário
    SSS = a subdivisão do formulário, quando houver
    VVV = a versão do formulário, onde o primeiro caracter identifica D para desenvolvimento e P para produção
    XXXX = número da TASK ou INC no ServiceNow
    AAAA = Ano
    MM = mês
    DD = dia
    hh = hora
    mm = minuto
    ss = segundos
    BRT = Timezone
    ID = String aleatória para garantir unicidade dos arquivos

  A pasta de destino é /opt/files/xmls/ccc/ , onde ccc é a versão em caixa baixa do código que identifica o tipo de formulário.

Na categoria 2 processa os arquivos encontrados em /opt/files/xmls/to_process/ServiceNow/
moovendo o arquivo para a pasta onde será lido pelo OdooImporter e com o seguinte formato:
  NNN_ZZZ_XXXXXXXXXXXXX_AAAAMMDD_HHMMSS_BRT_ID.xml
  
  Onde:
    NNN = INC para XMLs de incidente e TSK para XMLs de TASKs
    ZZZ = OPN para XMLs de abertura de eventos e CLS para XMLs de fechamento de eventos

  A pasta de destino é /opt/files/xmls/srvnow/ 