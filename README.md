# LVM - Logical Volume Manager

## Comandi di Test per LVM

### Creazione dei Physical Volume

#### Comando: `pvs`
- **Esempio**: `pvs`
- **Descrizione**: Verifica se esistono altri Physical Volumes.

#### Comando: `pvcreate`
- **Esempio**: `pvcreate /dev/sdX`
- **Descrizione**: Crea un nuovo Physical Volume sul dispositivo specificato.

### Creazione dei Volume Groups

#### Comando: `vgs`
- **Esempio**: `vgs`
- **Descrizione**: Verifica se esistono altri Volume Groups.

#### Comando: `vgcreate`
- **Esempio**: `vgcreate TestLvm /dev/sdX`
- **Descrizione**: Crea un Volume Group chiamato "TestLvm" utilizzando il Physical Volume specificato.

### Creazione dei Logical Volume

#### Comando: `lvs`
- **Esempio**: `lvs`
- **Descrizione**: Verifica se esistono altri Logical Volumes.

#### Comando: `lvcreate`
- **Esempio**: `lvcreate -L 10G -n Logical_LVM TestLvm`
- **Descrizione**: Crea un Logical Volume di 10GB chiamato "Logical_LVM" nel Volume Group "TestLvm".

### Creazione di una copia del Logical Volume

#### Comando: `lvcreate -m`
- **Esempio**: `lvcreate -L 10G -m 1 -n Logical_LVM TestLvm`
- **Descrizione**: Crea un Logical Volume di 10GB con una copia (mirroring) nel Volume Group "TestLvm".

### Riduzione spazio ad un Logical Volume

#### Comando: `efsck`
- **Esempio**: `efsck /dev/TestLvm/Logical_LVM`
- **Descrizione**: Controlla il filesystem del Logical Volume prima di ridurlo.

#### Comando: `resize2fs`
- **Esempio**: `resize2fs /dev/TestLvm/Logical_LVM 8G`
- **Descrizione**: Ridimensiona il filesystem del Logical Volume a 8GB.

#### Comando: `lvreduce`
- **Esempio**: `lvreduce -L 8G /dev/TestLvm/Logical_LVM`
- **Descrizione**: Riduce la dimensione di un Logical Volume a 8GB.

### Estensione spazio ad un Logical Volume

#### Comando: `lvextend`
- **Esempio**: `lvextend -L 10G /dev/TestLvm/Logical_LVM`
- **Descrizione**: Estende la dimensione di un Logical Volume a 10GB.

### Snapshot con LVM

#### Comando: `lvcreate -s`
- **Esempio**: `lvcreate -L 1G -s -n Logical_LVM_snapshot /dev/TestLvm/Logical_LVM`
- **Descrizione**: Crea uno snapshot di 1GB del Logical Volume specificato.

#### Comando: `lvconvert --merge`
- **Esempio**: `lvconvert --merge /dev/TestLvm/Logical_LVM_snapshot`
- **Descrizione**: Ripristina il Logical Volume dallo snapshot specificato.

### Rimozione di Logical Volume, Volume Group e Physical Volume

#### Comando: `lvremove`
- **Esempio**: `lvremove /dev/TestLvm/Logical_LVM`
- **Descrizione**: Rimuove un Logical Volume specificato.

#### Comando: `vgreduce`
- **Esempio**: `vgreduce TestLvm /dev/sdX`
- **Descrizione**: Rimuove un Physical Volume specificato dal Volume Group.
