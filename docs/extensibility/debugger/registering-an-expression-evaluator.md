---
title: "Registrazione di un analizzatore di espressioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], la valutazione di espressioni"
  - "analizzatori di espressioni, la registrazione"
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrazione di un analizzatore di espressioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'analizzatore di espressioni \(EE\) debba registrarsi in quanto una class factory con l'ambiente Windows COM e Visual Studio. Un EE viene implementato come DLL può essere inserito nello spazio degli indirizzi \(DE\) del motore di debug o lo spazio degli indirizzi di Visual Studio, a seconda di quale entità crea un'istanza di motore di esecuzione.  
  
## Analizzatore di espressioni di codice gestito  
 Un codice gestito EE viene implementato come una libreria di classi, ovvero una DLL che si registra con l'ambiente COM, in genere avviato da una chiamata al programma VSIP, **regpkg.exe**. L'effettivo processo di scrittura le chiavi del Registro di sistema per l'ambiente COM viene gestito automaticamente.  
  
 Un metodo della classe principale è contrassegnato con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, che indica che tale metodo viene chiamato quando la DLL è la registrazione con COM. Questo metodo di registrazione, spesso denominato `RegisterClass`, esegue l'attività di registrazione della DLL con Visual Studio. Un corrispondente `UnregisterClass` \(contrassegnati con il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>\), consente di annullare gli effetti di `RegisterClass` quando la DLL viene disinstallata.  
  
 Vengono apportate le stesse voci del Registro di sistema per un EE scritti in codice non gestito. l'unica differenza è che non vi è alcuna funzione di supporto, ad esempio `SetEEMetric` per svolgere il lavoro per l'utente. Un esempio di questo processo di registrazione\/annullamento della registrazione è simile al seguente:  
  
### Esempio  
 Questa funzione viene illustrato un codice gestito EE registra e Annulla la propria registrazione con Visual Studio.  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## Analizzatore di espressioni di codice non gestito  
 La DLL EE implementa il `DllRegisterServer` funzione di registrarsi con l'ambiente COM come Visual Studio.  
  
> [!NOTE]
>  Codice del Registro di sistema di esempio di codice MyCEE sono reperibili in dllentry.cpp il file, che si trova nell'installazione di VSIP in EnVSDK\\MyCPkgs\\MyCEE.  
  
### Processo Server DLL  
 Quando si registra l'analizzatore di Espressioni, il server DLL:  
  
1.  Registra la factory di classe `CLSID` in base alle convenzioni COM normale.  
  
2.  Chiama la funzione di supporto `SetEEMetric` per la registrazione con Visual Studio le metriche EE illustrate nella tabella seguente. La funzione `SetEEMetric` e le metriche specificate di seguito fanno parte della libreria dbgmetric.lib. Per informazioni dettagliate, vedere [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
    |Metrica|Descrizione|  
    |-------------|-----------------|  
    |`metricCLSID`|`CLSID` della factory EE \(classe\)|  
    |`metricName`|Nome del motore di esecuzione come una stringa visualizzabile|  
    |`metricLanguage`|Il nome del linguaggio che l'analizzatore di Espressioni è progettato per valutare|  
    |`metricEngine`|`GUID`s dei motori di debug \(DE\) che utilizzano questo EE|  
  
    > [!NOTE]
    >  Il `metricLanguage``GUID` identifica la lingua da nome, ma è il `guidLang` argomento `SetEEMetric` che consente di selezionare la lingua. Quando il compilatore genera il file di informazioni di debug, deve scrivere appropriati `guidLang` in modo che il DE sappia quale EE da utilizzare. Il DE richiede in genere il provider di simboli per la lingua `GUID`, cui è archiviata nel file di informazioni di debug.  
  
3.  Registra con Visual Studio mediante la creazione di chiavi in HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*y*, dove *y* è la versione di Visual Studio per registrarsi.  
  
### Esempio  
 Questa funzione viene illustrato un codice non gestito \(C\+\+\) EE registra e Annulla la propria registrazione con Visual Studio.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)