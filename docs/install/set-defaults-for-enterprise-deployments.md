---
title: Impostare i valori predefiniti per le distribuzioni aziendali di Visual Studio | Microsoft Docs
description: Criteri di dominio e altre operazioni di configurazione per la distribuzione aziendale di Visual Studio.
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: heaths
manager: ghogen
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
ms.sourcegitcommit: 8f38b2707376d4bee8852ad107980fa925114d99
ms.openlocfilehash: 05c5fd9e4be4cbf7d40e27c7c97793bc2466efe3
ms.contentlocale: it-it
ms.lasthandoff: 05/05/2017

---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Impostare i valori predefiniti per le distribuzioni aziendali di Visual Studio

È possibile impostare i criteri del Registro di sistema che influiscono sulla distribuzione di Visual Studio. Questi criteri sono globali per il nuovo programma di installazione e incidono sugli aspetti seguenti:

- Dove vengono installati alcuni pacchetti condivisi con altre versioni o istanze
- Dove vengono memorizzati i pacchetti
- Se vengono memorizzati tutti i pacchetti

È possibile impostare alcuni di questi criteri usando le [opzioni della riga di comando](use-command-line-parameters-to-install-visual-studio.md), impostare i valori del Registro di sistema sul proprio computer o persino distribuirli applicando Criteri di gruppo all'interno dell'organizzazione.

## <a name="registry-keys"></a>Chiavi del Registro di sistema

Esistono diverse percorsi in cui è possibile impostare i valori predefiniti dell'organizzazione in modo da esercitarne il controllo tramite Criteri di gruppo o direttamente nel Registro di sistema. Visual Studio controlla in modo sequenziale se sono stati impostati criteri aziendali; non appena viene trovato un valore di criteri nell'ordine seguente, le chiavi rimanenti vengono ignorate.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (in sistemi operativi a 64 bit)

Se non ancora impostati, alcuni valori del Registro di sistema verranno impostati automaticamente la prima volta che vengono usati. In questo modo si garantisce che eventuali installazioni successive usino gli stessi valori, che vengono archiviati nella seconda chiave del Registro di sistema: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

È possibile impostare i valori del Registro di sistema seguenti.

| **Nome** | **Type** | **Default** | **Descrizione** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Directory in cui vengono archiviati i manifesti di pacchetto e, facoltativamente, i payload. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Consente di mantenere i payload dei pacchetti anche dopo l'installazione. È possibile modificare questo valore in qualsiasi momento. Disabilitando questi criteri verranno rimossi tutti i payload di pacchetti memorizzati nella cache per l'istanza da riparare o modificare. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Directory in cui sono installati alcuni pacchetti condivisi tra più versioni di istanze di Visual Studio. È possibile modificare il valore in qualsiasi momento, ma questa operazione influirà solo sulle installazioni future. I prodotti già installati nel percorso precedente devono essere spostati o potrebbero non funzionare correttamente. |

> [!IMPORTANT]
> Se si modificano i criteri del Registro di sistema `CachePath` dopo un'installazione, è necessario spostare la cache del pacchetto esistente nel nuovo percorso e verificare che sia protetto in modo che `SYSTEM` e `Administrators` abbiano il controllo completo e `Everyone` l'accesso in lettura.
> Se non si sposta o non si protegge la cache esistente, è possibile che si verifichino problemi con le installazioni future.

## <a name="see-also"></a>Vedere anche

 * [Installare Visual Studio](install-visual-studio.md)
 * [Disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md)
 * [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Report a problem with Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md) (Segnalare un problema di Visual Studio)

