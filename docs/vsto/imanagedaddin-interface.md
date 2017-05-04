---
title: "Interfaccia IManagedAddin | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IManagedAddin (interfaccia)"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Interfaccia IManagedAddin
  Implementare l'interfaccia IManagedAddin per creare un componente che carichi componenti aggiuntivi VSTO gestiti. Questa interfaccia è stata aggiunta in Microsoft Office System 2007.  
  
## Sintassi  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## Metodi  
 La tabella seguente elenca i metodi definiti dall'interfaccia IManagedAddin.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Chiamato quando un'applicazione di Microsoft Office carica un componente aggiuntivo VSTO gestito.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Chiamato appena prima che un'applicazione di Microsoft Office scarichi un componente aggiuntivo VSTO gestito.|  
  
## Note  
 A partire da Microsoft Office System 2007, le applicazioni di Microsoft Office usano l'interfaccia IManagedAddin per consentire il caricamento di componenti aggiuntivi VSTO di Office. È possibile implementare l'interfaccia IManagedAddin per creare caricatori e runtime personalizzati per componenti aggiuntivi VSTO gestiti invece di usare il caricatore del componente aggiuntivo VSTO \(VSTOLoader.dll\) e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Per altre informazioni, vedere [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
## Modalità di caricamento dei componenti aggiuntivi gestiti  
 All'avvio di un'applicazione vengono effettuate le operazioni seguenti:  
  
1.  L'applicazione individua i componenti aggiuntivi VSTO cercando le voci nella chiave seguente del Registro di sistema:  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nome applicazione\>*\\Addins\\  
  
     Ogni voce sotto questa chiave del Registro di sistema è un ID univoco del componente aggiuntivo VSTO. In genere, corrisponde al nome dell'assembly del componente aggiuntivo VSTO.  
  
2.  L'applicazione cerca una voce `Manifest` nella voce per ciascun componente aggiuntivo VSTO.  
  
     I componenti aggiuntivi VSTO gestiti possono archiviare il percorso completo di un manifesto nella voce `Manifest` all'interno della chiave HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nome applicazione\>*\\Addins\\*\<ID componente aggiuntivo\>*. Un manifesto è un file \(in genere, un file XML\) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO.  
  
3.  Se l'applicazione individua una voce `Manifest`, prova a caricare un componente caricatore per componenti aggiuntivi VSTO gestiti. A tale scopo, l'applicazione prova a creare un oggetto COM che implementa l'interfaccia IManagedAddin.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] include un componente caricatore \(VSTOLoader.dll\) per componenti aggiuntivi VSTO. In alternativa, è possibile crearne uno personalizzato implementando l'interfaccia IManagedAddin.  
  
4.  L'applicazione chiama il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) e passa il valore della voce `Manifest`.  
  
5.  Il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) esegue le attività necessarie per caricare il componente aggiuntivo VSTO, ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO caricato.  
  
 Per altre informazioni sulle chiavi del Registro di sistema usate dalle applicazioni di Microsoft Office per individuare e caricare componenti aggiuntivi gestiti, vedere [Voci del Registro di sistema per i componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Indicazioni per l'implementazione di IManagedAddin  
 Se si implementa IManagedAddin, è necessario registrare la DLL contenente l'implementazione tramite il CLSID seguente:  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Le applicazioni di Microsoft Office usano questo CLSID per creare l'oggetto COM per l'implementazione di IManagedAddin.  
  
> [!CAUTION]  
>  Questo CLSID è inoltre usato da VSTOLoader.dll in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Se quindi si usa IManagedAddin per creare un componente caricatore e di runtime personalizzato per il componente aggiuntivo VSTO, non è possibile distribuire il componente ai computer in cui sono in esecuzione componenti aggiuntivi VSTO che si basano su [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## Vedere anche  
 [Riferimenti ad API non gestite &#40;sviluppo per Office in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  