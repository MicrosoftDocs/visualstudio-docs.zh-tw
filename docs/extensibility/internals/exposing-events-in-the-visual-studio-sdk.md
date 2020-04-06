---
title: 在可視化工作室 SDK 中公開事件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708492"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>在視覺化工作室 SDK 中公開事件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]允許您使用自動化來源事件。 我們建議您為專案和專案項源事件。

 事件由自動化消費者從<xref:EnvDTE.DTEClass.Events%2A>物件<xref:EnvDTE.DTEClass.GetObject%2A>或 (`GetObject("EventObjectName")`例如) 檢索。 環境通過使用`IDispatch::Invoke``DISPATCH_METHOD``DISPATCH_PROPERTYGET`或標誌來調用事件。

 以下過程說明如何返回特定於 VSPackage 的事件。

1. 環境開始。

2. 它從註冊表讀取所有 VSPackages 的**自動化**、**自動化事件**和**自動化屬性**鍵下的所有值名稱,並將這些名稱儲存在表中。

3. 自動化使用者呼叫,在此範例中,`DTE.Events.AutomationProjectsEvents``DTE.Events.AutomationProjectItemsEvents`或 。

4. 環境在表中尋找字串參數並載入相應的 VSPackage。

5. 環境使用調用中<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>傳遞的名稱調用方法;使用調用中傳遞的名稱調用 方法。這個範例中,`AutomationProjectsEvents``AutomationProjectItemsEvents`或 。

6. VSPackage 創建具有 方法`get_AutomationProjectsEvents`(`get_AutomationProjectItemEvents`如 和 ,然後返回指向該物件的 IDispatch 指標)的根物件。

7. 環境根據傳入自動化調用的名稱調用適當的方法。

8. 該方法`get_`創建另一個基於 IDispatch 的事件`IConnectionPointContainer`物件,該`IConnectionPoint`物件同時實現`IDispatchpointer`介面和介面, 並將返回到該物件。

   要使用自動化公開事件,必須回應<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>並監視添加到註冊表中的字串。 在基本項目範例中,字串是*BscProjects 事件*與*BscProjectItem 事件*。

## <a name="registry-entries-from-the-basic-project-sample"></a>基本項目範例中的註冊表項
 本節顯示向註冊表添加自動化事件值的位置。

 **[HKEY_LOCAL_MACHINE_SOFTWARE_微軟_VisualStudio_8.0_包\\<PkgGUID\>[自動化事件]**

 **自動化專案事件**`AutomationProjectEvents`= 傳回物件。

 **自動化專案專案事件**`AutomationProjectItemsEvents`= 傳回物件。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|預設值 (*)|REG_SZ|未使用|未使用的。 您可以使用資料欄位進行文件記錄。|
|*自動化專案事件*|REG_SZ|事件物件的名稱。|只有鍵名稱相關。 您可以使用資料欄位進行文件記錄。<br /><br /> 此示例來自基本專案示例。|
|*自動化項目專案事件*|REG_SZ|事件物件的名稱|只有鍵名稱相關。 您可以使用資料欄位進行文件記錄。<br /><br /> 此示例來自基本專案示例。|

 當自動化消費者請求任何事件物件時,請創建一個根物件,該物件具有 VSPackage 支援的任何事件的方法。 環境在此對象上調`get_`用 適當的方法。 例如,如果`DTE.Events.AutomationProjectsEvents`調用,則調用根`get_AutomationProjectsEvents`物件上的方法。

 ![視覺化工作室項目活動](../../extensibility/internals/media/projectevents.gif "專案事件")事件自動化模型

 類`CProjectEventsContainer`表示*BscProjectsEvents*的源物件`CProjectItemsEventsContainer`,表示*BscProjectItems 事件的*源物件。

 在大多數情況下,必須為每個事件請求返回一個新對象,因為大多數事件物件都採用篩選器物件。 觸發事件時,請檢查此篩選器以驗證是否正在調用事件處理程式。

 *自動化事件.h*和*自動化事件.cpp*包含下表中類的聲明和實現。

|類別|描述|
|-----------|-----------------|
|`CAutomationEvents`|實現從`DTE.Events`物件檢索的事件根物件。|
|`CProjectsEventsContainer` 和 `CProjectItemsEventsContainer`|實現觸發相應事件的事件源物件。|

 以下代碼示例演示如何回應事件物件的請求。

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

 在上面`g_wszAutomationProjects`的代碼中,是專案集合 *(FigProjects)*`g_wszAutomationProjectsEvents`的名稱 *(FigProjects)* 和`g_wszAutomationProjectItemsEvents`*(FigProject事件*)是從 VSPackage 實現來源的專案事件和專案專案事件的名稱。

 從同一中心位置(該物件)`DTE.Events`檢索事件物件。 這樣,所有事件物件都分組在一起,以便最終使用者不必瀏覽整個物件模型來查找特定事件。 這還允許您提供特定的 VSPackage 物件,而不是要求您為系統範圍的事件實現自己的代碼。 但是,對於最終用戶,他們必須為您的`ProjectItem`介面查找事件,則無法立即從何處檢索該事件物件。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
