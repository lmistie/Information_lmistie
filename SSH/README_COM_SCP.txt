НАЗВАНИЕ
     scp — безопасная копия файла OpenSSH

СИНТАКСИС
     scp [-346ABCpqrTv] [-c шифр] [-F ssh_config] [-i идентификационный_файл]
         [-J пункт назначения] [-l лимит] [-o ssh_option] [-P порт]
         [-S программа] источник ... цель

ПРИМЕРЫ
     Как перекидывать файлы из одной локальной машины в другую
     Находясь в одной сети. 

     Пример №1:
     Копируем из Персонального Компьютера 2 (ПК - 2) к которому подключились по ssh.

     ➜ scp namefile yourusername1@ipaddress1:/Users...home/yourusername/.../

     Где namefile - файл который вы собираетесь перекидывать из директории в которой вы находитесь.
     ipaddress1 - IP адрес ПК с которого мы подключились по SSH.
     Users или home у кого какая Операционная Система (ОС)

     
     Password:
     namefile                             100%   ***    ***.*KB/s   00:00

     Пример №2:
     Копируем из Персонального Компьютера 1 (ПК -1) для передачи файлов для ПК - 2.

     ➜ scp yourusername1@ipaddress1:/Users...home/yourusername/.../namefile .

     Где namefile - файл который вы собираетесь перекидывать.
     ipaddress1 - IP адрес ПК с которого мы подключились по SSH.
     Users или home у кого какая Операционная Система (ОС)
     Точка на конце означает текущий локальный каталог. ( . )
     Две точке является родительсским каталогом текущего каталога. ( .. |  Пример cd ..)

     
     Password:
     namefile                             100%   ***    ***.*KB/s   00:00

