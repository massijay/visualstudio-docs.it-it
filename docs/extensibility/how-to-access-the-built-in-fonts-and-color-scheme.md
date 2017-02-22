---
title: "Procedura: accedere ai tipi di carattere incorporati e combinazione di colori | Microsoft Docs"
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
  - "tipi di carattere, l'accesso predefinito"
  - "controllo tipo di carattere e colore [Visual Studio SDK], categorie"
  - "colori, l'accesso a schemi predefiniti"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: accedere ai tipi di carattere incorporati e combinazione di colori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ambiente di sviluppo integrato \(IDE\) di Visual Studio dispone di una combinazione di tipi di carattere e colori associata con la finestra dell'editor. È possibile accedere a questo schema tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.  
  
 Per utilizzare lo schema di colori e tipi di carattere incorporati, è necessario un VSPackage:  
  
-   Definire una categoria da utilizzare con il servizio predefinito di tipi di carattere e colori.  
  
-   Registrare la categoria con il server predefinito di tipi di carattere e colori.  
  
-   Consigliare l'IDE viene utilizzata una finestra specifica gli elementi di visualizzazione predefinite e le categorie utilizzando il `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` e `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfacce.  
  
 L'IDE utilizza la categoria risulta come handle di finestra. Nome della categoria viene visualizzato nel **Mostra impostazioni per:** casella di riepilogo a discesa il **tipi di carattere e colori** pagina delle proprietà.  
  
### Per definire una categoria utilizzando i colori e tipi di carattere incorporati  
  
1.  Creare un GUID non autorizzato.  
  
     Questo GUID viene utilizzato per identificare in modo univoco una categoria**.** Questa categoria riutilizza specifica di colori e tipi di carattere predefiniti dell'IDE.  
  
    > [!NOTE]
    >  Durante il recupero di dati carattere e colori con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> o altre interfacce, VSPackage usare questo GUID per fare riferimento a informazioni incorporate.  
  
2.  Nome della categoria deve essere aggiunto a una tabella di stringhe all'interno di file di risorse \(RC\) del package VS, in modo che possa essere localizzata in base alle necessità quando visualizzati nell'IDE di.  
  
     Per altre informazioni, vedere [Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string).  
  
### Per registrare una categoria utilizzando i colori e tipi di carattere incorporati  
  
1.  Creare un tipo speciale di voce del Registro di sistema di categoria nel percorso seguente:  
  
     \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\*\< versione di Visual Studio \>*\\FontAndColors\\*\< Category \>*\]  
  
     *\< category \>* è il nome non localizzato della categoria.  
  
2.  Popolare il Registro di sistema per l'utilizzo di tipi di carattere azionari e combinazione di colori con quattro valori:  
  
    |Nome|Tipo|Dati|Descrizione|  
    |----------|----------|----------|-----------------|  
    |Categoria|REG\_SZ|GUID|Un GUID arbitrario che identifica una categoria che contiene lo schema di carattere e colori predefinito.|  
    |Pacchetto|REG\_SZ|GUID|{F5E7E71D\-1401\-11D1\-883B\-0000F87579D2}<br /><br /> Questo GUID viene utilizzato da tutti i package VS che utilizzano le configurazioni predefinite di carattere e colori.|  
    |NameID|REG\_DWORD|ID|ID della risorsa di un nome di categoria localizzabili in VSPackage.|  
    |ToolWindowPackage|REG\_SZ|GUID|Il GUID del VSPackage il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.|  
  
3.  
  
### Per avviare l'utilizzo di fornita dal sistema di tipi di carattere e colori  
  
1.  Creare un'istanza di `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfaccia come parte dell'implementazione e l'inizializzazione della finestra.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> per ottenere un'istanza di `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaccia corrispondente all'oggetto corrente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> istanza.  
  
3.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> due volte.  
  
    -   Chiamare una volta con `VSEDITPROPID_ViewGeneral_ColorCategory`come argomento.  
  
    -   Chiamare una volta con `VSEDITPROPID_ViewGeneral_FontCategory` come argomento.  
  
     Questo imposta ed espone i servizi di tipi di carattere e colori predefiniti come proprietà della finestra.  
  
## Esempio  
 Nell'esempio seguente avvia l'utilizzo di colori e tipi di carattere incorporati.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## Vedere anche  
 [Utilizzando i tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)   
 [Recupero di tipi di carattere e le informazioni di colore per testo colorazione](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [L'accesso alle Stored carattere e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md)