---
title: 註冊運算式評估工具 |Microsoft Docs
description: 瞭解運算式評估工具必須將本身註冊為具有 Windows COM 環境和 Visual Studio 的 class factory。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f26eddf7191ee4393dd2ca986fe7a1d2c3af9e2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847139"
---
# <a name="register-an-expression-evaluator"></a>註冊運算式評估工具
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 運算式評估工具 (EE) 必須將本身註冊為具有 Windows COM 環境和 Visual Studio 的 class factory。 EE 會設定為 DLL，以便將它插入 debug engine (DE) 位址空間或 Visual Studio 位址空間，視哪一個實體具現化 EE 而定。

## <a name="managed-code-expression-evaluator"></a>Managed 程式碼運算式評估工具
 Managed 程式碼 EE 會實作為類別庫，此程式庫是向 COM 環境註冊本身的 DLL，通常是透過呼叫 VSIP 程式來啟動， *regpkg.exe*。 系統會自動處理為 COM 環境寫入登錄機碼的實際程式。

 主要類別的方法會標示為 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> ，表示在使用 COM 註冊 DLL 時，會呼叫方法。 此註冊方法（通常稱為 `RegisterClass` ）會執行使用 Visual Studio 註冊 DLL 的工作。 `UnregisterClass`以) 標記的對應 (<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ， `RegisterClass` 會在卸載 DLL 時復原效果。
針對以非受控碼撰寫的 EE 建立相同的登錄專案;唯一的差別在於沒有協助程式功能，例如 `SetEEMetric` 為您執行工作。 以下是註冊和取消註冊程式的範例。

### <a name="example"></a>範例
 下列函式顯示 managed 程式碼 EE 如何向 Visual Studio 登錄和取消註冊本身。

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

## <a name="unmanaged-code-expression-evaluator"></a>非受控碼運算式評估工具
 EE DLL 會實 `DllRegisterServer` 作用來向 COM 環境註冊本身以及 Visual Studio 的函式。

> [!NOTE]
> 您可以在 dllentry 檔案中找到 MyCEE 程式碼範例登錄程式碼，該檔案位於 EnVSDK\MyCPkgs\MyCEE. 下的 VSIP 安裝中 *。*

### <a name="dll-server-process"></a>DLL 伺服器進程
 註冊 EE 時，DLL 伺服器：

1. `CLSID`依據一般 COM 慣例來註冊其 class factory。

2. 呼叫 helper 函式 `SetEEMetric` ，以 Visual Studio 下表所示的 EE 計量來進行註冊。 以下列方式指定的函式 `SetEEMetric` 和度量是 *dbgmetric .lib* 程式庫的一部分。 如需詳細資料，請參閱 [SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 。

    |計量|描述|
    |------------|-----------------|
    |`metricCLSID`|`CLSID` EE class factory|
    |`metricName`|EE 的名稱，做為可顯示的字串|
    |`metricLanguage`|EE 設計用來評估的語言名稱|
    |`metricEngine`|`GUID`偵錯工具引擎 (使用此 EE 來解除) |

    > [!NOTE]
    > `metricLanguage``GUID`會依名稱識別語言，但它是 `guidLang` 選取語言的引數 `SetEEMetric` 。 當編譯器產生 debug 資訊檔案時，它應該撰寫適當的， `guidLang` 讓 DE 知道要使用哪一個 EE。 這種方式通常會要求此語言的符號提供者 `GUID` 會儲存在 debug 資訊檔中。

3. 藉由在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudioX-y 下建立索引鍵來註冊 Visual Studio \\ **，其中， *x. y* 是要註冊的 Visual Studio 版本。

### <a name="example"></a>範例
 下列函式顯示非受控碼 (c + +) EE 如何向 Visual Studio 註冊及取消註冊本身。

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
- [用於偵錯工具的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
