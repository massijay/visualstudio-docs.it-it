---
title: "CA2210: Gli assembly devono avere nomi sicuri validi | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AssembliesShouldHaveValidStrongNames"
  - "CA2210"
helpviewer_keywords: 
  - "AssembliesShouldHaveValidStrongNames"
  - "CA2210"
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2210: Gli assembly devono avere nomi sicuri validi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AssembliesShouldHaveValidStrongNames|  
|CheckId|CA2210|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un assembly non è firmato con un nome sicuro, il nome sicuro non può essere verificato oppure il nome sicuro non sarebbe valido senza le impostazioni correnti del Registro di sistema del computer.  
  
## Descrizione della regola  
 Questa regola recupera e verifica il nome sicuro di un assembly.  Si verifica una violazione se qualsiasi delle seguenti condizioni è vera:  
  
-   L'assembly non presenta un nome sicuro.  
  
-   L'assembly è stato alterato dopo la firma.  
  
-   L'assembly presenta una firma ritardata.  
  
-   L'assembly è stato firmato in modo errato o il processo di firma non è riuscito.  
  
-   L'assembly richiede impostazioni del Registro di sistema per superare la verifica.  Ad esempio, è stato utilizzato lo strumento Nome sicuro \(Sn.exe\) per ignorare la verifica dell'assembly.  
  
 Il nome sicuro protegge i client dal caricamento involontario di un assembly alterato.  Gli assembly con nomi sicuri non devono essere distribuiti al di fuori di scenari molto limitati.  Se si condividono o distribuiscono assembly non firmati correttamente, l'assembly può essere alterato, non essere caricato in Common Language Runtime oppure l'utente potrebbe avere la necessità di disabilitare la verifica nel proprio computer.  Un assembly senza un nome sicuro presenta i seguenti svantaggi:  
  
-   Non è possibile verificarne l'origine.  
  
-   In Common Language Runtime non è possibile avvisare gli utenti se il contenuto dell'assembly è stato alterato.  
  
-   Non può essere caricato nella Global Assembly Cache.  
  
 Si noti che per caricare e analizzare un assembly con firma ritardata è necessario disabilitare la verifica per l'assembly.  
  
## Come correggere le violazioni  
 **Per creare una file di chiavi**  
  
 Utilizzare una delle seguenti procedure:  
  
-   Utilizzare lo strumento Assembly Linker \(Al.exe\) fornito da [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
-   Per [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] v1.0 o v1.1, utilizzare l'attributo <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>.  
  
-   Per [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilizzare l'opzione del compilatore `/keyfile` o `/keycontainer` \(opzione del linker [\/KEYFILE \(Specifica una chiave o una coppia di chiavi per firmare un assembly\)](/visual-cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) o [\/KEYCONTAINER \(Specifica un contenitore di chiavi per firmare un assembly\)](/visual-cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) in C\+\+\).  
  
 **Per firmare l'assembly con un nome sicuro in Visual Studio**  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aprire la soluzione.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.  
  
3.  Fare clic sulla scheda **Firma** e selezionare la casella di controllo **Firma assembly**.  
  
4.  Da **Scegli un file chiave con nome sicuro** selezionare **Nuovo**.  
  
     Verrà visualizzata la finestra **Crea chiave con nome sicuro**.  
  
5.  In **Nome file di chiave** digitare un nome per la chiave con nome sicuro.  
  
6.  Scegliere se proteggere la chiave con una password, quindi scegliere **OK**.  
  
7.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Compila**.  
  
 **Per firmare l'assembly con un nome sicuro all'esterno di Visual Studio**  
  
-   Utilizzare lo strumento del nome sicuro \(Sn.exe\) fornito da [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK.  Per ulteriori informazioni, vedere [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo se l'assembly è utilizzato in un ambiente dove non si pone il problema di alterazione del contenuto.  
  
## Vedere anche  
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>   
 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>   
 [Procedura: firmare un assembly con un nome sicuro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)