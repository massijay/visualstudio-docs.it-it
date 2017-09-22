---
title: Vai | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.contentlocale: it-it
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>Vai
Esistono molti modi per esplorare con facilità il codice all'interno dell'IDE di Visual Studio, sia usando la tastiera che il mouse.

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>Vai a tutti
Questa funzionalità esiste in Visual Studio 2017 e versioni successive.  Consente di esplorare il codice per trovare i bit specifici che si stanno cercando.  Da una semplice interfaccia unificata si possono cercare una riga, un tipo, un simbolo, un file specifico e altro ancora.

### <a name="how-to-use"></a>Uso
* **Tastiera**
  * Premere **CTRL+** o **CTRL+T**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
* **Mouse**
  * Selezionare **Modifica > Vai > Vai a tutti**.

Per impostazione predefinita sarà visualizzata una piccola finestra in alto a destra dell'IDE.

![Vai a tutti](media/gotoall.png)

Da qui è possibile procedere in vari modi:
* Immettere il testo senza un prefisso per eseguire la ricerca usando [le icone di filtro](#filtered-searches) selezionate sotto la casella di testo.
* Immettere un [prefisso](#filtered-searches) seguito dal testo da cercare.
* Immettere un punto interrogativo (?) per ottenere informazioni aggiuntive.
  ![Guida di Vai a tutti](media/gotoall_help.png)

### <a name="filtered-searches"></a>Ricerche con filtri
Per restringere la ricerca a un tipo specifico, è possibile usare un prefisso durante la digitazione o usare le icone sotto la finestra di ricerca, come illustrato di seguito.

Prefisso | Icona | Metodo rapido | Descrizione
:----: | ---- | -------- | ---
#      | ![Icona Simbolo](media/gotoall_symbolicon.png) | CTRL+1, CTRL+S | Trova i simboli corrispondenti
f      | ![Icona File](media/gotoall_fileicon.png)     | CTRL+1, CTRL+F | Trova i nomi file corrispondenti
m      | ![Icona del membro](media/gotoall_membericon.png) | CTRL+1, CTRL+M | Trova i membri corrispondenti
u      | ![Icona Tipo](media/gotoall_typeicon.png)     | CTRL+1, CTRL+T | Trova i tipi corrispondenti
:      | ![Icona Riga](media/gotoall_lineicon.png)     | CTRL+G         | Passa al numero di riga immesso

### <a name="search-locations"></a>Percorsi di ricerca
Per restringere la ricerca a percorsi specifici, usare le due icone documento.

Icona | Descrizione
---- | ---
![Documento corrente](media/gotoall_currentdocument.png) | Cerca solo il documento corrente
![Documenti esterni](media/gotoall_external.png) | Cerca i documenti esterni oltre a quelli presenti nel progetto e/o nella soluzione

### <a name="settings"></a>Impostazioni
Fare clic sull'icona a forma di ingranaggio ![Icona Ingranaggio](media/gotoall_gear.png) in basso a destra per modificare il comportamento di questa funzionalità.

Impostazione | Descrizione
------- | ---
Utilizza scheda anteprima | Visualizza immediatamente l'elemento selezionato nella scheda anteprima dell'IDE
Mostra dettagli    | Visualizza informazioni relative a progetto, file, riga e riepilogo recuperando i commenti della documentazione nella finestra
Centra la finestra   | Sposta la finestra al centro dell'IDE anziché in alto a destra
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>Vai a definizione
È possibile passare all'origine di un tipo e visualizzare il risultato in una nuova scheda:

Input        | Funzione 
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **F12**
**Mouse**    | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Vai a definizione**

## <a name="peek-definition"></a>Visualizza definizione
È possibile visualizzare l'anteprima della definizione di un tipo in una finestra popup anziché in una nuova scheda:

Input        | Funzione 
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **Alt+F12**
**Mouse**    | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Visualizza definizione**

Se viene visualizza una definizione diversa da quella della finestra popup, è possibile seguire un percorso di navigazione usando i cerchi e le frecce visualizzati sopra la finestra popup.  Per altre informazioni, vedere [How to: View and Edit Code by Using Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) (Procedura: Visualizzare e modificare il codice usando la finestra Visualizza definizione (Alt+F12)).

## <a name="go-to-implementation"></a>Vai all'implementazione
È possibile passare da una classe o un tipo base alle relative implementazioni.  Se esistono più implementazioni, vengono elencate nella finestra **Risultati ricerca simbolo**:

Input        | Funzione 
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **Ctrl+F12**
**Mouse**    | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Vai all'implementazione**

## <a name="find-all-references"></a>Trova tutti i riferimenti
È possibile trovare i punti in cui viene usato un metodo, una proprietà o una variabile.  Con questa opzione è possibile verificare il codice non utilizzato e controllare i possibili effetti collaterali di un refactoring esteso.  Premere **F8** per passare ai risultati.

Input        | Funzione 
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **CTRL+K, R**
**Mouse**    | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Trova tutti i riferimenti**

## <a name="navigating-results"></a>Esplorazione dei risultati
Quando si usano le funzionalità di navigazione di Visual Studio, è possibile passare alla posizione successiva e precedente usando la pila:

Input        | Funzione 
------------ | ---
**CTRL+-**          | Passare alla posizione precedente usando la pila
**CTRL+MAIUSC+-**    | Passare alla posizione successiva usando la pila

È anche possibile usare le voci di menu **Visualizza > Posizione precedente** e **Visualizza > Posizione successiva**.
