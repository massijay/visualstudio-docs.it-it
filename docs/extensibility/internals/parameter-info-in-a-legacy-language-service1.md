---
title: "Informazioni sui parametri in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio, suggerimenti (metodo)"
  - "suggerimenti (metodo)"
  - "servizi linguistici, la descrizione comando informazioni parametri"
  - "Interfaccia IVsMethodData"
  - "Informazioni sui parametri (IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Informazioni sui parametri in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La descrizione comando informazioni sul parametro IntelliSense fornisce agli utenti con i suggerimenti su dove si trovano in un costrutto di linguaggio.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## Funzionamento di descrizione comandi per informazioni di parametro  
 Quando si digita un'istruzione nell'editor, VSPackage Visualizza una finestra piccola descrizione comando contenente la definizione dell'istruzione vengono digitato. Ad esempio, se si digita un'istruzione di Microsoft Foundation Classes \(MFC\) \(ad esempio `pMainFrame ->UpdateWindow`\) e premere un tasto per iniziare a elencare i parametri, viene visualizzato un suggerimento metodo la definizione della parentesi di apertura di `UpdateWindow` metodo.  
  
 Descrizione comandi per informazioni di parametro vengono in genere utilizzati in combinazione con il completamento delle istruzioni. Che sono più utili per le lingue che dispongono di parametri o altre informazioni formattate dopo la parola chiave o il nome del metodo.  
  
 Informazioni sul parametro descrizioni comandi vengono avviate dal servizio di linguaggio tramite l'intercettazione di comando. Per intercettare i caratteri dall'utente, è necessario implementare l'oggetto servizio di linguaggio il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e passare un puntatore per la visualizzazione di testo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione, chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia. Il filtro dei comandi intercetta i comandi digitati nella finestra del codice. Monitorare le informazioni sui comandi per sapere quando visualizzare informazioni sui parametri per l'utente. È possibile utilizzare lo stesso filtro di comando per il completamento delle istruzioni, i marcatori di errore e così via.  
  
 Quando si digita una parola chiave per cui il servizio di linguaggio può fornire suggerimenti, il servizio di linguaggio crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> e viene chiamato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia per notificare l'IDE per visualizzare un suggerimento. Creare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> utilizzando `VSLocalCreateInstance` e specificando la coclasse `CLSID_VsMethodTipWindow`.`VsLocalCreateInstance` è una funzione definita in vsdoc.h di file di intestazione che chiama `QueryService` per il Registro di sistema locale e chiama `CreateInstance` su questo oggetto per il `CLSID_VsMethodTipWindow`.  
  
## Fornire un suggerimento \(metodo\)  
 Per fornire un suggerimento sul metodo, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaccia, passandogli l'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia.  
  
 Quando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> classe viene richiamata, i metodi vengono chiamati nell'ordine seguente:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Restituisce la posizione e la lunghezza dei dati nel buffer di testo corrente. In questo modo l'IDE non poco che i dati con la finestra della descrizione comando.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Restituisce il numero di metodo \(indice in base zero\) che si desidera essere visualizzato inizialmente. Ad esempio, se viene restituito zero, quindi il primo metodo di overload viene inizialmente visualizzato.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Restituisce il numero di metodi di overload che sono applicabili nel contesto corrente. Se viene restituito un valore maggiore di 1 per questo metodo, quindi la visualizzazione di testo Visualizza frecce su e giù per l'utente. Se si fa clic sulla freccia rivolta verso il basso, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodo. Se si fa clic sulla freccia in su, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metodo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Il testo della descrizione comando informazioni sul parametro è stato costruito durante diverse chiamate al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metodi.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Restituisce il numero di parametri da visualizzare nel metodo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Se viene restituito un numero di metodo corrispondente con l'overload che si desidera visualizzare, questo metodo viene chiamato, seguita da una chiamata per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informa il servizio di linguaggio per aggiornare l'editor quando viene visualizzato un suggerimento sul metodo. Nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo, chiamare il comando seguente:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Si riceve una chiamata per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo quando si chiude la finestra suggerimento di metodo.