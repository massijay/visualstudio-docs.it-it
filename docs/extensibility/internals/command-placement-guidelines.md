---
title: Linee guida per la posizione di comando | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
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
ms.openlocfilehash: ca84800a199e9db420379697051fece598eb9295
ms.lasthandoff: 02/22/2017

---
# <a name="command-placement-guidelines"></a>Linee guida per il posizionamento di comando
Procedure consigliate per il posizionamento comandi nell'ambiente di sviluppo integrato (IDE) di Visual Studio variano a seconda delle dimensioni del set di comandi. I comandi definiti e posizionati in base alle informazioni nel file. vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Procedure consigliate per tutti i set di comandi  
 Per ogni set di comandi, attenersi alle seguenti indicazioni:  
  
-   Preparare in anticipo un grafico della struttura di comando. Identificare i comandi, caselle combinate, gruppi di comandi e menu di scelta rapida che verranno utilizzati in più posizioni.  
  
-   Comandi che vengono visualizzati nello stesso gruppo devono essere correlati.  
  
-   Gruppi che contengono un unico comando sono consentiti.  
  
-   Pacchetti non sono possibile aggiungere un numero elevato di comandi a menu di Visual Studio esistenti. Invece, è necessario creare menu o sottomenu per ospitare i nuovi comandi.  
  
-   Quando si inserisce un comando in un menu esistente, nome, il comando in modo che il suo scopo è chiaro e non essere confuso con comandi esistenti.  
  
## <a name="best-practices-for-small-command-sets"></a>Procedure consigliate per i set di comandi di piccole dimensioni  
 Inoltre, se si sta sviluppando un VSPackage contenente solo alcuni comandi, seguire queste linee guida:  
  
-   Quando possibile, utilizzare il [elemento padre](../../extensibility/parent-element.md) di un comando, casella combinata, gruppo o menu del figlio per inserirlo nel gruppo appropriato.  
  
-   Assegnare questi gruppi di menu visualizzati dal VSPackage.  
  
-   L'elemento padre di un menu del figlio o un comando deve essere un [elemento gruppo](../../extensibility/group-element.md). Assegnare ai gruppi di comandi e i menu figlio e quindi assegnare i gruppi di menu padre.  
  
-   È possibile inserire un comando in altri gruppi aggiungendo un [CommandPlacements elemento](../../extensibility/commandplacements-element.md) sezione dopo la definizione del comando, quindi aggiungere il `CommandPlacements Element` un [CommandPlacement elemento](../../extensibility/commandplacement-element.md) per ogni gruppo aggiuntiva.  
  
## <a name="best-practices-for-large-command-sets"></a>Procedure consigliate per i set di comandi di grandi dimensioni  
 Inoltre, se il pacchetto Visual Studio sono molti i comandi che verranno visualizzato in più contesti, seguire queste linee guida:  
  
-   Rendere i menu, gruppi e comandi self-relazione padre-figlio. Ovvero, non si assegna un `Parent Element` nella definizione dell'elemento.  
  
-   Utilizzare `CommandPlacement Element` voci di `CommandPlacements Element` sezione inserire menu, gruppi e i comandi nei menu del padre e gruppi.  
  
-   Nel `CommandPlacements` sezione, le voci che popolano un determinato menu o il gruppo deve essere adiacente. Ciò consente di migliorare la leggibilità e rende il `Priority` più semplice determinare le posizioni in classifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabella di comandi di Visual Studio (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
