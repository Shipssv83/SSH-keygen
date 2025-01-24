# SSH-keygen
Bash скрипта для генерации SSH ключа

  ```bash
  #!/bin/bash
echo "
 SSSSSSS  EEEEEEE  RRRRRR   HHH   HHH IIIIIIII IIIIIIII
 SSS      EEE      RRR  RR  HHH   HHH    III     III
 SSSSSS   EEEEE    RRRRRR   HHHHHHHHH    III     III
     SSS  EEE      RRR  RR  HHH   HHH    III     III
 SSSSSSS  EEEEEEE  RRR   RR HHH   HHH IIIIIIII IIIIIIII

 SSSSSSS  HHH   HHH YYY   YYY PPPPPP   YYY   YYY LLL      OOOOOOO  VVV     VVV
 SSS      HHH   HHH  YYY YYY  PPP  PP   YYY YYY  LLL      OOO OOO   VVV   VVV
 SSSSSS   HHHHHHHHH   YYYYY   PPPPPP     YYYYY   LLL      OOO OOO    VVV VVV
     SSS  HHH   HHH    YYY    PPP        YYY     LLL      OOO OOO     VVVV
 SSSSSSS  HHH   HHH    YYY    PPP        YYY     LLLLLLL  OOOOOOO      VV

      11   iii tttttttt      pppppp  rrrrrrr   ooooooo
      11         ttt         pp   pp rr   rr  oo     oo
      11   iii   ttt   ..... pppppp  rr  rrr  oo     oo
      11   iii   ttt         pp      rr   rr  oo     oo
      11   iii   ttt         pp      rr    rr  ooooooo
"
  # Запросить комментарий
  echo "Введите комментарий для ключа (по умолчанию ''):"
  read comment
  comment=${comment:-""}

  # Запросить пароль для ключа
  echo "Введите пароль для ключа (нажмите Enter для отсутствия пароля):"
  read -s password

  # Запросить имя файла для ключа
  echo "Введите имя файла для ключа (по умолчанию 'homelab'):"
  read filename
  filename=${filename:-"homelab"}

  # Генерация ключа с использованием алгоритма ed25519
  if [ -z "$password" ]; then
    ssh-keygen -t ed25519 -C "$comment" -f "$filename"
  else
    ssh-keygen -t ed25519 -C "$comment" -N "$password" -f "$filename"
  fi

  echo "Ключ сгенерирован и сохранен в $filename"
```
