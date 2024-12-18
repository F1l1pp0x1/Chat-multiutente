# **Chat Multi-Utente**

**Autori:**  
- **Bassoni Tommaso**  
- **Mosti Filippo**  

---

## 📋 **Obiettivo dell’Applicazione**

L'obiettivo del progetto è lo sviluppo di una chat multi-utente con funzionalità di comunicazione **uno-a-uno**. Gli utenti possono selezionare un destinatario specifico per scambiarsi messaggi privati.

---

## ⚙️ **Funzionamento dell’Applicazione**

### 🔐 **Accesso e Creazione Account**

All'avvio dell'applicazione, l'utente potrà scegliere tra:

1. **Creare un nuovo account**  
2. **Accedere a un account esistente**

### 💬 **Gestione delle Chat**

Dopo l'accesso, l'utente ha le seguenti opzioni:

- **Creare una nuova chat** con un destinatario non presente nei contatti esistenti.  
  - È necessaria una verifica preliminare dell’esistenza del destinatario.  

- **Cercare un destinatario nei contatti esistenti** tramite:  
  - **Nome del destinatario**  
  - **Indice nell’elenco dei contatti**

### ✉️ **Interazione nella Chat**

Nella chat con un destinatario, l'utente può:

- **Visualizzare la cronologia** dei messaggi scambiati.  
- **Inviare nuovi messaggi** al destinatario.

---

## 📡 **Protocollo di Comunicazione**

L'applicazione utilizza un protocollo di comunicazione personalizzato chiamato **"Packet"**. Questo protocollo è implementato tramite una classe Java dedicata e facilita la comunicazione tra **client** e **server**.

### 🛠️ **Struttura del Packet**

Il `Packet` include i seguenti campi:

| **Campo**              | **Tipo**           | **Descrizione**                                                          |
|-------------------------|--------------------|--------------------------------------------------------------------------|
| **Source username**     | `String`           | Mittente della comunicazione.                                            |
| **ACK**                 | `boolean`          | Conferma di operazioni (es. validazione credenziali).                    |
| **LOG**                 | `boolean`          | Richiesta di accesso (login).                                            |
| **CRT**                 | `boolean`          | Richiesta di creazione di un account.                                    |
| **MSG**                 | `boolean`          | Invio di un messaggio al destinatario.                                   |
| **Destination username**| `String`           | Destinatario della comunicazione.                                        |
| **Time**                | `LocalDateTime`    | Data e ora di invio del pacchetto.                                       |
| **Message**             | `String`           | Contenuto del messaggio (payload).                                       |

---

## 🔎 **Scenari di Applicazione del Protocollo**

### 📌 **Creazione dell’Account**

1. **Richiesta di validazione dello username**:  
    ```plaintext
    Username_scelto
    0 0 1 0
    null
    LocalDateTime.now()
    null
    ```

2. **Richiesta di validazione della password**:  
    ```plaintext
    Username_scelto
    0 0 1 0
    null
    LocalDateTime.now()
    password_scelta
    ```

### 🔐 **Accesso all’Account**

**Richiesta di validazione delle credenziali** (username e password):  
```plaintext
Username_scelto
0 1 0 0
null
LocalDateTime.now()
password_scelta
