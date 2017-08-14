---
title: ID dei carichi di lavoro e dei componenti dell'agente di test di Visual Studio 2017 | Microsoft Docs
description: Usare gli ID dei carichi di lavoro e dei componenti di Visual Studio per eseguire test automatizzati e test di carico da postazione remota
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: 55aea29b-1066-4e5a-aa99-fc87d4efb6d5
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c677e2b4e1be79483da15256ac1d48f302b6e749
ms.contentlocale: it-it
ms.lasthandoff: 05/13/2017

---

# <a name="visual-studio-test-agent-2017-component-directory"></a>Elenco dei componenti di Agente di test di Visual Studio 2017

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative alla pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro. È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata anche aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="test-agent"></a>Agente di test

**ID:** Microsoft.VisualStudio.Workload.TestAgent

**Descrizione:** supporta l'esecuzione di test automatizzati e test di carico in remoto

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestAgent | Funzionalità principali dell'agente di test | 15.0.26208.0 | Obbligatorio

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | Nome | Versione
--- | --- | ---
N/D | n/d | N/D


## <a name="see-also"></a>Vedere anche

* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)

