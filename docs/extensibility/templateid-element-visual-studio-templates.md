---
title: Elemento TemplateID (modelli di Visual Studio) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: a69f3c22a6984c0ce18052e18dcf0ba4603d0c31
ms.lasthandoff: 02/22/2017

---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelli di Visual Studio)
Specifica un identificatore per un modello di elemento che è suddivisa in un gruppo di modelli di elemento per il [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) elemento.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateID >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<TemplateID> ... </TemplateID>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 Oggetto `string` che rappresenta un identificatore per un modello di elemento che è suddivisa in un gruppo di modelli di elemento per il `TemplateGroupID` elemento.  
  
## <a name="remarks"></a>Note  
 `TemplateID` è un elemento facoltativo.  
  
 Se un file. vstemplate omette il `TemplateID` elemento, il [nome](../extensibility/name-element-visual-studio-templates.md) elemento viene utilizzato come identificatore per il modello.  
  
 Il valore di `TemplateID` elemento viene utilizzato la registrazione nel sistema di progetto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) per filtrare i modelli visualizzati nel **Aggiungi nuovo elemento** la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
