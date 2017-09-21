---
title: "註冊的運算式評估工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，運算式評估"
  - "運算式評估工具註冊"
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 註冊的運算式評估工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 運算式評估工具 \(EE\) 必須本身登錄為使用 Windows COM 環境和 Visual Studio 的 class factory。 因此，它可能會插入至偵錯引擎 \(DE\) 位址空間或 Visual Studio 的位址空間，取決於哪些實體會具現化 EE EE 被實作為 DLL。  
  
## Managed 程式碼運算式評估工具  
 Managed 程式碼 EE 實作為類別庫，也就是向 COM 環境，通常是透過呼叫 VSIP 計畫，來啟動 DLL **regpkg.exe**。 撰寫 COM 環境的登錄機碼的實際程序會自動處理。  
  
 主要類別的方法會標示 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, ，表示正在註冊 com DLL 時要呼叫該方法 此註冊方法中，通常稱為 `RegisterClass`, ，執行使用 Visual Studio 登錄 DLL 的工作。 對應 `UnregisterClass` \(標記為 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>\)，復原的效果 `RegisterClass` DLL 會解除安裝。  
  
 與 unmanaged 程式碼，以撰寫 EE 進行相同的登錄項目唯一的差別，沒有 helper 函式如 `SetEEMetric` 來為您執行的工作。 這個註冊\/取消註冊程序的範例看起來像這樣︰  
  
### 範例  
 此函式會顯示 managed 程式碼 EE 如何註冊和使用 Visual Studio 自動取消登錄。  
  
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
  
## Unmanaged 程式碼運算式評估工具  
 EE DLL 實作 `DllRegisterServer` COM 環境，以及 Visual Studio 登錄它自己的函式。  
  
> [!NOTE]
>  MyCEE 程式碼範例登錄機碼位於檔案 dllentry.cpp，其位於 EnVSDK\\MyCPkgs\\MyCEE VSIP 安裝中。  
  
### DLL 伺服器處理序  
 當登錄 EE，DLL 伺服器︰  
  
1.  註冊其類別站 `CLSID` 根據一般的 COM 慣例。  
  
2.  呼叫 helper 函式 `SetEEMetric` 註冊使用 Visual Studio 在下表所示的 EE 度量。 函式 `SetEEMetric` 和下面指定的度量是 dbgmetric.lib 程式庫的一部分。 如需詳細資訊，請參閱[SDK 協助程式進行偵錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。  
  
    |度量|描述|  
    |--------|--------|  
    |`metricCLSID`|`CLSID` EE class factory|  
    |`metricName`|可顯示的字串為 EE 的名稱|  
    |`metricLanguage`|評估旨在 EE 是語言的名稱|  
    |`metricEngine`|`GUID`偵錯引擎 \(DE\) 可搭配此 EE 的 s|  
  
    > [!NOTE]
    >  `metricLanguage` `GUID` 識別語言的名稱，但它是 `guidLang` 引數 `SetEEMetric` 所選取語言。 當編譯器產生偵錯資訊檔案時，它應該寫入適當 `guidLang` ，讓 DE 知道要使用哪個 EE。 通常此語言的要求的符號提供者的 DE `GUID`, ，其儲存在偵錯資訊檔案。  
  
3.  註冊使用 Visual Studio 建立機碼 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, ，其中 *X.Y* 是向 Visual Studio 的版本。  
  
### 範例  
 Unmanaged 程式碼 （c \+ \+） EE 如何註冊和自動取消登錄與 Visual Studio 會顯示這個函式。  
  
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
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [SDK 協助程式進行偵錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)