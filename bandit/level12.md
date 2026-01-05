# Bandit Level 12 → Level 13

## Obiettivo
Ripristinare un file che è stato convertito in hexdump e poi compresso multiplice volte.

## Processo manuale utilizzato

### 1. Preparazione ambiente
```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
mktemp -d
cd /tmp/tmp.XXXXXX
cp ~/data.txt .
```

### 2. Convertire hexdump in binario
```bash
xxd -r data.txt > data.bin
```

### 3. Ciclo di decompressione manuale

Ogni passo:

```bash
# Identificare tipo di file
file data.bin

# Decomprimere in base al tipo
```

**Esempi di comandi usati**

**Per gzip:**

```bash
mv data.bin data.gz
gzip -d data.gz
# risultato: file 'data'
mv data data.bin
```

**Per bzip2:**

```bash
bzip2 -d data.bin
# risultato: data.bin.out
mv data.bin.out data.bin
```

**Per tar:**
```bash
tar -xf data.bin
# estrae uno o più file
ls
# seleziona il file estratto e rinominalo come data.bin
mv nome_file_estratto data.bin
```

**Per XZ:**
```bash
mv data.bin data.xz
unxz data.xz
mv data data.bin
```

### 4. Ripetere fino a testo ASCII
Continuare con `file data.bin` e decompressione appropriata finchè:

```bash
file data.bin
# Output: ASCII text
cat data.bin
```

## Analisi tecnica

### Cosa ho imparato
- `xxd -r`: converte hexdump ASCII in binario
- `file`: identifica tipo file usando magic bytes
- Comandi decompressione specifici per formato
- L'importanza di lavorare in `/tmp/` per non lasciare tracce

### Formati di compressione incontrati
1. gzip (`*.gz`) → `gzip -d` o `gunzip`

2. bzip2 (`*.bz2`) → `bzip2 -d`

3. tar archive → `tar xf`

4. XZ (`*.xz`) → `unxz`

5. Hexdump → `xxd -r`


### Come automatizzare il processo

```bash
#!/bin/bash
cp ~/data.txt /tmp/work/
cd /tmp/work/
xxd -r data.txt > data

while true; do
    file_type=$(file -b data | awk '{print $1}')
    case $file_type in
        gzip)    mv data data.gz; gzip -d data.gz ;;
        bzip2)   bzip2 -d data ;;
        POSIX)   tar xf data; rm data; mv $(ls | head -1) data ;;
        XZ)      mv data data.xz; unxz data.xz ;;
        ASCII)   cat data; break ;;
        *)       echo "Tipo sconosciuto"; break ;;
    esac
done
```

### Domande aperte
- Come funzionano i "magic bytes" usati da `file`?
- Quali altri formati di compressione potrebbero apparire in scenari reali?
- Come gestire file corrotti o parziali in forensics?
- Quali tool automatizzano l'estrazione di file nidificati ?


### Note
Il livello simula un scenario di forensics: dati offuscati molteplici volte.
La persistenza e il metodo sistematico sono più importanti della velocità.