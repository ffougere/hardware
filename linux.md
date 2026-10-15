# 🐧 Sur Linux
# 1. Mémoire (RAM)
free -h
Regardez la ligne Mem: et la colonne total.

# 2. Carte Graphique (GPU) & VRAM
Nvidia :
nvidia-smi
Affiche le modèle de carte ainsi que la VRAM totale et utilisée.
AMD :   rocm-smi --showproductname --showmeminfo vram

Commande universelle (détection hardware) :Bash
lspci | grep -i vga

3. Processeur (CPU)Bashlscpu | grep -E "Model name|CPU\(s\):"

# 🪟 Sur Windows (PowerShell)
1. Mémoire (RAM)   PowerShell
2. Get-CimInstance Win32_PhysicalMemory | Measure-Object -Property Capacity -Sum | Select-Object @{N="TotalRAM_GB"; E={[math]::round($_.Sum / 1GB, 2)}}
3. Carte Graphique (GPU) & VRAMCommandes PowerShell :

5. Get-CimInstance Win32_VideoController | Select-Object Name, @{N="VRAM_GB"; E={[math]::round($_.AdapterRAM / 1GB, 2)}}
Si vous avez une carte Nvidia :PowerShell
nvidia-smi
7. Processeur (CPU)PowerShellGet-CimInstance Win32_Processor | Select-Object Name, NumberOfCores, NumberOfLogicalProcessors
