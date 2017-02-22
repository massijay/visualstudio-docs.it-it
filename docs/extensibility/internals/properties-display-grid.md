---
title: "Propriet&#224; Visualizza griglia | Microsoft Docs"
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
  - "griglia delle proprietà [Visual Studio SDK]"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Propriet&#224; Visualizza griglia
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visualizza i campi della finestra di **Proprietà** all'interno di una griglia.  La colonna sinistra contiene i nomi delle proprietà; la colonna destra contiene i valori della proprietà.  
  
## Utilizzo della griglia  
 L'elenco a due colonne vengono visualizzate le proprietà dell'configurazione\-indipendente che possono essere modificate in fase di progettazione e le relative impostazioni correnti.  Si noti che se un progetto ha un `IVsOutputGroup` che non desidera comprimere o distribuire, è sufficiente non inserire l'output in un gruppo.  Una proprietà può essere impostata come nascosta, ad esempio, implementando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> .  In particolare, nascondere le proprietà che fanno vedere le proprietà figlio [Nascondere le proprietà con proprietà figlio](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Per inserire le informazioni sulla finestra di **Proprietà** , l'ide utilizza <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene chiamato da Vspackage per ogni finestra che contiene gli oggetti selezionabili con le proprietà correlate da visualizzare nella finestra di **Proprietà** .  L'implementazione di Esplora Soluzioni di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chiama `GetProperty` utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> nella gerarchia del progetto per acquisire gli oggetti browseable nella gerarchia.  
  
 Se il package VS non supporta <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, l'ide tenta di utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> utilizzando il valore per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> che l'elemento o gli elementi di struttura fornisce.  
  
 Il progetto VSPackage non è necessario creare <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché il pacchetto Ido\-fornito la finestra che lo implementa \(ad esempio, **Esplora soluzioni**\) crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> al nome.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è costituito da tre metodi chiamati dall'IDE:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene il numero di oggetti selezionati da visualizzare nella finestra di **Proprietà** .  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> restituisce oggetti di `IDispatch` selezionati per essere visualizzato nella finestra di **Proprietà** .  
  
-   l'entity\_M:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects\(System.UInt32, System.Object\[\], System.UInt32\)  In questo modo il package VS aggiornarsi visivamente la selezione viene visualizzato nell'interfaccia utente.  
  
 La finestra di **Proprietà** estrae le informazioni dagli oggetti di `IDispatch` per recuperare le proprietà che rappresentano gli spostamenti.  Il browser delle proprietà utilizza `IDispatch` per chiedere all'oggetto proprietà supporta eseguire una query `ITypeInfo`, ottenuto da `IDispatch::GetTypeInfo`.  Il browser quindi utilizzare questi valori per popolare la finestra di **Proprietà** e per modificare i valori delle singole proprietà verranno visualizzate nella griglia.  Le informazioni delle proprietà vengono conservate nell'oggetto stesso.  
  
 Poiché gli oggetti restituiti supportano `IDispatch`, il chiamante può ottenere informazioni quali il nome dell'oggetto chiamando `IDispatch::Invoke` o `ITypeInfo::Invoke` con un identificatore predefinito dispatch \(DISPID\) che rappresenta le informazioni desiderate.  I dispid dichiarato è negativo verificare che non sia in conflitto con gli identificatori definiti dall'utente.  
  
 Tipi diversi di visualizzare la finestra di **Proprietà** di campi in base agli attributi di proprietà specifiche di un oggetto selezionato.  Questi campi sono incluse le caselle di testo, elenchi a discesa e collegamenti alle finestre di dialogo editor personalizzato.  
  
-   I valori contenuti in un elenco enumerato vengono recuperati da una query di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> a `IDispatch`.  I valori ottenuti da un elenco enumerato possono essere modificati nella griglia delle proprietà facendo doppio clic sul nome del campo, oppure facendo clic sul valore e selezionando il nuovo valore dall'elenco a discesa.  Per le proprietà che hanno predefinito delle impostazioni dagli elenchi enumerati, fare doppio clic sul nome della proprietà nei cicli di elenco di proprietà con le opzioni disponibili.  Per le proprietà predefinite con solo due opzioni, quali true\/false, fare doppio clic sul nome della proprietà per passare tra le opzioni.  
  
-   Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> è `false`, per indicare che il valore è stato modificato, il valore viene visualizzato in grassetto.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> viene utilizzato per determinare se il valore può essere reimpostato al valore originale.  In questo caso, è possibile ripristinare l'impostazione predefinita fare clic con il pulsante destro del mouse sul valore e scegliendo **Reimposta** dal menu visualizza.  In caso contrario, è necessario modificare il valore del nuovo valore predefinito manualmente.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> consente di localizzare e verrà nascosta i nomi delle proprietà vengono visualizzati durante la fase di progettazione, ma non influisce sui nomi delle proprietà visualizzate in fase di esecuzione.  
  
-   Fare clic sul pulsante con i puntini di sospensione \(...\) visualizzare un elenco di valori di proprietà dal quale l'utente può selezionare \(ad esempio una selezione colori o una polizza\).  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> fornisce questi valori.  
  
## Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)