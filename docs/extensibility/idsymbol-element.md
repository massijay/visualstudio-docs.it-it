---
title: Elemento IDSymbol | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d05dd013be9a3d6c4a173a5c7abc7a01ef2d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
Il `IDSymbol` elemento contiene l'ID della coppia GUID: ID che rappresenta un menu, gruppo o comando. Il GUID fornito dall'elemento padre `GuidSymbol` elemento. Il `IDSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per l'ID, che è contenuto nel `value` attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|name|Obbligatorio. Nome del simbolo ID.|  
|valore|Obbligatorio. Valore ID numerico del simbolo ID.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene il GUID della coppia GUID: ID che rappresenta un menu, gruppo o comando. Raggruppa gli elementi `IDSymbol`.|  
  
## <a name="remarks"></a>Note  
 Ogni `IDSymbol` elemento in un determinato `GuidSymbol` elemento deve essere univoco `value`. Tuttavia, `IDSymbol` gli elementi che hanno valori identici possono esistere in un pacchetto come hanno elementi padre diversi.  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)