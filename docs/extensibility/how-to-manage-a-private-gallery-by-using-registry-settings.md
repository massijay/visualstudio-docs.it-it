---
title: "Procedura: gestire una raccolta privata utilizzando le impostazioni del Registro di sistema | Microsoft Docs"
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
  - "Raccolte private VSIX, gestione"
  - "la gestione di raccolte private VSIX"
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: gestire una raccolta privata utilizzando le impostazioni del Registro di sistema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si è un amministratore o lo sviluppatore di un'estensione della Shell isolata, è possibile controllare l'accesso ai controlli, modelli e strumenti in Visual Studio Gallery, la raccolta di esempi o le raccolte private. Per rendere una raccolta disponibile o non disponibile, creare un file. pkgdef che descrive le chiavi del Registro di sistema modificati e i relativi valori.  
  
## La gestione di raccolte Private  
 È possibile creare un file. pkgdef per controllare l'accesso alle raccolte in più computer. Questo file deve essere nel formato seguente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Il `Repositories` chiave fa riferimento alla raccolta per essere abilitato o disabilitato. Raccolta di Visual Studio e la raccolta di esempi utilizzano il repository seguente GUID:  
  
-   Visual Studio Gallery: 0F45E408\-7995\-4375\-9485\-86B8DB553DC9  
  
-   Raccolta di esempi: AEB9CB40\-D8E6\-4615\-B52C\-27E307F8506C  
  
 Il `Disabled` il valore è facoltativo. Per impostazione predefinita, una raccolta è abilitata.  
  
 Il `Priority` valore determina l'ordine in cui le raccolte sono elencate nella finestra di dialogo Opzioni. Raccolta di Visual Studio ha priorità 10 e la raccolta di esempi ha priorità 20. Raccolte private avviare priorità 100. Se più raccolte hanno lo stesso valore di priorità, l'ordine in cui vengono visualizzati è determinato dai valori dei relativi localizzata `DisplayName` attributi.  
  
 Il `Protocol` valore è obbligatorio per le raccolte basate su SharePoint o Atom.  
  
 Sia `DisplayName`, o entrambi `DisplayNameResourceID` e `DisplayNamePackageGuid`, deve essere specificato. Se vengono specificati tutti, quindi la `DisplayNameResourceID` e `DisplayNamePackageGuid` coppia viene utilizzata.  
  
## La disabilitazione di un File. pkgdef utilizzando Visual Studio Gallery  
 È possibile disabilitare una raccolta in un file. pkgdef. La voce seguente disabilita la raccolta di Visual Studio:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La voce seguente disabilita la raccolta di esempi:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)