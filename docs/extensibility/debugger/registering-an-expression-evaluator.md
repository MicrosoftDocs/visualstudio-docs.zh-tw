---
title: 註冊運算式賦值器 |微軟文件
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
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713203"
---
# <a name="register-an-expression-evaluator"></a>註冊運算式賦值器
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 運算式賦值器 (EE) 必須將自己註冊為具有 Windows COM 環境和 Visual Studio 的類工廠。 EE 設定為 DLL,以便將其注入除錯引擎 (DE) 位址空間或 Visual Studio 位址空間,具體取決於實例化 EE 的實體。

## <a name="managed-code-expression-evaluator"></a>託管代碼表示式賦值器
 託管代碼 EE 作為類庫實現,它是一個 DLL,它向 COM 環境註冊自身,通常由對 VSIP 程式*regpkg.exe*的調用啟動。 自動處理為 COM 環境編寫註冊表項的實際過程。

 主類的方法用 標記<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, 指示在 DLL 向 COM 註冊時將呼叫該方法。 此註冊方法(通常稱為`RegisterClass`)執行在 Visual Studio 註冊 DLL 的任務。 相應的`UnregisterClass`(用<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>標記 ),撤銷卸載`RegisterClass`DLL 時的效果。
與使用非託管代碼編寫的 EE 相同的註冊表項;唯一的區別是沒有幫助器功能,例如`SetEEMetric`為你做工作。 下面是註冊和取消註冊過程的示例。

### <a name="example"></a>範例
 以下函數顯示了託管代碼 EE 如何在 Visual Studio 中註冊和註銷自身。

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

## <a name="unmanaged-code-expression-evaluator"></a>非託管代碼表示式賦值器
 EE DLL`DllRegisterServer`實現 在 COM 環境和可視化工作室中註冊自己的功能。

> [!NOTE]
> 您可以在檔*dllentry.cpp*中找到 MyCEE 代碼範例的註冊表代碼,該代碼位於 EnVSDK_MyCPkgs_MyCEE 下的 VSIP 安裝中。

### <a name="dll-server-process"></a>DLL 伺服器程序
 註冊 EE 時,DLL 伺服器:

1. 根據正常的`CLSID`COM 約定註冊其類工廠。

2. 調用說明器函數`SetEEMetric`向 Visual Studio 註冊下表中顯示的 EE 指標。 函數`SetEEMetric`和指標如下所示是*dbgmetric.lib*庫的一部分。 有關詳細資訊[,請參閱 SDK 協助器進行除錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。

    |計量|描述|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`EE 級工廠|
    |`metricName`|EE 的名稱為可顯示字串|
    |`metricLanguage`|EE 旨在評估的語言名稱|
    |`metricEngine`|`GUID`使用此 EE 的除錯引擎 (DE) 的|

    > [!NOTE]
    > 按`metricLanguage``GUID`名稱標識語言,但選擇該語言的參數`guidLang`是`SetEEMetric`該語言的參數。 當編譯器生成調試資訊檔時,它應該編寫適當的`guidLang`檔,以便 DE 知道要使用的 EE。 DE 通常會向符號提供程式詢問此`GUID`語言 ,該語言存儲在除錯資訊檔中。

3. 通過在HKEY_LOCAL_MACHINE_SOFTWARE_微軟_VisualStudio\\*X.Y*下創建密鑰來向 Visual Studio 註冊,其中*X.Y*是要註冊的 Visual Studio 版本。

### <a name="example"></a>範例
 以下函數顯示了非託管代碼 (C++) EE 如何在 Visual Studio 中註冊和登出自身。

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
- [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [除錯的 SDK 說明器](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
