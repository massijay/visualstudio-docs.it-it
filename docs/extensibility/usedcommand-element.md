---
title: Elemento UsedCommand | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b3974c9103a385badc56fda759ee95ef3a40a93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Consente a un pacchetto VSPackage per accedere a un comando che è definito in un altro file con estensione vsct. Ad esempio, se il pacchetto VSPackage utilizza lo standard **copia** comando, il quale è definito dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, per aggiungere il comando a un menu o una barra degli strumenti senza implementarla nuovamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Il GUID della coppia ID GUID che identifica il comando.|  
|ID|Obbligatorio. L'ID della coppia ID GUID che identifica il comando.|  
|Condizione|Parametro facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Nessuno||  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Raggruppa gli elementi di UsedCommand e altri raggruppamenti UsedCommands.|  
  
## <a name="remarks"></a>Note  
 Tramite l'aggiunta di un comando per il `<UsedCommands>` elemento, un pacchetto VSPackage informa il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente che il pacchetto VSPackage richiede che il comando. È necessario aggiungere un `<UsedCommand>` elemento per il pacchetto richiede che tutti i comandi potrebbe non essere inclusi in tutte le versioni e le configurazioni di Visual Studio. Ad esempio, se il pacchetto chiama un comando che è specifico di Visual C++, il comando non sarà disponibile per gli utenti di Visual Web Developer, a meno di non includere un `<UsedCommand>` elemento per il comando.  
  
## <a name="example"></a>Esempio  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)