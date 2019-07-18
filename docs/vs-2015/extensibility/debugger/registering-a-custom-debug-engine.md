---
title: 註冊自訂偵錯引擎 |Microsoft Docs
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703595"
---
# <a name="registering-a-custom-debug-engine"></a>註冊自訂的偵錯引擎
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯引擎必須註冊為遵循 COM 慣例的 class factory，以及註冊使用 Visual Studio 透過 Visual Studio 登錄子機碼。  
  
> [!NOTE]
> 如何註冊偵錯引擎的範例可在 TextInterpreter 範例中，建立成一部分[教學課程：建置偵錯引擎使用 ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)。  
  
## <a name="dll-server-process"></a>DLL 伺服器處理序  
 一般而言，偵錯引擎會在它自己的 DLL 中實作為 COM 伺服器。 這表示，Visual Studio 才能存取它，偵錯引擎必須註冊 com 其 class factory 的 CLSID。 然後偵錯引擎必須向 Visual Studio 本身才能建立任何屬性 （也稱為度量） 偵錯引擎支援。 計量會寫入至偵錯引擎的 Visual Studio 登錄子機碼的選擇取決於在偵錯引擎支援的功能。  
  
 [偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)描述不只登錄位置需要註冊的偵錯引擎中; 它也會描述 dbgmetric.lib 程式庫，其中包含許多有用的函式和宣告C++，讓開發人員管理登錄更容易。  
  
### <a name="example"></a>範例  
 以下是典型的範例 （來自 TextInterpreter 範例） 示範如何使用`SetMetric`函式 （從 dbgmetric.lib)，以向 Visual Studio 中的偵錯引擎。 Dbgmetric.lib 中，也會定義傳入的度量。  
  
> [!NOTE]
> TextInterpreter 是基本的偵錯引擎;它不會實作，並因此不會註冊 — 任何其他功能。 更完整的偵錯引擎會有一整份`SetMetric`呼叫或其對等項目，其中每項功能的偵錯引擎支援。  
  
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
 [教學課程：建置使用 ATL COM 偵錯引擎](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
