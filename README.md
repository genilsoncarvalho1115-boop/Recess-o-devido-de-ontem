name: Windows Cloud RayanTech

on:
  workflow_dispatch:

jobs:
  build:
    name: Start Building...
    runs-on: windows-latest
    timeout-minutes: 90  # Máximo de 1h30m horas para evitar tempo de execução excessivo

    steps:
    - name: Downloading & Installing Essentials
      run: |
        # Baixa o arquivo .bat para instalar componentes essenciais
        Invoke-WebRequest -Uri "https://raw.githubusercontent.com/..."
          -OutFile "Downloads.bat"

        # Executa o script .bat para instalar os componentes
        cmd /c Downloads.bat

    - name: Log In To AnyDesk
      run: |
        # Verifica se o arquivo start.bat existe antes de executar
        if (Test-Path "start.bat") {
          cmd /c start.bat
        } else {
          Write-Host "Arquivo start.bat não encontrado. Verifique a configuração."
        }

    - name: Monitor and Restart AnyDesk If Needed
