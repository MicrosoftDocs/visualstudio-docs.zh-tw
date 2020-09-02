---
title: 註冊自訂的 Debug Engine |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703595"
---
# <a name="registering-a-custom-debug-engine"></a>註冊自訂的偵錯引擎
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debug engine 必須將本身註冊為遵循 COM 慣例的 class factory，並透過 Visual Studio 登錄子機碼向 Visual Studio 註冊。  
  
> [!NOTE]
> 如需如何註冊 debug engine 的範例，請參閱 TextInterpreter 範例，該範例是在教學課程中建立的，它是教學課程的一部分 [：使用 ATL COM 來建立 Debug engine](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)。  
  
## <a name="dll-server-process"></a>DLL 伺服器進程  
 一般而言，debug engine 會在其本身的 DLL 中實作為 COM 伺服器。 這表示在 Visual Studio 可以存取之前，debug engine 必須先向 COM 註冊其 class factory 的 CLSID。 然後，debug engine 必須自行向 Visual Studio 本身登錄，才能建立任何屬性 (亦稱為「偵測引擎」支援) 的度量。 針對偵錯工具引擎寫入 Visual Studio 登錄子機碼的度量選擇取決於 debug engine 支援的功能。  
  
 [用於偵錯工具的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 不只描述註冊 debug engine 所需的登錄位置。它也會描述 dbgmetric .lib 程式庫，其中包含許多有用的函式和宣告，可讓 c + + 開發人員更輕鬆地操作登錄。  
  
### <a name="example"></a>範例  
 以下是從 TextInterpreter 範例 (的典型範例，) 示範如何使用 `SetMetric` (自 dbgmetric 的函式) ，以 Visual Studio 註冊偵錯工具引擎。 傳遞的度量也會在 dbgmetric 中定義。  
  
> [!NOTE]
> TextInterpreter 是基本的 debug 引擎;它不會執行任何其他功能，因此不會進行註冊。 更完整的 debug 引擎會有一個完整的 `SetMetric` 呼叫清單或其對等專案，而每項功能都有一個針對 debug engine 支援的功能。  
  
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
 [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [用於偵錯工具的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [教學課程：使用 ATL COM 建立 Debug Engine](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
