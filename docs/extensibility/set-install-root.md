---
title: L&quot;installazione all&quot;esterno della cartella estensioni con VSIX v3 | Documenti di Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
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
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>L'installazione all'esterno della cartella di estensioni

A partire da Visual Studio 2017 e VSIX v3 (versione 3), è ora disponibile un supporto per l'installazione di risorse di estensione all'esterno nella cartella extensions. Attualmente, i percorsi seguenti sono abilitati come percorsi di installazione valida (dove [installdir] viene mappata alla directory di installazione dell'istanza di Visual Studio):

* \Common7\IDE\PublicAssemblies. [installdir]
* \Common7\IDE\ReferenceAssemblies [installdir]
* \MSBuild [installdir]
* \Schemas [installdir]
* \Licenses [installdir]
* \RemoteDebugger [installdir]
* \VSTargets [installdir]

>**Nota:** il formato VSIX non consente di installare di fuori della struttura di cartelle di installazione di Visual Studio.

Per supportare l'installazione di queste directory, il progetto VSIX deve essere installato "per istanza per computer". Questo può essere abilitato selezionando la casella di controllo "all users" nella finestra di progettazione Extension. vsixmanifest:

![controllare tutti gli utenti](~/extensibility/media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Come impostare la directory principale di installazione

Per impostare le directory di installazione, è possibile utilizzare il **proprietà** finestra in Visual Studio. Ad esempio, è possibile impostare il `InstallRoot` proprietà di un riferimento di progetto a uno dei percorsi precedenti:

![installare le proprietà radice](~/extensibility/media/install-root-properties.png)

Verranno aggiunti alcuni metadati corrispondente `ProjectReference` proprietà all'interno di file con estensione csproj del progetto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Nota:** è possibile modificare il file con estensione csproj direttamente, se si preferisce.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Come impostare un sottopercorso sotto la directory principale di installazione

Se si desidera installare un sottopercorso sotto il `InstallRoot`, è possibile farlo impostando il `VsixSubPath` come proprietà di `InstallRoot` proprietà. Ad esempio, supponiamo si desidera visualizzare l'output del riferimento di progetto per installare ' [installdir]\MSBuild\MyCompany\MySDK\1.0'. Questo scopo, usiamo facilmente con la finestra di progettazione di proprietà:

![set sottopercorso](~/extensibility/media/set-subpath.png)

Le modifiche corrispondenti apportate csproj avrà un aspetto simile al seguente:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche di progettazione proprietà si applicano soltanto ai riferimenti al progetto; è possibile impostare il `InstallRoot` metadati per gli elementi all'interno del progetto anche (con gli stessi metodi descritti in precedenza).

