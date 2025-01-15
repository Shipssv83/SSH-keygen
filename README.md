# SSH-keygen
Bash скрипта для генерации SSH ключа

  ```bash
  #!/bin/bash

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
