---
title: 登錄的自訂偵錯引擎 |Microsoft 文件
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
ms.openlocfilehash: 99ff41f116e569baaae312acd17408928a6c79f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126284"
---
# <a name="registering-a-custom-debug-engine"></a>註冊的自訂偵錯引擎
偵錯引擎必須註冊為 class factory 遵循 COM 慣例，以及透過 Visual Studio 登錄子機碼來註冊使用 Visual Studio。  
  
> [!NOTE]
>  如何註冊偵錯引擎的範例，請參閱 TextInterpreter 範例中，建立成一部分[教學課程： 建立偵錯引擎使用 ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)。  
  
## <a name="dll-server-process"></a>DLL 伺服器處理序  
 一般而言，偵錯引擎會在它自己的 DLL 中實作為 COM 伺服器。 這表示，偵錯引擎必須登錄至其 class factory 的 CLSID COM Visual Studio 才能存取它。 然後偵錯引擎必須向 Visual Studio 本身才能建立任何內容 （否則稱為度量） 偵錯引擎支援。 Visual Studio 登錄子機碼的偵錯引擎寫入度量的選擇取決於偵錯引擎支援的功能。  
  
 [SDK 進行偵錯的協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)描述不僅的登錄位置需要註冊偵錯引擎; 它也會描述 dbgmetric.lib 程式庫，其中包含許多有用的函式和 c + + 開發人員，讓宣告管理更容易登錄。  
  
### <a name="example"></a>範例  
 以下是典型的範例 （來自 TextInterpreter 範例） 示範如何使用`SetMetric`函式 （從 dbgmetric.lib)，以註冊使用 Visual Studio 偵錯引擎。 傳入的度量也定義在 dbgmetric.lib。  
  
> [!NOTE]
>  TextInterpreter 是基本的偵錯引擎。未實作，並因此不會註冊 — 任何其他功能。 更完整的偵錯引擎會有整個清單`SetMetric`呼叫或其對等項目，其中每項功能的偵錯引擎支援。  
  
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
 [SDK 進行偵錯的協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [教學課程： 建立使用 ATL COM 偵錯引擎](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)