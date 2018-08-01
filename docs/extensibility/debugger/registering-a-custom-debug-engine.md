---
title: 註冊自訂偵錯引擎 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c3203382b33184edf5618daecd9d3dc9102e2ca6
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251646"
---
# <a name="register-a-custom-debug-engine"></a>註冊自訂的偵錯引擎
偵錯引擎必須註冊為 class factory，下列 COM 慣例，以及註冊使用 Visual Studio 透過 Visual Studio 登錄子機碼。  
  
> [!NOTE]
>  您可以找到如何在 TextInterpreter 範例中，建置的註冊偵錯引擎的範例[教學課程： 建置偵錯引擎使用 ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)。  
  
## <a name="dll-server-process"></a>DLL 伺服器處理序  
 偵錯引擎是通常會設定它自己的 DLL 中做為 COM 伺服器。 因此，偵錯引擎必須向其 class factory 的 CLSID COM Visual Studio 才能存取它。 然後，偵錯引擎必須將自己登錄與建立任何內容 （也稱為度量） 的 Visual Studio 偵錯引擎支援。 計量寫入 Visual Studio 登錄子機碼的選擇取決於在偵錯引擎支援的功能。  
  
 [偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)告訴您，不只登錄位置需要註冊的偵錯引擎中; 它也會描述*dbgmetric.lib*程式庫，其中包含許多有用的函式和宣告適用於 c + + 開發人員，讓管理更容易登錄。  
  
### <a name="example"></a>範例  
 下列範例 （來自 TextInterpreter 範例） 示範如何使用`SetMetric`函式 (從*dbgmetric.lib*)，以向 Visual Studio 中的偵錯引擎。 中也會定義傳入的度量*dbgmetric.lib*。  
  
> [!NOTE]
>  TextInterpreter 是基本的偵錯引擎;它不會設定，並因此不會註冊 — 任何其他功能。 更完整的偵錯引擎會有一整份`SetMetric`呼叫或其對等項目，其中每項功能的偵錯引擎支援。  
  
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
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [教學課程： 建置使用 ATL COM 偵錯引擎](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)