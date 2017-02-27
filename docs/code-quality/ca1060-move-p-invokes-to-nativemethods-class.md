---
title: "CA1060: Spostare i P/Invoke nella classe NativeMethods | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1060: Spostare i P/Invoke nella classe NativeMethods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Categoria|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo utilizza Platform Invocation Services per accedere a codice non gestito e non è un membro di una delle classi **NativeMethods**.  
  
## Descrizione della regola  
 I metodi di chiamata al sistema operativo, ad esempio i metodi contrassegnati con l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> o quelli definiti mediante la parola chiave `Declare` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] accedono a codice non gestito.  Questi metodi devono essere contenuti in una delle classi riportate di seguito:  
  
-   **NativeMethods**: questa classe non elimina i percorsi stack per l'autorizzazione del codice non gestito. <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> non deve essere applicato a questa classe\). Questa classe è destinata ai metodi che possono essere utilizzati ovunque poiché verrà eseguito un percorso stack.  
  
-   **SafeNativeMethods**: questa classe elimina i percorsi stack per l'autorizzazione del codice non gestito. <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicato a questa classe\). Questa classe è destinata ai metodi che chiunque può chiamare in modo sicuro.  Ai chiamanti di questi metodi non viene richiesto di eseguire una revisione completa della sicurezza per assicurare che l'utilizzo sia sicuro poiché i metodi sono innocui per qualsiasi chiamante.  
  
-   **UnsafeNativeMethods**: questa classe elimina i percorsi stack per l'autorizzazione del codice non gestito. <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicato a questa classe\). Questa classe è destinata ai metodi potenzialmente pericolosi.  Qualsiasi chiamante di questi metodi deve eseguire una revisione completa della sicurezza per garantire che l'utilizzo sia sicuro poiché non verrà eseguito alcun percorso stack.  
  
 Queste classi sono dichiarate come `internal` \(`Friend` in Visual Basic\) e dichiarano un costruttore privato per impedire la creazione di nuove istanze.  I metodi di queste classi devono essere `static` e `internal` \(`Shared` e `Friend` in Visual Basic\).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, spostare il metodo nella classe **NativeMethods** appropriata.  Per la maggior parte delle applicazioni è sufficiente spostare i P\/Invoke in una nuova classe denominata **NativeMethods**.  
  
 Se tuttavia si stanno sviluppando librerie da utilizzare nelle altre applicazioni, è opportuno definire due altre classi chiamate **SafeNativeMethods** e **UnsafeNativeMethods**.  Queste classi assomigliano alla classe **NativeMethods**, tuttavia sono contrassegnate con un attributo speciale denominato **SuppressUnmanagedCodeSecurityAttribute**.  Quando questo attributo è applicato, il runtime non esegue un percorso stack completo per assicurarsi che tutti i chiamanti dispongano dell'autorizzazione **UnmanagedCode**.  Il runtime verifica solitamente questa autorizzazione all'avvio.  La mancata esecuzione di questo controllo migliora notevolmente le prestazioni di tutte le chiamate a questi metodi non gestiti, i quali possono venire chiamati anche dal codice con autorizzazioni limitate.  
  
 Tuttavia, è necessario utilizzare questo attributo con estrema attenzione.  Se erroneamente implementato, può compromettere gravemente la sicurezza.  
  
 Per informazioni sull'implementazione dei metodi, vedere gli esempi **NativeMethods**,  **SafeNativeMethods** e **UnsafeNativeMethods**.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene dichiarato un metodo che viola questa regola.  Per correggere la violazione, è necessario spostare i P\/Invoke **RemoveDirectory** in una classe appropriata progettata per contenere solo P\/Invoke.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## Esempio NativeMethods  
  
### Descrizione  
 Poiché la classe **NativeMethods** non deve essere contrassegnata con **SuppressUnmanagedCodeSecurityAttribute**, i P\/Invoke contenuti richiederanno l'autorizzazione **UnmanagedCode**.  Poiché la maggior parte delle applicazioni viene eseguita dal computer locale e con attendibilità, questo non è generalmente un problema.  Se tuttavia si stanno sviluppando librerie riutilizzabili, è opportuno definire una classe **SafeNativeMethods** o **UnsafeNativeMethods**.  
  
 Nell'esempio seguente viene illustrato un metodo **Interaction.Beep** che esegue il wrapping della funzione **MessageBeep** da user32.dll.  Il P\/Invoke **MessageBeep** viene inserito nella classe **NativeMethods**.  
  
### Codice  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## Esempio SafeNativeMethods  
  
### Descrizione  
 I metodi di P\/Invoke che possono essere esposti a una qualsiasi applicazione senza provocare effetti collaterali devono essere memorizzati in una classe denominata **SafeNativeMethods**.  Non è necessario richiedere autorizzazioni né conoscere da dove vengono chiamati.  
  
 Nell'esempio seguente viene illustrata una proprietà **Environment.TickCount** che esegue il wrapping della funzione **GetTickCount** da kernel32.dll.  
  
### Codice  
 [!CODE [FxCop.Design.NativeMethodsSafe#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe#1)]  
  
## Esempio UnsafeNativeMethods  
  
### Descrizione  
 I metodi P\/Invoke che è sconsigliabile chiamare e che potrebbero provocare effetti collaterali devono essere inseriti in una classe denominata **UnsafeNativeMethods**.  Questi metodi devono essere controllati rigorosamente per assicurarsi che non vengano esposti involontariamente all'utente.  La regola [CA2118: Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) può essere di aiuto in questo caso.  In alternativa, può essere opportuno richiedere a questi metodi un'altra autorizzazione anziché **UnmanagedCode** durante l'utilizzo.  
  
 Nell'esempio seguente viene illustrato un metodo **Cursor.Hide** che esegue il wrapping della funzione **ShowCursor** da user32.dll.  
  
### Codice  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## Vedere anche  
 [Avvisi di progettazione](../code-quality/design-warnings.md)