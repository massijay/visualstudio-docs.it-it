---
title: "Attività FileClassifier | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 7
author: kempb
ms.author: kempb
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: e8c0f52f1e3e15bd2a12716fc7c93a0fbf32779e
ms.contentlocale: it-it
ms.lasthandoff: 05/30/2017

---
# <a name="fileclassifier-task"></a>Attività FileClassifier
L'attività <xref:Microsoft.Build.Tasks.Windows.FileClassifier> classifica un insieme di risorse di origine come quelle che verranno incorporate in un assembly. Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale. In caso contrario, viene incorporata in un assembly satellite.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Non usato.|  
|`CLRResourceFiles`|Non usato.|  
|`CLRSatelliteEmbeddedResource`|Non usato.|  
|`Culture`|Parametro **String** facoltativo.<br /><br /> Specifica le impostazioni cultura per la compilazione. Questo valore può essere **null** se la compilazione non è localizzabile. Se **null**, il valore predefinito corrisponde al valore minuscolo restituito da **CultureInfo.InvariantCulture**.|  
|`MainEmbeddedFiles`|Parametro di output **ITaskItem[]** facoltativo.<br /><br /> Specifica le risorse non localizzabili incorporate nell'assembly principale.|  
|`OutputType`|Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di file in cui incorporare i file di origine specificati. I valori validi sono **exe**, **winexe** e **library**.|  
|`SatelliteEmbeddedFiles`|Parametro di output **ITaskItem[]** facoltativo.<br /><br /> Specifica i file localizzabili incorporati nell'assembly satellite per le impostazioni cultura specificate dal parametro **Culture**.|  
|`SourceFiles`|Parametro **ITaskItem []** obbligatorio.<br /><br /> Specifica l'elenco di file da classificare.|  
  
## <a name="remarks"></a>Note  
 Se il parametro **Culture** non è impostato, tutte le risorse specificate usando il parametro **SourceFiles** non sono localizzabili. In caso contrario, sono localizzabili a meno che non vengano associate a un attributo **Localizable** impostato su **false**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente un singolo file di origine viene classificato come risorsa e incorporato in un assembly satellite per le impostazioni cultura Francese-Canadese (fr-CA).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
