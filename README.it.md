<p align="center">
  <img src="icon.png" width="128" height="128" alt="Icona di Termina">
</p>

<h1 align="center">Termina</h1>

<p align="center">
  <b>Client SSH nativo per iPhone, iPad e Mac.</b><br>
  Veloce, leggero e riservato: password e chiavi non lasciano mai il tuo dispositivo.
</p>

<p align="center">
  <a href="README.md">English</a> · <b>Italiano</b>
</p>

![Termina su Mac: elenco dei server e terminale](screenshots/mac-terminal-it.jpg)

## Indice

- [Funzioni](#funzioni)
- [Requisiti di sistema](#requisiti-di-sistema)
- [Download](#download)
- [Guida all'uso](#guida-alluso)
  - [1. Aggiungere un server](#1-aggiungere-un-server)
  - [2. Connessione rapida](#2-connessione-rapida)
  - [3. Usare il terminale](#3-usare-il-terminale)
  - [4. Command Deck e tastiera](#4-command-deck-e-tastiera)
  - [5. File (SFTP)](#5-file-sftp)
  - [6. Port forwarding (tunnel)](#6-port-forwarding-tunnel)
  - [7. Sessioni che sopravvivono: tmux](#7-sessioni-che-sopravvivono-tmux)
  - [8. Impostazioni e lingua](#8-impostazioni-e-lingua)
  - [9. Sincronizzazione tra iPhone, iPad e Mac](#9-sincronizzazione-tra-iphone-ipad-e-mac)
  - [10. Handoff: continuare su un altro dispositivo](#10-handoff-continuare-su-un-altro-dispositivo)
  - [Scorciatoie da tastiera](#scorciatoie-da-tastiera)
- [Sicurezza e privacy](#sicurezza-e-privacy)
- [Risoluzione dei problemi](#risoluzione-dei-problemi)
- [Supporto](#supporto)

## Funzioni

- **Terminale vero**: xterm-256color con rendering su GPU (Metal), truecolor, vim, htop, tmux, profili colore.
- **Tab**: più server aperti insieme, si passa dall'uno all'altro con ⌘1…⌘9.
- **Connessione rapida**: scrivi `utente@host` e sei dentro, come `ssh` nel Terminale.
- **Command Deck**: Esc, Tab, Ctrl, Alt, frecce, simboli e le tue macro a un tocco.
- **File (SFTP)** accanto al terminale: carica, scarica, anteprima, modifica dei file di testo, permessi.
- **Port forwarding**: tunnel locali (-L) e remoti (-R) con stato e traffico in tempo reale.
- **Credenziali sicure**: password e chiavi nel Portachiavi, sbloccate con Face ID o Touch ID; chiavi hardware
  generate nel **Secure Enclave**, che non possono mai essere copiate.
- **Handoff**: inizi sul Mac, continui sull'iPad con un tocco, sullo stesso server.
- **Sincronizzazione iCloud**: server, macro, tunnel, password e chiavi su tutti i tuoi iPhone, iPad e Mac,
  cifrati end-to-end, senza creare account.
- **Tailscale** riconosciuto da solo; **tmux** tiene viva la shell quando la connessione cade.
- 5 lingue: italiano, English, Français, Deutsch, Español.

| | |
|---|---|
| ![Schermata iniziale con la connessione rapida](screenshots/mac-welcome-it.jpg) | ![Terminale con il pannello File](screenshots/mac-files-it.jpg) |
| Schermata iniziale, server recenti e connessione rapida | Terminale con il pannello File |
| ![Port forwarding](screenshots/mac-tunnels-it.jpg) | ![Modifica di un server](screenshots/mac-editor-it.jpg) |
| Port forwarding con stato in tempo reale | Modifica di un server: icona, colore, gruppo, autenticazione |
| ![Terminale su iPad](screenshots/ipad-terminal-it.jpg) | ![Impostazioni](screenshots/mac-settings-it.jpg) |
| iPad con la Command Deck | Impostazioni |

<p align="center">
  <img src="screenshots/iphone-welcome-it.jpg" width="240" alt="iPhone: schermata iniziale">
  &nbsp;
  <img src="screenshots/iphone-terminal-it.jpg" width="240" alt="iPhone: terminale">
  &nbsp;
  <img src="screenshots/ipad-portrait-terminal-it.jpg" width="360" alt="iPad in verticale">
</p>

## Requisiti di sistema

| | iPhone | iPad | Mac |
|---|---|---|---|
| **Sistema operativo** | iOS 17 o successivo | iPadOS 17 o successivo | macOS 15 Sequoia o successivo |
| **Dispositivi** | iPhone XS, XR o successivi | iPad (6ª gen.), iPad mini (5ª gen.), iPad Air (3ª gen.), iPad Pro (2ª gen.) o successivi | Apple silicon (M1 o successivi) o Mac Intel che eseguono macOS 15 |
| **Aspetto Liquid Glass** | iOS 26 | iPadOS 26 | macOS 26 Tahoe |
| **Sblocco delle credenziali** | Face ID, Touch ID o codice (il codice deve essere impostato) | Face ID, Touch ID o codice (il codice deve essere impostato) | Touch ID o password del Mac |
| **Chiavi Secure Enclave** | Tutti gli iPhone supportati | Tutti gli iPad supportati | Apple silicon, o Mac Intel con chip T2 |
| **Tastiera fisica** | Facoltativa | Facoltativa (Magic Keyboard, Smart Keyboard, Bluetooth) | Integrata |

Sui sistemi precedenti l'app funziona allo stesso modo, con l'aspetto classico (senza vetro). Serve poi un server
SSH a cui collegarsi (Linux, macOS, BSD, Raspberry Pi, NAS, router…) raggiungibile dal dispositivo: in rete
locale, via Internet o tramite una VPN come Tailscale.

## Download

Termina arriverà sull'App Store per iPhone, iPad e Mac. Le nuove versioni e le note di rilascio sono pubblicate
nella pagina [Releases](https://github.com/kikoz85/Termina/releases) di questo repository.

## Guida all'uso

### 1. Aggiungere un server

1. Premi **+** in cima all'elenco dei server (oppure ⌘N).
2. Compila **Indirizzo** (IP o hostname), **Porta** (di solito 22) e **Utente**. L'**Etichetta** è il nome che vedrai nell'elenco.
3. Facoltativo: scegli un **gruppo** (Locale, Mac Mini, Produzione), un **colore** e un'**icona**, per riconoscerlo a colpo d'occhio.
4. Scegli come accedere:
   - **Password**: la scrivi una volta e resta nel Portachiavi.
   - **Chiave**: importa una chiave privata OpenSSH (Ed25519 o RSA) da File, con la passphrase se ce l'ha.
   - **Secure Enclave**: Termina crea una chiave dentro il chip del dispositivo. Copia la chiave pubblica mostrata
     e aggiungila a `~/.ssh/authorized_keys` sul server. La chiave privata non si può mai esportare né copiare.
5. Premi **Salva**, poi tocca il server per collegarti.

Alla prima connessione Termina mostra il **fingerprint** del server: confrontalo con quello del server
(`ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub`) e scegli **Considera attendibile**. Se un giorno cambia,
Termina rifiuta la connessione e ti avvisa: può essere un attacco, oppure il server è stato reinstallato.

### 2. Connessione rapida

Nella schermata iniziale scrivi `utente@host` (o `utente@host:porta`) accanto a `ssh` e premi Invio.
Termina si collega subito e chiede la password, come fa `ssh`. La password resta in memoria solo per quella
sessione. Per tenere il server apri il menu della sessione (**⋯**) e scegli **Salva server**: la password che
hai scritto è già compilata.

Se l'indirizzo corrisponde a un server già salvato, si apre direttamente la sua sessione.

### 3. Usare il terminale

- Ogni server si apre in una **tab**. Il **+** accanto alle tab apre un altro server; **×** chiude la tab.
- Il titolo mostra `utente@host — processo — colonne×righe`.
- **Pizzica** lo schermo (o ⌘+ / ⌘-) per cambiare la dimensione del testo.
- **⌘F** cerca nell'output; **⌘K** pulisce lo schermo e lo scrollback.
- Seleziona il testo per copiarlo; i link nell'output si aprono direttamente.
- Se la connessione cade, una scheda mostra il motivo con **Riconnetti** e **Modifica server** (per correggere
  indirizzo, utente o password senza uscire dalla sessione).

### 4. Command Deck e tastiera

La barra sotto il terminale (la **Command Deck**) ti dà i tasti che la tastiera touch non ha:

- **ctrl** e **alt** restano bloccati per il tasto successivo: tocca **ctrl**, poi **c** per inviare Control-C.
- **esc**, **tab**, frecce, `|` `~` `/` `-` e scorciatoie come **^C ^D ^Z ^R**.
- **Macro**: pulsanti che scrivono un intero comando (`ls -la`, `htop`, `docker ps`…). Premi **+** per aggiungerne
  di tue, con nome, icona e la scelta se eseguirle subito. Le macro sono di ciascun server.

Con una **tastiera fisica** (Magic Keyboard su iPad, o quella del Mac) la Deck può mostrare solo le macro o
sparire del tutto: vedi *Impostazioni → Tastiera → Command Deck*. **⌘.** invia sempre Esc, anche dalle tastiere senza
il tasto Esc. **Option come Meta** fa inviare a Option la sequenza Esc+tasto (utile in Emacs, bash e tmux); disattivalo per scrivere lettere accentate con Option.

### 5. File (SFTP)

Premi il pulsante **cartella** nella barra (⇧⌘F) per aprire i file del server accanto al terminale.

- Tocca una cartella per aprirla; tocca il percorso in alto per tornare indietro; **↑** va alla cartella superiore.
- Tocca un file di testo per **modificarlo**; gli altri file si aprono in **Quick Look**.
- **Carica** con il pulsante di condivisione o **trascinando** i file; tieni premuto (o clic destro) su un file per
  **salvarlo**, **rinominarlo**, cambiare i **permessi**, copiarne il percorso o eliminarlo.
- **Apri nel terminale** esegue `cd` in quella cartella nella shell.

### 6. Port forwarding (tunnel)

I tunnel servono a raggiungere servizi che vede solo il server, per esempio un database o un pannello di amministrazione.
Premi il pulsante **tunnel** nella barra (⇧⌘T), poi **+**:

- **Locale (-L)**: ascolta sul tuo dispositivo e inoltra al server. Esempio: dispositivo `127.0.0.1:5432` → server
  `127.0.0.1:5432` ti permette di aprire il PostgreSQL del server dalle app del tuo iPad o Mac.
- **Remoto (-R)**: ascolta sul server e inoltra al tuo dispositivo o alla tua rete.

Ogni tunnel mostra lo stato e il traffico in tempo reale; i tunnel web si aprono nel browser con un tocco. Su iPhone
e iPad i tunnel locali funzionano finché Termina è in primo piano (anche in Split View e Slide Over).

### 7. Sessioni che sopravvivono: tmux

iOS chiude le connessioni di rete circa 30 secondi dopo che un'app passa in background. Per non interrompere i
lavori lunghi, scrivi un nome in **Sessione tmux** quando modifichi un server: Termina avvia
`tmux new-session -A -s <nome>` dopo l'accesso e si riaggancia alla stessa shell quando si riconnette. Sul server
deve essere installato `tmux`.

### 8. Impostazioni e lingua

Apri le **Impostazioni** con l'ingranaggio (o ⌘,):

- **Profilo**: sei temi colore con anteprima dal vivo, e l'opacità.
- **Testo**: carattere e dimensione. **Cursore**: forma e lampeggio.
- **Tastiera**: Option come Meta e comportamento della Command Deck.
- **Lingua**: *Automatica* segue la lingua del sistema (inglese se la tua lingua non è disponibile), oppure
  scegli English, Italiano, Français, Deutsch o Español. La nuova lingua vale dalla prossima apertura dell'app;
  sul Mac puoi riavviarla subito.

### 9. Sincronizzazione tra iPhone, iPad e Mac

Termina tiene allineati i tuoi dispositivi attraverso **il tuo iCloud**: non c'è un account Termina da creare.
È attiva di default (*Impostazioni → Sincronizzazione → iCloud*); basta aver fatto l'accesso con lo stesso
Apple Account su ogni dispositivo.

- **Cosa si sincronizza**: server (con gruppi, colori, icone), macro, tunnel, host key fidate, password e chiavi
  private. Aggiungi un server sul Mac e ti colleghi dall'iPad senza riscrivere la password.
- **Privacy**: tutto è cifrato end-to-end con chiavi del tuo Portachiavi iCloud; Apple non può leggerlo.
- **Cosa resta su ogni dispositivo**: le chiavi Secure Enclave (non escono mai dal chip: creane una per
  dispositivo e aggiungi ogni chiave pubblica ad `authorized_keys`) e l'elenco dei server recenti.
- Le modifiche arrivano in pochi secondi; **Sincronizza ora** nelle Impostazioni forza un controllo. Se due
  dispositivi modificano lo stesso server, vince la modifica più recente.
- Le password salvate prima di attivare la sincronizzazione partono la prima volta che le usi per collegarti.

### 10. Handoff: continuare su un altro dispositivo

Mentre una sessione è aperta su un dispositivo, Termina la offre agli altri: l'icona di Termina compare in fondo
al **Dock** su Mac e iPad e nel **selettore app** su iPhone. Toccala e lì si apre lo stesso server.

- Con una **sessione tmux** impostata per il server ritrovi la stessa identica shell, con tutto ancora in corso.
- Senza tmux ottieni una shell nuova nella **stessa cartella**, se la shell la comunica (sequenza OSC 7; in bash
  aggiungi a `~/.bashrc` `PROMPT_COMMAND='printf "\e]7;file://%s%s\e\\" "$HOSTNAME" "$PWD"'`).
- Serve lo stesso Apple Account, Bluetooth e Wi‑Fi attivi e **Handoff** abilitato (Impostazioni → Generali →
  AirPlay e Continuity su iPhone/iPad, Impostazioni di Sistema → Generali → AirDrop e Handoff sul Mac).

### Scorciatoie da tastiera

| Tasti | Azione |
|---|---|
| ⌘T / ⌘W | Nuova tab / chiudi tab |
| ⌘1…⌘9, ⇧⌘[ ⇧⌘] | Vai alla tab / precedente / successiva |
| ⌘K | Pulisci schermo e scrollback |
| ⌘F, ⌘G, ⇧⌘G | Trova, successivo, precedente |
| ⌘+ ⌘- ⌘0 | Dimensione del testo |
| ⌘. | Esc |
| ⇧⌘T | Tunnel |
| ⇧⌘F, ⌘↑ | File, cartella superiore |
| ⌘N / ⌘, | Nuovo server / Impostazioni |
| ⌘R | Riconnetti |

Su iPad tieni premuto **⌘** per vedere tutte le scorciatoie.

## Sicurezza e privacy

- Password e chiavi private sono salvate solo nel **Portachiavi** del dispositivo, protette da Face ID, Touch ID o
  dal codice. Con la sincronizzazione iCloud attiva viaggiano anche nel tuo iCloud, cifrate end-to-end: né
  Apple né lo sviluppatore possono leggerle.
- Le chiavi Secure Enclave nascono dentro il chip e **non si possono estrarre**, nemmeno da Termina.
- L'identità di ogni server viene verificata (fingerprint della host key) per proteggerti dagli attacchi man-in-the-middle.
- Niente account, niente statistiche, nessun tracciamento: Termina si collega solo ai server che aggiungi tu (e, con la sincronizzazione attiva, al tuo iCloud).

Informativa completa: [Privacy](https://kikoz85.github.io/Termina/privacy.html).

## Risoluzione dei problemi

| Problema | Cosa fare |
|---|---|
| "Credenziale non trovata nel Portachiavi" | Apri **Modifica server** dalla scheda della sessione e scrivi di nuovo la password o reimporta la chiave. |
| "Autenticazione non riuscita" | Controlla utente e password. Per le chiavi, verifica che la chiave pubblica sia in `~/.ssh/authorized_keys` sul server. |
| "La host key è cambiata" | Se hai reinstallato il server, eliminalo da Termina e aggiungilo di nuovo. Altrimenti **non** collegarti. |
| `100.x.x.x` o `*.ts.net` non raggiungibili | Attiva la VPN Tailscale sul dispositivo. |
| La connessione cade in background | Usa una **sessione tmux** (vedi la guida, punto 7). |
| Le lettere accentate con Option non funzionano | Disattiva **Option come Meta** nelle Impostazioni. |
| Un server non compare su un altro dispositivo | Verifica di aver fatto l'accesso a iCloud con lo stesso Apple Account, poi **Impostazioni → Sincronizza ora**. |

## Supporto

- Aiuto e contatti: [pagina di Supporto](https://kikoz85.github.io/Termina/support.html)
- Bug e suggerimenti: apri una [issue](https://github.com/kikoz85/Termina/issues) o scrivi a enricofanucchi@gmail.com

© 2026 Enrico Fanucchi
