---
title: "Modello di progetto VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "distribuzione di pacchetti"
  - "pubblicare l'estensione"
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Modello di progetto VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare il modello di progetto VSIX per includere una o più estensioni di Visual Studio in un progetto VSIX e quindi pubblicare il pacchetto nel [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web.  
  
 La distribuzione VSIX supporta package VS, gli assembly, MEF componenti, i modelli di progetto, modelli di elemento, i controlli della casella degli strumenti e tipi di estensione personalizzati.  
  
> [!NOTE]
>  Per utilizzare progetti VSIX, è necessario installare Visual Studio SDK. Per ulteriori informazioni sul SDK di Visual Studio, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Dove trovare il modello di progetto VSIX  
 Il modello di progetto VSIX è disponibile nel **Nuovo progetto** la finestra di dialogo. Espandere il **Visual Basic** nodo o **Visual c\#** nodo e quindi scegliere **estendibilità**.  
  
> [!TIP]
>  È necessario assicurarsi che .NET Framework 4.5 o successiva è specificato nella casella a discesa nella parte superiore del **Nuovo progetto** la finestra di dialogo.  
  
## Utilizzi del modello di progetto VSIX  
 Il modello di progetto VSIX ha due utilizzi principali:  
  
-   Per distribuire modelli di progetto, modelli di elementi e altre estensioni che non dispongono già di supporto VSIX.  
  
-   Per disporre gli output di più estensioni nel pacchetto una distribuzione.  
  
 Non è necessario utilizzare il modello di progetto VSIX per distribuire i package VS o altri tipi di estensioni che dispongono di VSIX.  
  
## Assemblaggio di un'estensione in un progetto VSIX vuoto  
 È possibile distribuire un'estensione esistente o un'estensione che non dispongono di VSIX, mediante il wrapping in un progetto VSIX vuoto. L'estensione per eseguire il wrapping deve essere di un tipo supportato da di [schema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### Per il pacchetto di un'estensione tramite un progetto VSIX  
  
1.  Compilare i progetti che costituiscono l'estensione.  
  
2.  Creare un progetto VSIX tramite il **progetto VSIX** modello.  
  
     Source.Extension.vsixmanifest viene aperto in **Progettazione manifesto**.  
  
3.  Nel **asset** scheda, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
4.  Nel **tipo** elenco, scegliere il tipo di estensione da aggiungere.  
  
5.  Per aggiungere un elemento di estensione o il contenuto che è incluso nella soluzione corrente \(ad esempio, un modello di elemento o un assembly compilato\), procedere come segue:  
  
    1.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
    2.  Nel **progetto** elenco, scegliere il nome dell'estensione.  
  
    3.  Nel **Embed in questa cartella** immettere il nome di una cartella in cui si desidera incorporare la risorsa e quindi scegliere il **OK** pulsante.  
  
6.  Per aggiungere un'estensione o un elemento di contenuto che non è incluso nella soluzione corrente, eseguire la procedura seguente:  
  
    1.  Nel **origine** nella casella di riepilogo, scegliere **File in filesystem**.  
  
    2.  Nel **percorso** campo, immettere il percorso completo del file di estensione compilata o compressa oppure utilizzare il **Sfoglia** pulsante per individuare il file.  
  
    3.  Nel **Embed in questa cartella** immettere il nome di una cartella in cui si desidera incorporare la risorsa e quindi scegliere il **OK** pulsante.  
  
7.  Se si desidera il pacchetto include estensioni aggiuntive, aggiungerle nello stesso modo.  
  
8.  Compilare la soluzione.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Compila un file con estensione VSIX che contiene un file di manifesto VSIX, un file con estensione XML \[Content\_Types\] e tutte le risorse di estensione che è stato aggiunto al progetto.  
  
## Vedere anche  
 [Riferimento dello Schema 2.0 estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)