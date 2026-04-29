# dotfiles

> Personal dotfiles, configs & dev notes — Ivan Neto

---

## Structure

```
dotfiles/
├── fixes/
│   └── fix-xdg-desktop-loop.md       # Fix: Área de trabalho em loop simbólico (Ubuntu)
├── sysctl/
│   └── 99-custom-performance.conf    # Otimizações de kernel (memória, swap, rede)
└── README.md
```

---

## Fixes

Documentação de bugs encontrados e suas soluções, testados em Ubuntu 26.04 LTS.

## Sysctl

Configurações de kernel aplicadas em `/etc/sysctl.d/`. Para aplicar:

```bash
sudo cp sysctl/99-custom-performance.conf /etc/sysctl.d/
sudo sysctl --system
```
