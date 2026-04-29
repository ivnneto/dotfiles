# Fix: Área de trabalho em loop simbólico (Ubuntu)

## Sintoma

- Pastas do sistema (`Documentos`, `Músicas`, `Imagens`, etc.) aparecem na Área de Trabalho
- Erro ao abrir pastas no Nautilus: `Muitos níveis de links simbólicos`
- `~/Área de trabalho` aponta pra si mesmo

## Diagnóstico

```bash
ls -la ~/Área\ de\ trabalho
# Output esperado do bug:
# lrwxrwxrwx ... '/home/user/Área de trabalho' -> '/home/user/Área de trabalho'
```

## Causa

O `xdg-user-dirs` cria um link simbólico circular — `~/Área de trabalho` aponta para ele mesmo.
Pode acontecer após atualizações do sistema ou instalações que mexem no `xdg-user-dirs`.

## Solução

```bash
rm ~/Área\ de\ trabalho
mkdir ~/Área\ de\ trabalho
xdg-user-dirs-update --force
```

Reiniciar a sessão ou o sistema após aplicar o fix.

## Verificação

```bash
ls -la ~/Área\ de\ trabalho
# Deve mostrar uma pasta normal, não um symlink
```

## Ambiente

- Testado no Ubuntu 24.04 LTS
- Reproduzido também no Ubuntu 26.04 Beta
