---
title: 註冊運算式評估工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2b30a3b1ee02a6ac64c66aa7d80a35dc45a683a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715306"
---
# <a name="register-an-expression-evaluator"></a>註冊運算式評估工具
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 運算式評估工具 (EE) 必須將自己做為使用 Windows COM 環境和 Visual Studio 的 class factory 登錄。 EE 會設為 DLL，因此它會將其插入偵錯引擎 (DE) 位址空間或 Visual Studio 的位址空間，視實體會具現化 EE。

## <a name="managed-code-expression-evaluator"></a>Managed 程式碼運算式評估工具
 EE 會實作為類別庫，也就是向 COM 環境中，啟動一般 VSIP 計畫中，呼叫 DLL 的 managed 程式碼*regpkg.exe*。 撰寫 COM 環境的登錄機碼的實際程序會自動處理。

 主要類別的方法會標示<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>，指出正在使用 COM 註冊 DLL 時要呼叫的方法 此註冊方法，通常稱為`RegisterClass`，執行使用 Visual Studio 註冊 DLL 的工作。 相對應`UnregisterClass`(以標記<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>)，復原的效果`RegisterClass`當解除安裝此 DLL。
與 unmanaged 程式碼，以撰寫 EE 做相同的登錄項目唯一的差別是，沒有任何協助程式函式例如`SetEEMetric`來為您執行工作。 以下是註冊和取消註冊程序的範例。

### <a name="example"></a>範例
 下列函式會示範如何註冊 EE 的 managed 程式碼，並使用 Visual Studio 自動取消登錄。

```csharp
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

## <a name="unmanaged-code-expression-evaluator"></a>Unmanaged 程式碼運算式評估工具
 EE DLL 實作`DllRegisterServer`向 COM 環境，以及 Visual Studio 的函式。

> [!NOTE]
>  您可以在檔案中找到 MyCEE 程式碼範例登錄機碼*dllentry.cpp*，位於 EnVSDK\MyCPkgs\MyCEE 在 VSIP 安裝。

### <a name="dll-server-process"></a>DLL 伺服器處理序
 當註冊 EE，DLL 伺服器：

1.  其 class factory 註冊`CLSID`根據一般的 COM 慣例。

2.  呼叫 helper 函式`SetEEMetric`向 Visual Studio 下表所示的 EE 度量。 此函式`SetEEMetric`和指定，如下所示的計量是的一部分*dbgmetric.lib*程式庫。 請參閱[進行偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)如需詳細資訊。

    |度量|描述|
    |------------|-----------------|
    |`metricCLSID`|`CLSID` EE class factory 的|
    |`metricName`|可顯示的字串形式 EE 的名稱|
    |`metricLanguage`|評估旨在 EE 的語言名稱|
    |`metricEngine`|`GUID`s 的偵錯引擎 (DE) 可搭配此 EE|

    > [!NOTE]
    >  `metricLanguage``GUID`識別的語言名稱，但它是`guidLang`引數`SetEEMetric`選取語言。 當編譯器產生偵錯資訊檔案時，它應該寫入適當`guidLang`，讓裝置知道要使用哪一個 EE。 DE 通常會符號提供者要求此語言`GUID`，儲存在偵錯資訊檔案。

3.  藉由建立 hkey_local_machine\software\microsoft\visualstudio \ 底下的機碼會向 Visual Studio\\*X.Y*，其中*X.Y*是向 Visual Studio 的版本。

### <a name="example"></a>範例
 下列函式會顯示未受管理的程式碼 （c + +） EE 如何註冊，並使用 Visual Studio 自動取消登錄。

```cpp
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

## <a name="see-also"></a>另請參閱
- [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
