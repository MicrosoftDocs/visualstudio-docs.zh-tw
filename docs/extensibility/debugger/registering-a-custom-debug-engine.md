---
title: 註冊自訂的 Debug Engine |Microsoft Docs
description: 瞭解 debug engine 如何將本身註冊為 class factory、遵循 COM 慣例，以及透過登錄註冊 Visual Studio。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 04e4e8de875cb66ed285e610950baa1c5bf4ef3f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070657"
---
# <a name="register-a-custom-debug-engine"></a>註冊自訂的調試引擎
Debug engine 必須將本身註冊為 class factory，並遵循 COM 慣例，並透過 Visual Studio 登錄子機碼向 Visual Studio 註冊。

> [!NOTE]
> 您可以在 TextInterpreter 範例中找到如何註冊 debug 引擎的範例，此範例是在教學課程中建立的，它是教學課程的一部分 [：使用 ATL COM 建立 debug engine](/previous-versions/bb147024(v=vs.90))。

## <a name="dll-server-process"></a>DLL 伺服器進程
 Debug 引擎通常會在其本身的 DLL 中設定為 COM 伺服器。 因此，在 Visual Studio 可以存取之前，debug engine 必須先向 COM 註冊其 class factory 的 CLSID。 然後，debug engine 必須向 Visual Studio 註冊本身，才能建立任何屬性 (亦稱為「偵測引擎」支援) 的度量。 寫入 Visual Studio 登錄子機碼的度量選擇取決於 debug engine 支援的功能。

 [用於偵錯工具的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 不只描述註冊 debug engine 所需的登錄位置。它也會描述 *dbgmetric .lib* 程式庫，其中包含許多有用的函式和宣告，可讓 c + + 開發人員更輕鬆地操作登錄。

### <a name="example"></a>範例
 下列範例 (從 TextInterpreter 範例中) 示範如何 (使用 dbgmetric 的函式 `SetMetric`)  ，以 Visual Studio 註冊 debug engine。 傳遞的度量也會在 *dbgmetric* 中定義。

> [!NOTE]
> TextInterpreter 是基本的 debug 引擎;它不會設定（因此不會註冊）任何其他功能。 更完整的 debug 引擎會有一個完整的 `SetMetric` 呼叫清單或其對等專案，而每項功能都有一個針對 debug engine 支援的功能。

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>另請參閱
- [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [用於偵錯工具的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [教學課程：使用 ATL COM 建立 debug engine](/previous-versions/bb147024(v=vs.90))