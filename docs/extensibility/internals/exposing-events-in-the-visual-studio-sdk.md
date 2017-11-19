---
title: "公開事件，在 Visual Studio SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7b392ac841a50d835186e79a383e404e7fba190
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>公開 Visual Studio SDK 中的事件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可讓您使用自動化來源的事件。 我們建議您來源專案和專案項目的事件。  
  
 從自動化取用者會擷取事件<xref:EnvDTE.DTEClass.Events%2A>物件或<xref:EnvDTE.DTEClass.GetObject%2A>(「 EventObjectName")。 環境呼叫`IDispatch::Invoke`使用`DISPATCH_METHOD`或`DISPATCH_PROPERTYGET`旗標，以傳回事件。  
  
 下列程序說明如何傳回 VSPackage 特定事件。  
  
1.  啟動環境。  
  
2.  它從登錄中讀取所有的值名稱之下的所有 Vspackage，自動化、 AutomationEvents 和 AutomationProperties 索引鍵，並將資料表中的那些名稱。  
  
3.  在此範例中，為自動化取用者呼叫`DTE.Events.AutomationProjectsEvents`或`DTE.Events.AutomationProjectItemsEvents`。  
  
4.  環境在資料表中尋找的字串參數，並載入對應的 VSPackage。  
  
5.  環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法使用的名稱傳遞的呼叫中; 在此範例中，AutomationProjectsEvents 或 AutomationProjectItemsEvents。  
  
6.  VSPackage 會建立根物件，例如具有方法`get_AutomationProjectsEvents`和`get_AutomationProjectItemEvents`，然後傳回該物件的 IDispatch 指標。  
  
7.  環境呼叫適當的方法根據傳遞至自動化呼叫的名稱。  
  
8.  `get_`方法會建立另一個同時實作的 IDispatch 為基礎的事件物件`IConnectionPointContainer`介面和`IConnectionPoint`介面，並傳回 IDispatchpointer 物件。  
  
 若要使用 automation 公開事件，您必須回應<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>和監看式新增到登錄的字串。 在基本專案範例中，字串會是"BscProjectsEvents"和"BscProjectItemsEvents"。  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>從基本的專案範例的登錄項目  
 本節說明如何新增至登錄的 automation 事件值。  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 「 AutomationProjectEvents"="傳回 AutomationProjectEvents 物件 」  
  
 「 AutomationProjectItemEvents"="傳回 AutomationProjectItemsEvents 物件 」  
  
|名稱|類型|範圍|說明|  
|----------|----------|-----------|-----------------|  
|預設值 (@)|REG_SZ|未使用|未使用。 如需文件，您可以使用的資料欄位。|  
|AutomationProjectsEvents|REG_SZ|事件物件的名稱。|索引鍵的名稱會相關。 如需文件，您可以使用的資料欄位。<br /><br /> 這個範例來自基本專案範例。|  
|AutomationProjectItemEvents|REG_SZ|事件物件的名稱|索引鍵的名稱會相關。 如需文件，您可以使用的資料欄位。<br /><br /> 這個範例來自基本專案範例。|  
  
 當任何事件物件會要求自動化取用者時，建立具有 VSPackage 支援的任何事件的方法的根物件。 環境呼叫適當`get_`此物件上的方法。 例如，如果`DTE.Events.AutomationProjectsEvents`呼叫時，`get_AutomationProjectsEvents`根物件上的方法會叫用。  
  
 ![Visual Studio 專案事件](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
事件的 automation 模型  
  
 類別`CProjectEventsContainer`BscProjectsEvents，表示來源物件時`CProjectItemsEventsContainer`BscProjectItemsEvents 代表來源物件。  
  
 在大部分情況下，您必須傳回每個事件要求新的物件，因為大部分的事件物件的篩選物件。 當引發事件時，會檢查此篩選條件，驗證正在呼叫事件處理常式。  
  
 AutomationEvents.h 和 AutomationEvents.cpp 包含宣告和實作下表中的類別。  
  
|類別|說明|  
|-----------|-----------------|  
|`CAutomationEvents`|實作事件根物件，擷取自`DTE.Events`物件。|  
|`CProjectsEventsContainer` 和 `CProjectItemsEventsContainer`|實作會引發對應的事件的事件來源物件。|  
  
 下列程式碼範例示範如何在事件物件的要求回應。  
  
```cpp  
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
  
 在上述程式碼中`g_wszAutomationProjects`是您的專案集合 (「 FigProjects") 的名稱`g_wszAutomationProjectsEvents`(「 FigProjectsEvents") 和`g_wszAutomationProjectItemsEvents`(「 FigProjectItemEvents 」) 是專案事件的名稱和專案項目來自於事件您VSPackage 實作。  
  
 事件物件會從相同的中央位置，擷取`DTE.Events`物件。 如此一來，所有事件物件會都群組在一起，讓使用者不必瀏覽整個物件模型來尋找特定的事件。 這也可讓您提供您特定的 VSPackage 物件，而不需要您實作您自己的全系統事件的程式碼。 不過，一般使用者，使用者必須尋找事件，以供您`ProjectItem`介面，不立即清除該事件物件擷取的位置。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK 範例](http://aka.ms/vs2015sdksamples)