---
title: "CA2100: Controllare la vulnerabilit&#224; della sicurezza nelle query SQL | Microsoft Docs"
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
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100: Controllare la vulnerabilit&#224; della sicurezza nelle query SQL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|Category|Microsoft.Security|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo imposta la proprietà <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> utilizzando una stringa compilata da un argomento stringa nel metodo.  
  
## Descrizione della regola  
 La regola presuppone che l'argomento stringa contenga l'input dell'utente.  Una stringa di comando SQL compilata da un input dell'utente è vulnerabile agli attacchi intrusivi nel codice SQL,  nei quali un utente malintenzionato fornisce un input che modifica la progettazione di una query nel tentativo di danneggiare o di ottenere accesso non autorizzato al database sottostante.  Le tecniche tipiche includono l'intrusione di un apice o un apostrofo, che è delimitatore di stringa letterale di SQL, di due trattini, che indicano un commento SQL, e di un punto e virgola, che indica un nuovo comando a seguire.  Se l'input dell'utente deve essere parte della query, scegliere una delle soluzioni riportate di seguito ed elencate in ordine di efficacia per ridurre il rischio di attacco.  
  
-   Utilizzare una stored procedure.  
  
-   Utilizzare una stringa di comando con parametri.  
  
-   Convalidare l'input dell'utente sia per tipo che per contenuto prima di compilare la stringa di comando.  
  
 I seguenti tipi di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] implementano la proprietà <xref:System.Data.IDbCommand.CommandText%2A> o forniscono costruttori che la impostano mediante un argomento stringa.  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> e <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>.  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> e <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>.  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> e <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>.  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) e [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True).  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> e <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>.  
  
 Si noti che questa regola viene violata quando il metodo ToString di un tipo viene utilizzato in modo esplicito o implicito per costruire la stringa di query.  Di seguito è riportato un esempio.  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 La regola viene violata perché un utente malintenzionato può eseguire l'override del metodo ToString\(\).  
  
 La regola è violata anche quando viene utilizzato ToString in modo implicito.  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, utilizzare una query con parametri.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il testo del comando non contiene alcun input dell'utente.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati il metodo `UnsafeQuery` che viola la regola e il metodo `SaferQuery` che la soddisfa mediante l'utilizzo di una stringa di comando con parametri.  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## Vedere anche  
 [Cenni preliminari sulla sicurezza](../Topic/Security%20Overview2.md)