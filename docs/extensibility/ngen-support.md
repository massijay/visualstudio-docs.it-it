---
title: Supporto di Ngen in VSIX v3 | Documenti di Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>Supporto di Ngen in VSIX v3

Con Visual Studio 2017 e il nuovo v3 VSIX estensione (versione 3) manifesto formato, l'estensione per gli sviluppatori possono ora "ngen" gli assembly in fase di installazione.

Di seguito è riportato un estratto da MSDN che spiega quali "ngen" viene:

>Il generatore di immagini native (Ngen.exe) consente di migliorare le prestazioni delle applicazioni gestite. Questo strumento crea immagini native, ovvero file contenenti codice macchina compilato specifico del processore, e le installa nella cache delle immagini native del computer locale. Il runtime può usare le immagini native della cache anziché il compilatore Just-In-Time (JIT) per compilare l'assembly originale.
>
>da [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Per poter "ngen" un assembly, il progetto VSIX deve essere installato "per istanza per computer". Questo può essere abilitato selezionando la casella di controllo "all users" nella finestra di progettazione Extension. vsixmanifest:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Come abilitare Ngen

Per abilitare ngen per un assembly, è possibile utilizzare il **proprietà** finestra in Visual Studio.

Esistono 4 proprietà che è possibile impostare:

1. **Ngen** (booleano): se true, il programma di installazione di Visual Studio verrà "ngen" dell'assembly.
2. **Applicazione Ngen** (stringa) – Ngen offre la possibilità di utilizzare file app. config dell'applicazione per risolvere le dipendenze dell'assembly. Questo valore deve essere impostato a un'applicazione il cui file app. config si desidera utilizzare (relativo alla directory di installazione di Visual Studio).
3. **Architettura di Ngen** (enumerazione) – l'architettura per compilare in modo nativo l'assembly. Le opzioni sono: una. B NotSpecified. X86 c. X64 d. Tutti
4. **Priorità Ngen** (numero intero compreso tra 1 e 3): livello di priorità Ngen è documentata in [livelli di priorità Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Di seguito viene illustrato il **proprietà** finestra in azione:

![Ngen nelle proprietà](media/ngen-in-properties.png)

Metadati verrà aggiunto il riferimento al progetto all'interno di file con estensione csproj del progetto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Nota:** è possibile modificare il file con estensione csproj direttamente, se si preferisce.

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche di progettazione proprietà si applicano soltanto ai riferimenti al progetto; è possibile impostare i metadati di Ngen per gli elementi all'interno del progetto anche (con gli stessi metodi descritti in precedenza) finché gli elementi sono assembly .NET.