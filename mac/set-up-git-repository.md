---
title: Impostazione di un repository Git in Visual Studio per Mac
description: Utilizzo di Git e Subversion in Visual Studio per Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 9f25eda17648ba7eb3c264660ee0eb3b8eee166c
ms.contentlocale: it-it
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-git-repository"></a>Impostazione di un repository Git

Git è un sistema di controllo della versione della versione distribuito che consente ai team di lavorare contemporaneamente sugli stessi documenti. Ciò significa che è presente un unico server che contiene tutti i file ma ogni volta che viene estratto un repository da questa origine centrale, l'intero repository viene clonato localmente nel computer in uso.

Vi sono molti host remoti che consentono di lavorare con Git per il controllo della versione, tuttavia il più comune di questi è GitHub. Nell'esempio seguente viene usato un host GitHub, ma è possibile usare qualsiasi host Git per il controllo della versione in Visual Studio per Mac.

Se si desidera usare GitHub, assicurarsi che sia stato creato e configurato un account prima di eseguire i passaggi seguenti. 

## <a name="creating-a-remote-repo-on-github"></a>Creazione di un repository remoto su GitHub

Nell'esempio seguente viene usato un host GitHub, ma è possibile usare qualsiasi host Git per il controllo della versione in Visual Studio per Mac.

Per impostare un repository Git, seguire questa procedura:

1. Creare un nuovo repository Git in github.com:

    ![Creare nuovo repository Git](media/version-control-git1-sml.png)

2. Impostare il nome, la descrizione e la privacy del repository. **Non** inizializzare il repository. Impostare .gitignore e licenza su None (Nessuno):

    ![Impostare i dettagli del repository Git](media/version-control-git2.png)

3. La posizione successiva consentirà di visualizzare e copiare l'indirizzo HTTPS o SSH nel repository appena creato:

    ![visualizzare e copiare l'indirizzo](media/version-control-git3.png) Sarà necessario l'indirizzo HTTPS perché Visual Studio per Mac punti a questo repository.


## <a name="publishing-an-existing-project"></a>Pubblicazione di un progetto esistente

4. Tornare al proprio progetto aperto in Visual Studio per Mac. 

5. Nella barra dei menu selezionare **Version Control (Controllo della versione) > Publish in Version Control… (Pubblica in controllo della versione…)**:

    ![Avviare l'estrazione in Visual Studio per Mac](media/version-control-git4-sml.png)

6. Verrà visualizzata la finestra di dialogo **Seleziona repository**. Scegliere la scheda **Repository registrati** e premere i pulsante **Aggiungi**:

    ![](media/version-control-git5.png)

7. Inserire il nome del repository che si desidera visualizzare localmente e incollare l'URL del passaggio 3. La finestra di dialogo Configurazione repository sarà analoga alla seguente. Premere OK: 

    ![Finestra di dialogo di inserimento dettagli Git](media/version-control-git6.png)

    Notare che è anche possibile usare SSH per la connessione a Git.

8. Per tentare di pubblicare l'app in Git, selezionare il repository appena creato e assicurarsi che i campi di testo **Nome modulo** e **Messaggio** siano compilati:

    ![Tentativo di pubblicazione del progetto in Git](media/version-control-git7.png)

9. Fare clic su **OK** e quindi su **Pubblica** dalla finestra di dialogo di avviso.

10. Se non si sono ancora immesse le credenziali Git nelle preferenze di Visual Studio per Mac, immetterle ora. Per prima cosa, è necessario creare un token di accesso che viene usato al posto di una password. A tale scopo, seguire la procedura descritta nella documentazione del [token di accesso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

11. Inserire il nome utente e il token di accesso personale, quindi premere **OK**:

    ![Inserire nome utente e password per Git](media/version-control-git9-sml.png)

12. Dopo alcuni secondi, la soluzione verrà pubblicata con il suo commit iniziale. Per verificare ciò, aprire la voce del menu Controllo della versione, la quale dovrebbe ora essere popolata con molte opzioni: 

    ![Menu Controllo della versione](media/version-control-git10.png)

13. Dopo aver iniziato ad apportare modifiche aggiuntive, selezionare **...** per eseguire il push delle modifiche nel repository **remoto**. Ciò consentirà a tutti gli utenti appropriati di visualizzarlo in github.com: 

    ![Eseguire il push delle modifiche nel repository remoto](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Pubblicazione di un nuovo progetto

La finestra di dialogo del nuovo progetto può essere usata per pubblicare un nuovo progetto usando Git. Per abilitarla, selezionare la casella di controllo **Usa GIT per il controllo della versione**, come illustrato nella schermata seguente. Verrà inizializzato il repositori e verrà aggiunto un file con estensione GITIGNORE facoltativo:

![Eseguire il push delle modifiche nel repository remoto](media/version-control-git12.png)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi con l'inizializzazione del progetto con un repository remoto vuoto, provare a eseguire la procedura seguente:

- Andare alla cartella della soluzione.
- Premere `Command + Shift + . ` per mostrare i file e le cartelle nascosti.
- Se è presente una cartella `.git`, eliminarla.
- Se è presente un file `gitignore`, eliminarlo.
- Premere `Command + Shift + . ` per nascondere file e cartelle.
- Aprire la soluzione in Visual Studio per Mac.
- Nel riquadro della soluzione selezionare il nodo della soluzione.
- Andare al menu Controllo della versione e scegliere **Pubblica nel Controllo della versione**.
- Seguire la procedura dell'esercitazione precedente partendo dal passaggio 6.
