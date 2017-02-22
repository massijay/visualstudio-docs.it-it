---
title: "Utilizzo di Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mlearned"
manager: "douge"
---
# Utilizzo di Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento sono elencati i membri pubblici dello spazio dei nomi `Microsoft::VisualStudio::CppUnitTestFramework`.  
  
 I file di intestazione sono contenuti nella cartella di *VisualStudio2012\[x86\]InstallFolder***\\ VC \\ include \\ UnitTest**.  
  
 I file lib si trovano nella cartella di *VisualStudio2012\[x86\]InstallFolder***\\ VC \\ UnitTest \\ lib**.  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
-   [Creare le classi e i metodi di test](#BKMK_Create_test_classes_and_methods)  
  
-   [Inizializzazione e pulizia](#BKMK_Initialize_and_cleanup)  
  
    -   [Metodi di test](#BKMK_Test_methods)  
  
    -   [Classi di test](#BKMK_Test_classes)  
  
    -   [Moduli di test](#BKMK_Test_modules)  
  
-   [Creare attributi di test](#BKMK_Create_test_attributes)  
  
    -   [Attributi di test del metodo](#BKMK_Test_method_attributes)  
  
    -   [Attributi di classe di test](#BKMK_Test_class_attributes)  
  
    -   [Attributi del modulo di test](#BKMK_Test_module_attributes)  
  
    -   [Attributi predefiniti](#BKMK_Pre_defined_attributes)  
  
     [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
    -   [Asserzioni generali](#BKMK_General_Asserts)  
  
        -   [Sono uguali](#BKMK_General_Are_Equal)  
  
        -   [Non sono uguali](#BKMK_General_Are_Not_Equal)  
  
        -   [Sono lo stesso](#BKMK_General_Are_Same)  
  
        -   [Non sono lo stesso](#BKMK_General_Are_Not_Same)  
  
        -   [E' Null.](#BKMK_General_Is_Null)  
  
        -   [Non è Null](#BKMK_General_Is_Not_Null)  
  
        -   [E' true](#BKMK_General_Is_True)  
  
        -   [E' false.](#BKMK_General_Is_False)  
  
        -   [Fail](#BKMK_General_Fail)  
  
    -   [Asserzioni di Windows Runtime](#BKMK_WinRT_Asserts)  
  
        -   [Sono uguali](#BKMK_WinRT_Are_Equal)  
  
        -   [Sono lo stesso](#BKMK_WinRT_Are_Same)  
  
        -   [Non sono uguali](#BKMK_WinRT_Are_Not_Equal)  
  
        -   [Non sono lo stesso](#BKMK_WinRT_Are_Not_Same)  
  
        -   [E' Null.](#BKMK_WinRT_Is_Null)  
  
        -   [Non è Null](#BKMK_WinRT_Is_Not_Null)  
  
    -   [Asserzioni di eccezione](#BKMK_Exception_Asserts)  
  
        -   [Prevedere un'eccezione](#BKMK_Expect_Exception)  
  
         [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
        -   [Logger](#BKMK_Logger)  
  
        -   [Scrittura del messaggio](#BKMK_Write_Message)  
  
##  <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
###  <a name="BKMK_Create_test_classes_and_methods"></a> Creare le classi e i metodi di test  
  
```cpp  
TEST_CLASS(className)  
```  
  
 Richiesto per ogni classe che contiene metodi di test.  Identifica *className* come classe di test.  `TEST_CLASS` deve essere dichiarato nell'ambito dello spazio dei nomi.  
  
```cpp  
TEST_METHOD(methodName)   
{  
    // test method body  
}  
  
```  
  
 Definisce *methodName* come metodo di test.  `TEST_METHOD` deve essere dichiarato nella classe del metodo.  
  
###  <a name="BKMK_Initialize_and_cleanup"></a> Inizializzazione e pulizia  
  
####  <a name="BKMK_Test_methods"></a> Metodi di test  
  
```cpp  
TEST_METHOD_INITIALIZE(methodName)   
{  
    // method initialization code  
}  
  
```  
  
 Definisce *methodName* come metodo da eseguire prima che ogni metodo di test sia eseguito.  `TEST_METHOD_INITIALIZE` può essere definito una sola volta in una classe di test e deve essere definito nella classe di test.  
  
```cpp  
TEST_METHOD_CLEANUP(methodName)   
{  
    // test method cleanup  code  
}  
  
```  
  
 Definisce *methodName* come metodo che viene eseguito dopo l'esecuzione di ogni metodo di test.  `TEST_METHOD_CLEANUP` può essere definito una sola volta in una classe di test e deve essere definito nella classe di test.  
  
####  <a name="BKMK_Test_classes"></a> Classi di test  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Definisce *methodName* come metodo che viene eseguito dopo che ogni classe di test viene creata.  `TEST_CLASS_INITIALIZE` può essere definito una sola volta in una classe di test e deve essere definito nella classe di test.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Definisce *methodName* come metodo che viene eseguito dopo che ogni classe di test viene creata.  `TEST_CLASS_CLEANUP` può essere definito una sola volta in una classe di test e deve essere definito nella classe di test.  
  
####  <a name="BKMK_Test_modules"></a> Moduli di test  
  
```cpp  
TEST_MODULE_INITIALIZE(methodName)  
{  
    // module initialization code  
}  
```  
  
 Definisce il metodo *methodName* eseguito quando un modulo viene caricato.  `TEST_MODULE_INITIALIZE` può essere definito una sola volta in un modulo di test e deve essere dichiarato in ambito dello spazio dei nomi.  
  
```cpp  
TEST_MODULE_CLEANUP(methodName)  
```  
  
 Definisce il metodo *methodName* eseguito quando un modulo viene scaricato.  `TEST_MODULE_CLEANUP` può essere definito una sola volta in un modulo di test e deve essere dichiarato in ambito dello spazio dei nomi.  
  
###  <a name="BKMK_Create_test_attributes"></a> Creare attributi di test  
  
####  <a name="BKMK_Test_method_attributes"></a> Attributi di test del metodo  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Aggiunge gli attributi definiti con uno o più macro `TEST_METHOD_ATTRIBUTE` al metodo di test *testClassName*.  
  
 Una macro di `TEST_METHOD_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.  
  
####  <a name="BKMK_Test_class_attributes"></a> Attributi di classe di test  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Aggiunge gli attributi definiti con uno o più macro `TEST_CLASS_ATTRIBUTE` alla classe di test *testClassName*.  
  
 Una macro di `TEST_CLASS_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.  
  
####  <a name="BKMK_Test_module_attributes"></a> Attributi del modulo di test  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Aggiunge gli attributi definiti con uno o più macro `TEST_MODULE_ATTRIBUTE` al modulo di test *testModuleName*.  
  
 Una macro di `TEST_MODULE_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.  
  
####  <a name="BKMK_Pre_defined_attributes"></a> Attributi predefiniti  
 Queste macro di attributi predefiniti possono essere sostituite dalle macro `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE`, o `TEST_MODULE_ATTRIBUTE` descritto in precedenza.  
  
```cpp  
TEST_OWNER(ownerAlias)  
```  
  
 Definisce un attributo con il nome `Owner` e il valore di attributo *ownerAlias*.  
  
```cpp  
TEST_DESCRIPTION(description)  
```  
  
 Definisce un attributo con il nome `Description` e il valore di attributo *description*.  
  
```cpp  
TEST_PRIORITY(priority)  
```  
  
 Definisce un attributo con il nome `Priority` e il valore di attributo *priority*.  
  
```cpp  
TEST_WORKITEM(workitem)  
```  
  
 Definisce un attributo con il nome `WorkItem` e il valore di attributo *workItem*.  
  
```cpp  
TEST_IGNORE()  
```  
  
 Definisce un attributo con il nome `Ignore` e il valore di attributo `true`.  
  
##  <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
###  <a name="BKMK_General_Asserts"></a> Asserzioni generali  
  
####  <a name="BKMK_General_Are_Equal"></a> Sono uguali  
 Verifica che due oggetti sono uguali  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verifica che due double siano uguali  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verifica che due float siano uguali  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che due stringhe char\* siano uguali  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verifica che due stringhe di w\_char\* siano uguali  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Equal"></a> Non sono uguali  
 Verifica che due double non siano uguali  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verifica che due float non siano uguali  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verifica che due stringhe char\* non siano uguali  
  
```cpp  
static void AreNotEqual(  
    const char* notExpected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verifica che due stringhe di w\_char\* non siano uguali  
  
```cpp  
static void AreNotEqual(  
    const wchar_t* notExpected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verifica che due riferimenti non siano uguali in base all'operatore \=\=.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Same"></a> Sono lo stesso  
 Verifica che due riferimenti puntano alla stessa istanza di un oggetto \(identità\).  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Same"></a> Non sono lo stesso  
 Verifica che due riferimenti non si riferiscano alla stessa istanza di un oggetto \(identità\).  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Null"></a> E' Null.  
 Verifica che un puntatore sia NULL.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Not_Null"></a> Non è Null  
 Verifica che un puntatore non sia NULL  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_True"></a> E' true  
 Verifica che una condizione è true  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_False"></a> E' false.  
 Verifica che una condizione è false  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Fail"></a> Fail  
 Forza il risultato del test case a fallire  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
###  <a name="BKMK_WinRT_Asserts"></a> Asserzioni di Windows Runtime  
  
####  <a name="BKMK_WinRT_Are_Equal"></a> Sono uguali  
 Verifica che due puntatori di Windows Runtime siano uguali.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Verifica che due stringhe di Platform::String^ siano uguali.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Same"></a> Sono lo stesso  
 Verifica che due riferimenti di Windows Runtime fanno riferimento allo stesso oggetto.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Equal"></a> Non sono uguali  
 Verifica che due puntatori di Windows Runtime non siano uguali.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Verifica che due stringhe di Platform::String^ non siano uguali.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Same"></a> Non sono lo stesso  
 Verifica che due riferimenti di Windows Runtime non fanno riferimento allo stesso oggetto.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Null"></a> E' Null.  
 Verifica che un puntatore di Windows Runtime sia un nullptr.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Not_Null"></a> Non è Null  
 Verifica che un puntatore di Windows Runtime non sia un nullptr.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
###  <a name="BKMK_Exception_Asserts"></a> Asserzioni di eccezione  
  
####  <a name="BKMK_Expect_Exception"></a> Prevedere un'eccezione  
 Verifica che una funzione genera un'eccezione:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>   
static void ExpectException(  
    _FUNCTOR functor,   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo= NULL)  
```  
  
 Verifica che una funzione genera un'eccezione:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>   
    static void ExpectException(  
    _RETURNTYPE (*func)(),   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
##  <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
###  <a name="BKMK_Logger"></a> Logger  
 La classe logger contiene i metodi statici per scriverci  
  
```  
class Logger  
```  
  
###  <a name="BKMK_Write_Message"></a> Scrittura del messaggio  
  
```  
static void   
Logger::WriteMessage(const wchar_t* message)  
```  
  
```  
static void   
Logger::WriteMessage(const char* message)  
```  
  
## Esempio  
 Questo è un esempio di codice  
  
```  
////////////////////////////////////////////////////////////  
/* USAGE EXAMPLE  
// The following is an example of VSCppUnit usage.  
// It includes examples of attribute metadata, fixtures,  
// unit tests with assertions, and custom logging.  
  
#include <CppUnitTest.h>  
  
using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
  
BEGIN_TEST_MODULE_ATTRIBUTE()  
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")  
END_TEST_MODULE_ATTRIBUTE()  
  
TEST_MODULE_INITIALIZE(ModuleInitialize)  
{  
    Logger::WriteMessage("In Module Initialize");  
}  
  
TEST_MODULE_CLEANUP(ModuleCleanup)  
{  
    Logger::WriteMessage("In Module Cleanup");  
}  
  
TEST_CLASS(Class1)  
{  
  
public:  
  
    Class1()  
    {  
        Logger::WriteMessage("In Class1");  
    }  
  
    ~Class1()  
    {  
        Logger::WriteMessage("In ~Class1");  
    }  
  
    TEST_CLASS_INITIALIZE(ClassInitialize)  
    {  
        Logger::WriteMessage("In Class Initialize");  
    }  
  
    TEST_CLASS_CLEANUP(ClassCleanup)  
    {  
        Logger::WriteMessage("In Class Cleanup");  
    }  
  
    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
        TEST_OWNER(L"OwnerName")  
        TEST_PRIORITY(1)  
    END_TEST_METHOD_ATTRIBUTE()  
  
    TEST_METHOD(Method1)  
    {     
        Logger::WriteMessage("In Method1");  
        Assert::AreEqual(0, 0);  
    }  
  
    TEST_METHOD(Method2)  
    {  
        Assert::Fail(L"Fail");  
    }  
};  
```  
  
## Vedere anche  
 [Eseguire unit test del codice](../test/unit-test-your-code.md)   
 [Unit testing native code with Test Explorer](http://msdn.microsoft.com/it-it/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Aggiunta di unit test alle applicazioni C\+\+ esistenti](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)