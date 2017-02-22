---
title: "Interfaccia della procedura guidata (IDTWizard) | Microsoft Docs"
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
  - "Interfaccia IDTWizard"
  - "procedure guidate, interfaccia"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfaccia della procedura guidata (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'ambiente di sviluppo \(IDE\) integrato \(IDE\) utilizza l'interfaccia di <xref:EnvDTE.IDTWizard> per comunicare con le procedure guidate.  Le procedure guidate devono implementare questa interfaccia per essere installato nell'IDE.  
  
 Il metodo di <xref:EnvDTE.IDTWizard.Execute%2A> è l'unico metodo associato con l'interfaccia di <xref:EnvDTE.IDTWizard> .  Le procedure guidate implementano questo metodo e l'ide chiama il metodo sull'interfaccia.  Nell'esempio seguente viene illustrata la firma del metodo.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 Il meccanismo di avvio è simile per sia **nuovo progetto** che le procedure guidate di **Aggiungi nuovo elemento** .  Per avviare uno, chiama l'interfaccia di <xref:EnvDTE.IDTWizard> definita in Dteinternal.h.  L'unica differenza è il set di parametri personalizzate e di contesto passati all'interfaccia quando l'interfaccia è denominata.  
  
 Le informazioni seguenti descrivono l'interfaccia di <xref:EnvDTE.IDTWizard> che le procedure guidate devono implementare per lavorare nell'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  L'ide chiama il metodo di <xref:EnvDTE.IDTWizard.Execute%2A> nella procedura guidata, passando le operazioni seguenti:  
  
-   L'oggetto DTE  
  
     L'oggetto DTE è la radice del modello di automazione.  
  
-   Un handle di finestra di dialogo della finestra come illustrato nel segmento di codice, `hwndOwner ([in] long)`.  
  
     La procedura guidata utilizza questo `hwndOwner` come elemento padre per la finestra di dialogo della procedura guidata.  
  
-   I parametri di contesto sono passato all'interfaccia come variant per SAFEARRAY come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     I parametri di contesto contengono una matrice di valori specifici del tipo di procedura guidata che viene avviata e lo stato corrente del progetto.  L'ide passa i parametri di contesto alla procedura guidata.  Per ulteriori informazioni, vedere [Parametri di contesto](../../extensibility/internals/context-parameters.md).  
  
-   Parametri personalizzati passati all'interfaccia come variant per SAFEARRAY come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     I parametri personalizzati contengono una matrice di parametri definiti dall'utente.  Un file VSZ passare i parametri personalizzati all'IDE.  I valori sono determinati dalle istruzioni di `Param=` .  Per ulteriori informazioni, vedere [Parametri personalizzati](../../extensibility/internals/custom-parameters.md).  
  
-   i valori restituiti per l'interfaccia sono  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## Vedere anche  
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [Procedura guidata \(. File vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)