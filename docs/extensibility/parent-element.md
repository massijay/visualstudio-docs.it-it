---
title: Elemento padre | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0da0bd0aceaccdbf8d2cf11fd3490a3e5810ad2e
ms.lasthandoff: 02/22/2017

---
# <a name="parent-element"></a>Elemento padre
L'elemento padre di una pulsante o una casella combinata può essere solo un gruppo. L'elemento padre di un menu o un gruppo può essere qualsiasi altro menu o gruppo. In un [CommandPlacement elemento](../extensibility/commandplacement-element.md), questo elemento è obbligatorio; in tutte le altre istanze è facoltativa. Se questo elemento viene omesso, l'elemento padre di `Group_Undefined:0` verrà implicita.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Identificatore GUID di GUID o ID del comando.|  
|ID|Obbligatorio. Identificatore di comando ID GUID/ID.|  
  
### <a name="child-elements"></a>Elementi figlio  
 None  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che fornisce un VSPackage all'ambiente di sviluppo integrato (IDE). Ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate.|  
|[Elemento di pulsanti](../extensibility/buttons-element.md)|Gruppi [elemento Button](../extensibility/button-element.md) elementi.|  
|[Elemento menu](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comando di un package VS.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella di comandi di Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
