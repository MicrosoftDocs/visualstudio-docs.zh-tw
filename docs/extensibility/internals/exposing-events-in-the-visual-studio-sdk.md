---
title: 公開 Visual Studio SDK 中的事件 |Microsoft Docs
description: 瞭解公開專案和專案專案事件的 Visual Studio SDK 方法和登錄專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00dd13898204fe322ec0ddd33db10e7ca19db167
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946640"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>在 Visual Studio SDK 中公開事件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可讓您使用自動化來來源事件。 建議您輸入專案和專案專案的來源事件。

 自動化取用者會從 <xref:EnvDTE.DTEClass.Events%2A> 物件或 (抓取事件 <xref:EnvDTE.DTEClass.GetObject%2A> ，例如 `GetObject("EventObjectName")`) 。 `IDispatch::Invoke`使用 `DISPATCH_METHOD` 或 `DISPATCH_PROPERTYGET` 旗標來傳回事件的環境會呼叫。

 下列程式說明如何傳回 VSPackage 特定事件。

1. 環境隨即啟動。

2. 它會從登錄讀取所有 Vspackage 之 **Automation**、 **AutomationEvents** 和 **AutomationProperties** 索引鍵下的所有值名稱，並將這些名稱儲存在資料表中。

3. 自動化取用者會呼叫，在此範例中為 `DTE.Events.AutomationProjectsEvents` 或 `DTE.Events.AutomationProjectItemsEvents` 。

4. 環境會尋找資料表中的字串參數，並載入對應的 VSPackage。

5. 環境會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 使用在呼叫中傳遞的名稱來呼叫方法，在此範例中為 `AutomationProjectsEvents` 或 `AutomationProjectItemsEvents` 。

6. VSPackage 會建立具有例如和等方法的根物件 `get_AutomationProjectsEvents` ， `get_AutomationProjectItemEvents` 然後傳回物件的 IDispatch 指標。

7. 環境會根據傳遞給 automation 呼叫的名稱來呼叫適當的方法。

8. `get_`方法會建立另一個 IDispatch 型事件物件，此物件會同時 `IConnectionPointContainer` 執行介面和 `IConnectionPoint` 介面，並將傳 `IDispatchpointer` 回到物件。

   若要使用 automation 來公開事件，您必須回應 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 並監看您新增到登錄的字串。 在基本專案範例中，字串是 *BscProjectsEvents* 和 *BscProjectItemsEvents*。

## <a name="registry-entries-from-the-basic-project-sample"></a>基本專案範例中的登錄專案
 本節說明如何將 automation 事件值新增至登錄。

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = 傳回 `AutomationProjectEvents` 物件。

 **AutomationProjectItemEvents** = 傳回 `AutomationProjectItemsEvents` 物件。

|名稱|類型|範圍|Description|
|----------|----------|-----------|-----------------|
|預設 ( @ ) |REG_SZ|未使用|未使用的。 您可以使用資料欄位來取得檔。|
|*AutomationProjectsEvents*|REG_SZ|事件物件的名稱。|只有索引鍵名稱是相關的。 您可以使用資料欄位來取得檔。<br /><br /> 此範例來自基本專案範例。|
|*AutomationProjectItemEvents*|REG_SZ|事件物件的名稱|只有索引鍵名稱是相關的。 您可以使用資料欄位來取得檔。<br /><br /> 此範例來自基本專案範例。|

 當 automation 取用者要求任何事件物件時，請建立根物件，該物件具有 VSPackage 所支援之任何事件的方法。 環境會 `get_` 在此物件上呼叫適當的方法。 例如，如果 `DTE.Events.AutomationProjectsEvents` 呼叫，則會叫用 `get_AutomationProjectsEvents` 根物件上的方法。

 ![Visual Studio 專案事件](../../extensibility/internals/media/projectevents.gif "ProjectEvents") 事件的 Automation 模型

 類別 `CProjectEventsContainer` 代表 *BscProjectsEvents* 的來源物件，並 `CProjectItemsEventsContainer` 代表 *BscProjectItemsEvents* 的來源物件。

 在大部分的情況下，您必須針對每個事件要求傳回新的物件，因為大部分的事件物件都採用篩選物件。 當您引發事件時，請檢查此篩選準則來確認正在呼叫事件處理常式。

 *AutomationEvents .h* 和 *AutomationEvents* 包含下表中類別的宣告和實作為。

|類別|描述|
|-----------|-----------------|
|`CAutomationEvents`|執行從物件取出的事件根物件 `DTE.Events` 。|
|`CProjectsEventsContainer` 和 `CProjectItemsEventsContainer`|執行引發對應事件的事件來源物件。|

 下列程式碼範例顯示如何回應事件物件的要求。

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

 在上述程式碼中， `g_wszAutomationProjects` 是您的專案集合名稱 (*FigProjects*) ， `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) 和 `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) 是源自于 VSPackage 的專案事件和專案專案事件的名稱。

 系統會從相同的中央位置（物件）抓取事件物件 `DTE.Events` 。 如此一來，所有事件物件都會群組在一起，讓使用者不必流覽整個物件模型來尋找特定的事件。 這也可讓您提供特定的 VSPackage 物件，而不需要針對全系統事件執行自己的程式碼。 不過，對於必須為您的介面尋找事件的終端使用者而言，並 `ProjectItem` 不會立即從該事件物件的抓取位置清楚清楚。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
