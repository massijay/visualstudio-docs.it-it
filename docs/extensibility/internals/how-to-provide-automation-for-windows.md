---
title: "Procedura: consentire l&#39;automazione per Windows | Microsoft Docs"
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
  - "automazione [Visual Studio SDK], le finestre degli strumenti"
  - "finestre degli strumenti, automazione"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: consentire l&#39;automazione per Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile fornire l'automazione per il documento e le finestre degli strumenti.  La specificazione di automazione è consigliabile ogni volta che si desidera rendere disponibili agli oggetti ActiveX in una finestra e l'ambiente non fornisce un oggetto ActiveX pronto, come in un elenco attività.  
  
## Automazione per le finestre degli strumenti  
 L'ambiente fornisce l'automazione in una finestra degli strumenti restituendo un oggetto standard di <xref:EnvDTE.Window> come illustrato nella procedura riportata di seguito:  
  
#### Per fornire automazione per le finestre degli strumenti  
  
1.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> tramite l'ambiente con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> come parametro di `VSFPROPID` per ottenere l'oggetto di `Window` .  
  
2.  Quando un chiamante richiede un oggetto di automazione VSPackage\-specifico per la finestra degli strumenti con <xref:EnvDTE.Window.Object%2A>, l'ambiente chiama `QueryInterface` per `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o le interfacce di `IDispatch` .  sia `IExtensibleObject` che `IVsExtensibleObject` forniscono un metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> .  
  
3.  Quando l'ambiente viene quindi chiamato il metodo di `GetAutomationObject` che passa `NULL`, rispondere passato nuovamente l'oggetto VSPackage\-specifico.  
  
4.  Se la chiamata al metodo `QueryInterface` per `IExtensibleObject` e l'esito negativo di `IVsExtensibleObject` , nell'ambiente chiama `QueryInterface` per `IDispatch`.  
  
## Automazione per le finestre di documento  
 Un oggetto di <xref:EnvDTE.Document> standard è disponibile anche dall'ambiente, sebbene un editor può avere la propria implementazione dell'oggetto di `T:EnvDTE.Document` implementando l'interfaccia di `IExtensibleObject` e risposta a `GetAutomationObject`.  
  
 Inoltre, un editor possibile fornire un oggetto di automazione VSPackage\-specifico, recuperato dal metodo di <xref:EnvDTE.Document.Object%2A> , implementando interfacce di `IExtensibleObject` o di `IVsExtensibleObject` .  [Esempi di VSSDK](../../misc/vssdk-samples.md) Consente un oggetto di automazione documento\-specifico RTF.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>