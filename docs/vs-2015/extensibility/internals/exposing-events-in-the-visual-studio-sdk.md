---
title: Visual Studio SDK 中公開事件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7056497c505bbb355287416e468e411b4e5a2a62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196695"
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>在 Visual Studio SDK 中公開事件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 可讓您使用自動化來源事件。 我們建議您來源專案和專案項目的事件。  
  
 從自動化取用者會擷取事件<xref:EnvDTE.DTEClass.Events%2A>物件或<xref:EnvDTE.DTEClass.GetObject%2A>(「 EventObjectName")。 環境呼叫`IDispatch::Invoke`利用`DISPATCH_METHOD`或`DISPATCH_PROPERTYGET`旗標，以傳回事件。  
  
 下列程序說明如何傳回 VSPackage 特定事件。  
  
1. 啟動環境時。  
  
2. 它會從登錄中讀取所有的 Vspackage，自動化、 AutomationEvents 和 AutomationProperties 索引鍵下的所有值名稱，並將資料表中的這些名稱。  
  
3. 在此範例中，自動化取用者呼叫`DTE.Events.AutomationProjectsEvents`或`DTE.Events.AutomationProjectItemsEvents`。  
  
4. 環境資料表中尋找的字串參數，並載入對應的 VSPackage。  
  
5. 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法所使用的名稱傳遞的呼叫中; 在此範例中，AutomationProjectsEvents 或 AutomationProjectItemsEvents。  
  
6. VSPackage 建立根物件，例如具有方法`get_AutomationProjectsEvents`和`get_AutomationProjectItemEvents`，然後傳回該物件的 IDispatch 指標。  
  
7. 環境呼叫適當的方法，以傳遞至自動化呼叫名稱為基礎。  
  
8. `get_`方法會建立另一個 IDispatch 為基礎的事件物件會實作`IConnectionPointContainer`介面和`IConnectionPoint`介面，並傳回 IDispatchpointer 物件。  
  
   若要使用自動化公開事件，您必須回應<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>和監看式新增至登錄的字串。 在基本專案範例中，字串會是"BscProjectsEvents 」 和 「 BscProjectItemsEvents"。  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>從基本的專案範例的登錄項目  
 本節說明如何將自動化事件值新增至登錄。  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]  
  
 「 AutomationProjectEvents"="傳回 AutomationProjectEvents 物件 」  
  
 「 AutomationProjectItemEvents"="傳回 AutomationProjectItemsEvents 物件 」  
  
|名稱|類型|Range|描述|  
|----------|----------|-----------|-----------------|  
|預設值 (@)|REG_SZ|未使用|未使用。 如需文件，您可以使用 [資料] 欄位。|  
|AutomationProjectsEvents|REG_SZ|事件物件的名稱。|索引鍵的名稱是相關項目。 如需文件，您可以使用 [資料] 欄位。<br /><br /> 此範例中，來自於基本的專案範例。|  
|AutomationProjectItemEvents|REG_SZ|事件物件的名稱|索引鍵的名稱是相關項目。 如需文件，您可以使用 [資料] 欄位。<br /><br /> 此範例中，來自於基本的專案範例。|  
  
 當事件物件的任何要求的自動化取用者時，建立具有 VSPackage 支援的任何事件的方法的根物件。 環境呼叫適當`get_`此物件上的方法。 例如，如果`DTE.Events.AutomationProjectsEvents`呼叫時，`get_AutomationProjectsEvents`叫用的根物件的方法。  
  
 ![Visual Studio 專案事件](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
事件的 automation 模型  
  
 此類別`CProjectEventsContainer`BscProjectsEvents，代表來源物件時`CProjectItemsEventsContainer`BscProjectItemsEvents 表示來源物件。  
  
 在大部分情況下，您必須傳回每個事件要求新的物件，因為大部分的事件物件採用篩選物件。 當引發事件時，請檢查此篩選條件來驗證呼叫的事件處理常式。  
  
 AutomationEvents.h 和 AutomationEvents.cpp 包含宣告和下表中的類別的實作。  
  
|類別|說明|  
|-----------|-----------------|  
|`CAutomationEvents`|實作事件的根物件，擷取自`DTE.Events`物件。|  
|`CProjectsEventsContainer` 和 `CProjectItemsEventsContainer`|實作會引發對應的事件的事件來源物件。|  
  
 下列程式碼範例示範如何回應事件物件的要求。  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 在上述程式碼`g_wszAutomationProjects`是您的專案集合 (「 FigProjects") 的名稱`g_wszAutomationProjectsEvents`(「 FigProjectsEvents") 和`g_wszAutomationProjectItemsEvents`("FigProjectItemEvents 」) 是專案事件的名稱和專案項目來自於的事件程式VSPackage 實作。  
  
 事件物件會從相同的中央位置，擷取`DTE.Events`物件。 如此一來，所有事件物件會都群組在一起，讓使用者不必瀏覽整個物件模型來尋找特定的事件。 這也可讓您提供您特定的 VSPackage 物件，而不需要您實作自己的全系統事件的程式碼。 不過，使用者，使用者必須尋找事件，以供您`ProjectItem`介面，不立即清除從那個 event 物件擷取所在。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK 範例](../../misc/vssdk-samples.md)
