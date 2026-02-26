FIRMWARE MARLIN 2.1 - ELEGOO NEPTUNE 2
=======================================

ESPECIFICACOES:
- Placa: MKS Robin Nano V1.2
- Display: MKS TFT35 (480x320 FSMC)
- Interface: TFT_COLOR_UI (Marlin Default Touch-Friendly)
- Data compilacao: 25/02/2026

TAMANHO DO FIRMWARE:
- Arquivo: Robin_nano35.bin
- Tamanho: 246.5 KB
- Flash usado: 48.1% (252444 / 524288 bytes)
- RAM usada: 81.7% (53560 / 65536 bytes)

CONFIGURACOES APLICADAS:
========================

VELOCIDADES E ACELERACOES (OTIMIZADAS):
- Velocidades max: XY=300mm/s, Z=15mm/s, E=120mm/s
- Aceleracoes max: XY=3000mm/s², Z=100mm/s², E=5000mm/s²
- Aceleracao impressao: 2000mm/s²
- Aceleracao retract: 3000mm/s²
- Aceleracao travel: 3000mm/s²
- Velocidade homing: XY=80mm/s, Z=15mm/s

HARDWARE ELEGOO NEPTUNE 2:
- Steps/mm: X=80, Y=80, Z=400, E=90
- Mesa: 235x235x260mm
- Temp max hotend: 270°C
- Temp max bed: 110°C
- Temp min extrusao: 170°C
- PID hotend: Kp=22.2, Ki=1.08, Kd=114

DRIVERS TMC2209 STANDALONE:
- X, Y, Z, E0: TMC2209_STANDALONE (sem UART - configurado via MS1/MS2)
- Correntes: XY=580mA RMS, Z=580mA RMS, E=650mA RMS
- Corrente homing: 400mA RMS (protecao em caso de colisao)
- Microstepping: 16 passos (com interpolacao 256x pelo TMC2209)
- Chopper: CHOPPER_DEFAULT_24V (correto para fonte 24V da Neptune 2)
- stealthChop: ATIVO abaixo de 80mm/s (XY) / 5mm/s (Z) / 50mm/s (E)
- HYBRID_THRESHOLD: spreadCycle acima dos thresholds (mais torque)

INPUT SHAPING (Anti-ghosting/ringing):
- INPUT_SHAPING_X: ATIVO - Freq: 35.0 Hz, Zeta: 0.1
- INPUT_SHAPING_Y: ATIVO - Freq: 35.0 Hz, Zeta: 0.1
- Calibrar com: M593 X F<freq> D<zeta> ; M593 Y F<freq> D<zeta>
- Menu de ajuste disponivel no TFT: Configuration > Input Shaping
- Salvar apos calibrar: M500

RECURSOS HABILITADOS:
- USB Serial (porta -1) - comunicacao via terminal
- EEPROM (M500/M501/M502) - salvar configuracoes
- SD Card support - leitura de arquivos
- TFT_COLOR_UI - interface touch completa
- Babystepping - ajuste Z em tempo real
- LCD_BED_TRAMMING - nivelamento manual dos cantos
- Fan control: HE1 (PB0) = hotend cooling fan ativa aos 50°C

TOUCH SCREEN:
- Calibracao: HABILITADA (primeira inicializacao)
- Auto-save na EEPROM: HABILITADO
- Calibrara apenas 1 vez e salvara automaticamente

INSTALACAO:
===========

1. Copie Robin_nano35.bin para o cartao SD (raiz)

2. Insira o cartao na impressora e ligue

3. Aguarde o flash automatico (LED piscando)

4. Desligue e religue a impressora

PRIMEIRA INICIALIZACAO (IMPORTANTE):
=====================================

1. Ao ligar pela primeira vez, a tela de CALIBRACAO DO TOUCHSCREEN
   sera exibida automaticamente

2. Toque nos 4 pontos indicados na tela quando solicitado
   (geralmente nos cantos da tela)

3. Apos calibrar os 4 pontos, a calibracao sera SALVA AUTOMATICAMENTE
   na EEPROM

4. A impressora reiniciara e o touchscreen funcionara perfeitamente

5. NAO SERA NECESSARIO CALIBRAR NOVAMENTE, a menos que execute M502
   (reset de fabrica)

