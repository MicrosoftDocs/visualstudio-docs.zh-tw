---
title: 註冊自定義調試引擎 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713216"
---
# <a name="register-a-custom-debug-engine"></a>註冊自訂除錯引擎
調試引擎必須按照 COM 約定註冊自己為類工廠,並透過 Visual Studio 註冊表子鍵向 Visual Studio 註冊。

> [!NOTE]
> 您可以在 TextInterpreter 範例中找到如何註冊除錯引擎的範例,該範例作為教學的一部分建[構 :使用 ATL COM 建構除錯引擎](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)。

## <a name="dll-server-process"></a>DLL 伺服器程序
 除錯引擎通常在其自己的 DLL 中設定為 COM 伺服器。 因此,除錯引擎必須在 Visual Studio 訪問之前將其類工廠的 CLSID 註冊到 COM。 然後,調試引擎必須向 Visual Studio 註冊自身,以建立調試引擎支援的任何屬性(也稱為指標)。 寫入 Visual Studio 註冊表子鍵的指標選擇取決於調試引擎支援的功能。

 [用於調試的 SDK 幫助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)不僅描述了註冊調試引擎所需的註冊表位置,還描述了調試引擎的註冊表位置。它還描述了*dbgmetric.lib*庫,該庫包含許多有用的函數和聲明,用於C++開發人員,使操作註冊表更容易。

### <a name="example"></a>範例
 以下範例(從 TextInterpreter 範例)簡`SetMetric`用如何使用函數(來自*dbgmetric.lib)* 向 Visual Studio 註冊調試引擎。 正在通過的指標也在*dbgmetric.lib*中定義。

> [!NOTE]
> 文本解釋器是一個基本的調試引擎;它不設置,因此不註冊任何其他功能。 更完整的調試引擎將具有一個完整的`SetMetric`調用清單或其等效項,每個功能都針對調試引擎支援。

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
- [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [除錯的 SDK 說明器](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [教學:使用 ATL COM 建構除錯引擎](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
