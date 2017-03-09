---
title: "Progetto di esempio per la creazione di unit test | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "unit test (esempio) [Visual Studio]"
  - "unit test, esempi"
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Progetto di esempio per la creazione di unit test
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo codice di esempio viene fornito per le procedure dettagliate seguenti:  
  
-   [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  Questa procedura dettagliata descrive i passaggi per creare e personalizzare gli unit test, eseguirli ed esaminare i risultati dei test.  
  
-   [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/it-it/d4aab8e2-2140-4975-b4e3-41ef3fa944c8).  Questa procedura dettagliata illustra come visualizzare i dati di code coverage, che mostrano la percentuale di codice del progetto che si sta testando.  
  
-   [Procedura dettagliata: Uso dell'utilità di test della riga di comando](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md).  In questa procedura dettagliata è possibile usare l'utilità della riga di comando MSTest.exe per eseguire test e visualizzare i risultati.  
  
## Codice di esempio  
 L'unico errore intenzionale di questo esempio è che nel metodo Debit "m\_balance \+\= amount" dovrebbe esserci un segno meno e non più prima del segno di uguale.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 \/\* Ogni riferimento a società, organizzazioni, prodotti, nomi di dominio, indirizzi di posta elettronica, logo, persone, luoghi ed eventi è puramente casuale.  Nessuna associazione con nessuna società, organizzazione, prodotto, nome di dominio, indirizzo di posta elettronica, logo, persona, luogo o evento è intenzionale o può essere presupposta.  \*\/  
  
## Utilizzo del codice  
 Per usare questo codice, è necessario avere prima creato un progetto apposito in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Seguire i passaggi della sezione relativa alla preparazione per la procedura dettagliata in [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## Vedere anche  
 [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/it-it/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Procedura dettagliata: Uso dell'utilità di test della riga di comando](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md)