APOS CALIBRACAO DO TOUCH:
==========================

1. Acesse: Configuration > Store Settings (M500)
   Isso salva todas as configuracoes de movimento e temperatura

2. Pronto! Sua impressora esta configurada e pronta para usar

RECURSOS DO MENU TFT_COLOR_UI:
===============================

TELA PRINCIPAL:
- Print: Selecionar e imprimir arquivos do SD
- Move: Movimento manual dos eixos (X, Y, Z, E)
- Temperature: Controle de temperaturas (hotend e bed)
- Configuration: Configuracoes e salvamento
- Level Corners: Nivelamento manual dos 4 cantos
- Home: Fazer homing dos eixos

SUBMENU CONFIGURATION:
- Store Settings (M500): Salvar configuracoes na EEPROM
- Load Settings (M501): Carregar configuracoes da EEPROM
- Restore Defaults (M502): Resetar para configuracoes de fabrica
- Level Corners: Nivelar cantos da mesa
- Babystep Z: Ajuste fino de Z durante impressao
- Touch Screen: Recalibrar touchscreen (se necessario)

DURANTE A IMPRESSAO:
- Pause/Resume: Pausar ou retomar impressao
- Babystep: Ajustar offset Z em tempo real
- Temperature: Ajustar temperaturas
- Speed/Flow: Ajustar velocidade e fluxo
- Stop: Cancelar impressao

COMANDOS GCODE UTEIS:
=====================

EEPROM:
M500 - Salvar configuracoes na EEPROM
M501 - Carregar configuracoes da EEPROM
M502 - Resetar para configuracoes de fabrica (requer nova calibracao do touch!)
M503 - Mostrar configuracoes atuais

TOUCHSCREEN:
M995 - Iniciar calibracao manual do touchscreen

BABYSTEP:
M290 Z0.1 - Ajustar baby step (+0.1mm)
M290 Z-0.1 - Ajustar baby step (-0.1mm)

MOVIMENTO:
G28 - Home all axes
G28 X Y - Home apenas X e Y
G28 Z - Home apenas Z

TEMPERATURAS:
M104 S200 - Definir temperatura hotend (200C)
M140 S60 - Definir temperatura bed (60C)
M109 S200 - Definir e AGUARDAR temperatura hotend
M190 S60 - Definir e AGUARDAR temperatura bed

OBSERVACOES IMPORTANTES:
========================

1. PRIMEIRA INICIALIZACAO: Calibre o touchscreen tocando nos
   4 pontos indicados. A calibracao e salva automaticamente!

2. Apos calibrar o touch, SEMPRE execute M500 para salvar todas
   as configuracoes de movimento na EEPROM

3. Se executar M502 (reset de fabrica), VOCE PRECISARA:
   a) Recalibrar o touchscreen (M995 ou via menu)
   b) Salvar as configuracoes com M500

4. A fan do hotend (HE1/PB0) liga automaticamente aos 50°C
   e desliga abaixo dessa temperatura

5. O cartao SD deve estar formatado em FAT32

6. Para recalibrar o touchscreen manualmente:
   - Via menu: Configuration > Touch Screen
   - Via gcode: M995

SOLUCAO DE PROBLEMAS:
=====================

Tela nao responde ao toque:
- Execute recalibracao: Configuration > Touch Screen
- Ou envie comando M995 via terminal
- Salve com M500 apos calibrar

Pede calibracao toda vez que liga:
- A calibracao nao foi salva na EEPROM
- Execute M500 para salvar todas as configuracoes
- Verifique se EEPROM esta funcionando (M503 deve mostrar valores)

Velocidades muito rapidas/lentas:
- Use M503 para ver configuracoes atuais
- Ajuste via LCD: Configuration > Motion
- Salve com M500

Temperatura nao estabiliza:
- Execute PID Autotune: M303 E0 S200 C8
- Salve resultados com M500

Extrusao incorreta:
- Verifique steps/mm do extrusor (deve ser 90)
- Ajuste com M92 E90 e salve com M500

Menu 'Initialize EEPROM' aparece e nao responde:
- Calibre o touchscreen primeiro
- Toque nos 4 pontos indicados
- A EEPROM sera inicializada automaticamente apos calibrar