ОПИСАНИЕ
     scp копирует файлы между хостами в сети.

     Он использует ssh(1) для передачи данных и использует ту же аутентификацию
     и обеспечивает ту же безопасность, что и сеанс входа в систему. Протокол SCP
     требует запуска оболочки удаленного пользователя для выполнения glob(3)
     сопоставление с образцом.

     scp запросит пароли или парольные фразы, если они необходимы для
     аутентификация.

     Источник и цель могут быть указаны как локальный путь, удаленный
     host с необязательным путем в форме [user@]host:[path] или URI в
     форма scp://[пользователь@]хост[:порт][/путь]. Имена локальных файлов могут быть
     сделано явным с использованием абсолютных или относительных путей, чтобы избежать scp
     обработка имен файлов, содержащих ‘:’, как спецификаторов хоста.

     При копировании между двумя удаленными хостами, если используется формат URI,
     порт может быть указан на цели, только если используется опция -3.

   Варианты следующие:

     -3     Копии между двумя удаленными хостами передаются через
            местный хост. Без этой опции данные копируются напрямую
            между двумя удаленными хостами. Обратите внимание, что этот вариант
            отключает индикатор выполнения и выбирает пакетный режим для
            второй хост, так как scp не может запрашивать пароли или
            пароли для обоих хостов.

     -4     Заставляет scp использовать только адреса IPv4.

     -6     Заставляет scp использовать только адреса IPv6.

     -A     Разрешает переадресацию ssh-agent(1) на удаленную систему.
            По умолчанию не пересылать агент аутентификации.

     -B     Выбирает пакетный режим (предотвращает запрос паролей или парольные фразы).

     -C     Включить сжатие. Передает флаг -C в ssh(1) для включения сжатие.

     -c     шифр
            Выбирает шифр, используемый для шифрования передачи данных.
            Эта опция напрямую передается в ssh(1).

     -F     ssh_config
            Указывает альтернативный файл конфигурации для каждого пользователя для ssh.
            Эта опция напрямую передается в ssh(1).

     -i     идентификационный_файл
            Выбирает файл, из которого удостоверение (закрытый ключ) для
            аутентификация с открытым ключом читается. Этот вариант напрямую
            передан ssh(1).

     -J     пункт назначения
            Подключитесь к целевому хосту, сначала установив соединение scp
            к хосту перехода, описанному пунктом назначения, а затем
            установление TCP-переадресации до конечного пункта назначения
            оттуда. Несколько прыжков могут быть указаны отдельно
            по символам запятой. Это ярлык для указания
            Директива конфигурации ProxyJump. Этот вариант напрямую
            передан ssh(1).

      -l    предел
            Ограничивает используемую полосу пропускания, указанную в кбит/с.

      -o    ssh_option
            Может использоваться для передачи параметров в ssh в формате, используемом в ssh_config(5). 
            Это полезно для указания параметров для которого нет отдельного флага командной строки scp.
            Для полного подробности о вариантах, перечисленных ниже, и их возможных значения, см. ssh_config(5).
                  
                   АдресСемья
                   Пакетный режим
                   BindAddress
                   BindInterface
                   CanonicalDomains
                   CanonicalizeFallbackLocal
                   CanonicalizeHostname
                   CanonicalizeMaxDots
                   CanonicalizePermittedCNAMEs
                   CASignatureАлгоритмы
                   СертификатФайл
                   ВызовОтветАутентификация
                   ПроверитьHostIP
                   Шифры
                   Сжатие
                   Попытки подключения
                   ConnectTimeout
                   Мастер управления
                   путь управления
                   ControlPersist
                   глобалкноунхостсфиле
                   GSSAPIAАутентификация
                   GSSAPIDelegateCredentials
                   HashKnownHosts
                   Хозяин
                   HostbasedAcceptedAlgorithms
                   Аутентификация на основе хоста
                   HostKeyАлгоритмы
                   HostKeyAlias
                   Имя хоста
                   только удостоверения
                   ИдентитиАгент
                   IdentityFile
                   IPQoS
                   KbdInteractiveAuthentication
                   KbdInteractiveDevices
                   KexАлгоритмы
                   Команда KnownHosts
                   Логуровень
                   MAC
                   NoHostAuthenticationForLocalhost
                   КоличествоПодсказокПароля
                   ПарольАутентификация
                   PKCS11Provider
                   Порт
                   PreferredAuthentications
                   Проксикоманда
                   ПроксиДжамп
                   PubkeyAcceptedАлгоритмы
                   PubkeyАутентификация
                   RekeyLimit
                   SendEnv
                   СерверАливеИнтервал
                   СерверАливеКаунтМакс
                   SetEnv
                   Строгий ХостКейПроверка
                   TCPKeepAlive
                   ОбновлениеHostKeys
                   Пользователь
                   UserKnownHostsFile
                   VerifyHostKeyDNS
         -p порт
            Указывает порт для подключения на удаленном узле. Примечание
            что эта опция пишется с большой буквы «P», потому что -p
            уже зарезервировано для сохранения времени и способов
            файл.

         -p Сохраняет время модификации, время доступа и режимы изисходный файл.

         -q Тихий режим: отключает индикатор выполнения, а также предупреждение и диагностические сообщения от ssh(1).

         -r Рекурсивно копировать целые каталоги. Обратите внимание, что scp следует
            символические ссылки, встречающиеся при обходе дерева.

         -S программа
            Имя программы, используемой для зашифрованного соединения.
            программа должна понимать параметры ssh(1).

         -T Отключить строгую проверку имен файлов. По умолчанию при копировании
            файлы с удаленного хоста в локальный каталог scp проверяет
            что полученные имена файлов совпадают с запрошенными на
            командной строки, чтобы предотвратить отправку удаленным концом
            неожиданные или нежелательные файлы. Из-за различий в том, как
            различные операционные системы и оболочки интерпретируют имя файла
            подстановочные знаки, эти проверки могут привести к тому, что нужные файлы будут
            отклоненный. Эта опция отключает эти проверки за счет
            полностью доверять тому, что сервер не будет отправлять неожиданные
            имена файлов.

         -v Подробный режим. Заставляет scp и ssh(1) печатать отладкусообщения об их продвижении. 
         Это полезно при отладке проблемы с подключением, аутентификацией и конфигурацией.

ВЫХОД СТАТУС
     Утилита scp возвращает 0 в случае успеха и >0 в случае ошибки.

СМОТРИТЕ ТАКЖЕ
     sftp(1), ssh(1), ssh-add(1), ssh-agent(1), ssh-keygen(1), ssh_config(5), sshd(8)

ИСТОРИЯ
     scp основан на программе rcp в исходном коде BSD от Regents.
     Калифорнийского университета.