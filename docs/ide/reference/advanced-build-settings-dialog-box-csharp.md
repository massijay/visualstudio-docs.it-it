---
title: Finestra di dialogo Impostazioni di compilazione avanzate (C#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 13
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 82ec5d2db35da72beb017e15d1c271f751b5f56b
ms.lasthandoff: 02/22/2017

---
# <a name="advanced-build-settings-dialog-box-c"></a>Finestra di dialogo Impostazioni di compilazione avanzate (C#)
Per specificare le proprietà di configurazione di compilazione avanzate del progetto, usare la finestra di dialogo **Impostazioni di compilazione avanzate** di **Creazione progetti**. Questa finestra di dialogo è applicabile solo ai progetti [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  
  
## <a name="general"></a>Generale  
 Le opzioni seguenti consentono di configurare le impostazioni avanzate generali.  
  
 **Versione linguaggio**  
 Specifica la versione del linguaggio da usare. Il set di funzionalità varia a seconda della versione. Questa opzione può quindi essere usata per forzare il compilatore ad attivare solo un sottoinsieme delle funzionalità implementate oppure solo le funzionalità compatibili con uno standard esistente. Le opzioni di questa impostazione sono le seguenti:  
  
-   **ISO-1**  
  
     Fa riferimento alle funzionalità standard ISO-1.  
  
-   **default**  
  
     Fa riferimento alla versione corrente.  
  
 Per altre informazioni, vedere [/langversion (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).  
  
 **Segnalazione errori interni del compilatore**  
 Specifica se gli errori del compilatore devono essere segnalati a Microsoft. Se l'opzione è impostata su **prompt**, al verificarsi di un errore del compilatore interno sarà chiesto se si vuole inviare elettronicamente a Microsoft una segnalazione errori. Se è impostata su **send**, sarà inviata automaticamente una segnalazione errori. Se è impostata su **queue**, le segnalazioni errori saranno accodate. Se è impostata su **none**, l'errore sarà segnalato soltanto nell'output di testo del compilatore. Per altre informazioni, vedere [/errorreport (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).  
  
 **Controlla overflow/underflow aritmetico**  
 Specifica se un'istruzione aritmetica su valori interi che non è inclusa nell'ambito delle parole chiave [checked](/dotnet/csharp/language-reference/keywords/checked) o [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) e che genera un valore non compreso nell'intervallo del tipo di dati genererà un'eccezione in fase di esecuzione. Per altre informazioni, vedere [/checked (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option) (/checked (Opzioni del compilatore C#).  
  
 **Ometti riferimenti a mscorlib.dll**  
 Specifica se nel programma sarà importato il file mscorlib.dll per l'intero spazio dei nomi <xref:System>. Selezionare questa casella se si vuole definire o creare lo spazio dei nomi <xref:System> e gli oggetti personalizzati. Per altre informazioni, vedere [/nostdlib (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).  
  
## <a name="output"></a>Output  
 Le opzioni seguenti consentono di specificare impostazioni di output avanzate.  
  
 **Informazioni di debug**  
 Specifica il tipo di informazioni di debug generate dal compilatore. Per informazioni su come configurare le prestazioni di debug di un'applicazione, vedere [Semplificazione del debug di un'immagine](http://msdn.microsoft.com/Library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Le opzioni di questa impostazione sono le seguenti:  
  
-   **none**  
  
     Specifica che non saranno generate informazioni di debug  
  
-   **full**  
  
     Consente di associare un debugger al programma in esecuzione.  
  
-   **pdbonly**  
  
     Consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma l'assembler viene visualizzato solo se il programma in esecuzione è associato al debugger.  
  
 Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
 **Allineamento file**  
 Specifica le dimensioni delle sezioni nel file di output. I valori validi sono **512**, **1024**, **2048**, **4096** e **8192**. Questi valori sono misurati in byte. Ogni sezione sarà allineata in base a un limite multiplo di questo valore, determinando così le dimensioni del file di output. Per altre informazioni, vedere [/filealign (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).  
  
 **Indirizzo di base DLL**  
 Specifica l'indirizzo di base preferenziale in cui caricare una DLL. L'indirizzo di base predefinito per una DLL viene impostato dal Common Language Runtime [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]. Per altre informazioni, vedere [/baseaddress (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).  
  
## <a name="see-also"></a>Vedere anche  
 [C# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)  (Opzioni del compilatore C#)  
 [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md)