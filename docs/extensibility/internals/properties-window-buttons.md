---
title: "Pulsanti della finestra propriet&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Finestra Proprietà, i pulsanti"
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Pulsanti della finestra propriet&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A seconda del linguaggio di sviluppo e il tipo del prodotto, alcuni pulsanti visualizzare per impostazione predefinita nella barra degli strumenti della finestra di **Proprietà** .  In tutti i casi, **per categoria**, i pulsanti di **In ordine alfabetico**, di **Proprietà**e di **Pagine delle proprietà** visualizzare.  In Visual c\# e Visual Basic, il pulsante di **eventi** viene visualizzato.  In alcuni progetti Visual C\+\+, **messaggi di VC\+\+** e i pulsanti di **VC override** visualizzare.  I pulsanti aggiuntivi possono essere visualizzati per altri tipi di progetto.  Per ulteriori informazioni sui pulsanti nella finestra di **Proprietà** , vedere [Finestra Proprietà](../../ide/reference/properties-window.md).  
  
## Implementazione dei pulsanti della Finestra Proprietà  
 Quando si fa clic sul pulsante di **per categoria** , Visual Studio chiama l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> sull'oggetto che ha lo stato attivo per ordinare le relative proprietà per categoria.  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> viene implementato in l `IDispatch` viene presentato nella finestra di **Proprietà** .  
  
 Vi sono 11 categoria predefinita della proprietà, che contengono valori negativi.  È possibile definire categorie personalizzate, ma è consigliabile assegnare loro valori positivi per poterle distinguere le categorie predefinite.  
  
 Il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> restituisce il valore appropriato di categoria di proprietà per la proprietà specificata.  Il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> restituisce una stringa contenente il nome della categoria.  È necessario fornire solo il supporto per i valori personalizzati di categoria perché Visual Studio riconosce i valori standard di categoria della proprietà.  
  
 Quando si fa clic sul pulsante di **In ordine alfabetico** , le proprietà vengono visualizzate in ordine alfabetico in base al nome.  I nomi vengono recuperati da `IDispatch` come un algoritmo di ordinamento localizzato.  
  
 Quando la finestra di **Proprietà** è aperta, il pulsante di **Proprietà** automaticamente viene illustrato come selezionare.  In altre parti dell'ambiente, lo stesso pulsante visualizza e è possibile fare clic su per visualizzare la finestra di **Proprietà** .  
  
 Il pulsante di **Pagine delle proprietà** non è disponibile se `ISpecifyPropertyPages` non viene implementato per l'oggetto selezionato.  Le pagine delle proprietà visualizzate le proprietà di distribuzione che sono in genere associati alle soluzioni e i progetti, ma possono inoltre essere associate agli elementi di progetto \(ad esempio, in Visual C\+\+\).  
  
> [!NOTE]
>  Non è possibile aggiungere i pulsanti della barra degli strumenti alla finestra di **Proprietà** utilizzando il codice non gestito.  Per aggiungere un pulsante della barra degli strumenti, è necessario creare un oggetto gestito che deriva da <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)