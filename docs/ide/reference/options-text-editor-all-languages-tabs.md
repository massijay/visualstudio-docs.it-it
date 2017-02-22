---
title: "Opzioni, Editor di testo, Tutti i linguaggi, Schede | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs"
helpviewer_keywords: 
  - "rientri, Editor del codice"
  - "Editor del codice, comportamento predefinito"
  - "tabulazioni, impostazione nell'Editor del codice"
  - "Tutti i linguaggi (finestra di dialogo Opzioni dell'editor di testo)"
  - "editor, Editor del codice"
  - "Editor del codice, rientro"
  - "Editor del codice, tabulazioni"
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opzioni, Editor di testo, Tutti i linguaggi, Schede
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare il comportamento predefinito dell'editor di codice.  Queste impostazioni si applicano anche ad altri editor basati sull'editor di codice, ad esempio la visualizzazione Origine della finestra di progettazione HTML.  Per visualizzare tali opzioni, scegliere **Opzioni** dal menu **Strumenti**.  Nella cartella **Editor di testo** espandere la sottocartella **Tutti i linguaggi** e quindi scegliere **Tabulazioni**.  
  
> [!CAUTION]
>  In questa pagina è possibile impostare le opzioni predefinite di tutti i linguaggi di sviluppo.  La reimpostazione di un'opzione in questa finestra di dialogo determina la reimpostazione delle opzioni per le tabulazioni in tutti i linguaggi in base alle selezioni effettuate in questo contesto.  Per modificare le opzioni dell'editor di testo per un solo linguaggio, espandere la sottocartella di tale linguaggio e selezionare le relative pagine di opzioni.  
  
 Se nelle pagine di opzioni Tabulazioni sono state selezionate impostazioni diverse per determinati linguaggi di programmazione, in presenza di opzioni **Rientri** diverse viene visualizzato il messaggio "Le impostazioni dei rientri per singoli formati di testo sono in conflitto" e in presenza di opzioni **Tabulazioni** diverse viene visualizzato il messaggio "Le impostazioni delle tabulazioni per i singoli formati di testo sono in conflitto".  Questo promemoria viene ad esempio visualizzato se per Visual Basic viene selezionata l'opzione **Rientri intelligenti** e per Visual C\+\+ si seleziona invece **Blocca rientri**.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Rientri  
 Nessuno  
 Se l'opzione è selezionata, le nuove righe non sono rientrate.  Il punto di inserimento è posizionato nella prima colonna di una nuova riga.  
  
 Blocco  
 Se l'opzione è selezionata, le nuove righe vengono rientrate automaticamente.  Il punto di inserimento è posizionato nello stesso punto iniziale della riga precedente.  
  
 Intelligenti  
 Se l'opzione è selezionata, le nuove righe vengono posizionate e adattate al contesto del codice, in base ad altre impostazioni di formattazione del codice e alle convenzioni IntelliSense per il linguaggio di sviluppo.  Questa opzione non è disponibile per tutti i linguaggi di sviluppo.  
  
 Le righe racchiuse tra una parentesi graffa di apertura \( { \) e una parentesi graffa di chiusura \( } \), ad esempio, possono essere rientrate automaticamente al successivo punto di tabulazione dalla posizione delle parentesi graffe allineate.  
  
## Tabs  
 Dimensione tabulazione  
 Consente di impostare il numero di spazi tra due punti di tabulazione.  Il valore predefinito è quattro spazi.  
  
 Dimensione rientro  
 Consente di impostare il numero di spazi di un rientro automatico.  Il valore predefinito è quattro spazi.  Verranno inseriti i caratteri di tabulazione e\/o gli spazi in modo da riempire la dimensione specificata.  
  
 Inserisci spazi  
 Se l'opzione è selezionata, le operazioni di rientro consentono di inserire solo caratteri di spazio, non caratteri di tabulazione.  Se **Dimensione rientro** è impostato su 5, ad esempio, verranno inseriti cinque spazi ogni volta che verrà premuto il tasto TAB o verrà scelto il pulsante **Aumenta rientro** nella barra degli strumenti **Formattazione**.  
  
 Mantieni tabulazioni  
 Se l'opzione è selezionata, le operazioni di rientro consentono di inserire tutti i caratteri di tabulazione possibili.  Ogni carattere di tabulazione consente di riempire il numero di spazi specificato in **Dimensione tabulazione**.  Se **Dimensione rientro** non è un multiplo pari di **Dimensione tabulazione**, verranno aggiunti spazi per colmare la differenza.  
  
## Vedere anche  
 [Opzioni, Editor di testo, Tutti i linguaggi](../../ide/reference/options-text-editor-all-languages.md)   
 [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)