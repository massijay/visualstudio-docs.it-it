---
title: "Procedura: aggiornare un&#39;estensione di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetto di aggiornamento"
  - "aggiornare l'estensione"
  - "nuova versione del pacchetto"
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: aggiornare un&#39;estensione di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile aggiornare un'estensione di Visual Studio nel sistema utilizzando **estensioni e aggiornamenti** per installare la versione aggiornata. Se si crea una versione aggiornata di un'estensione, è possibile segnalare l'aggiornamento incrementando il numero di versione nel manifesto VSIX.  
  
 Gli aggiornamenti vengono installati quando il manifesto VSIX dell'estensione ha lo stesso `ID` come quello installato e un livello più elevato `Version` numero. Se il `Version` numero è uguale o inferiore, il pacchetto non può essere installato. Se il `ID` valori non corrispondono, il pacchetto che non è ancora installato viene riconosciuto come un'estensione diversa.  
  
 Per evitare conflitti durante lo sviluppo, è consigliabile disinstallare le versioni precedenti delle estensioni in corso, anche disinstallare o disabilitare eventuali altre estensioni potenzialmente in conflitto.  
  
### Per aggiornare un'estensione del sistema  
  
1.  Nel menu **Strumenti** fare clic su **Estensioni e aggiornamenti**.  
  
2.  Nel riquadro a sinistra, fare clic su **aggiornamenti**.  
  
3.  Nel riquadro centrale, fare clic sull'aggiornamento da installare.  
  
     Il numero di versione dell'estensione aggiornata viene visualizzato nel riquadro di destra, insieme ad altre informazioni.  
  
4.  Nella parte inferiore del riquadro di destra, fare clic su **aggiornamento**.  
  
### Per pubblicare un aggiornamento di un'estensione  
  
1.  In Visual Studio, aprire la soluzione per l'estensione che si desidera aggiornare. Apportare le modifiche.  
  
    > [!IMPORTANT]
    >  Senza segno che tutte le estensioni di utente non vengono aggiornate automaticamente. È sempre necessario firmare le estensioni.  
  
2.  In **Esplora**, aprire source.extension.manifest.  
  
3.  Nella finestra di progettazione del manifesto, aumentare il valore del numero nel **versione** campo.  
  
4.  Salvare la soluzione e compilarla.  
  
5.  Caricare il nuovo file con estensione VSIX \(nella cartella \\bin\\Debug\\ del progetto\) per il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web.  
  
     Quando si apre un utente che dispone di una versione precedente dell'estensione **estensioni e aggiornamenti**, la nuova versione verrà visualizzato nel **aggiornamenti** elenco, a condizione che lo strumento è impostato per la ricerca di aggiornamenti.  
  
     È possibile abilitare o disabilitare il controllo automatico per gli aggiornamenti nella parte inferiore del **aggiornamenti** riquadro \(**abilitare o disabilitare il rilevamento automatico degli aggiornamenti disponibili**\), le modifiche di **Controlla aggiornamenti** impostazione in **Strumenti \/ opzioni \/ ambiente \/ estensioni e aggiornamenti**.  
  
    > [!NOTE]
    >  A partire da Visual Studio 2015 Update 2, è possibile specificare \(in **Strumenti \/ opzioni \/ ambiente \/ estensioni e aggiornamenti**\) se si desidera aggiornamenti automatici per le estensioni per utente, tutte le estensioni di utente o entrambi \(impostazione predefinita\).  
  
## Vedere anche  
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)