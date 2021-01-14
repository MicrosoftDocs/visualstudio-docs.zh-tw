---
title: 專案子類型的初始化順序 |Microsoft Docs
description: 瞭解 Visual Studio 環境中，以多個專案子類型匯總的專案系統的初始化順序。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea784eae808cbab3a5991651961d3b150b641c04
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204705"
---
# <a name="initialization-sequence-of-project-subtypes"></a>專案子類型的初始化順序
環境會呼叫的基底專案 factory，以建立專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 。 當環境判斷專案檔延伸的專案類型 GUID 清單不是空的時，就會啟動專案子類型的結構。 專案檔延伸和專案 GUID 會指定專案為 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案類型。 例如，vbproj 副檔名和 {F184B08F-C81C-45F6-A57F-5ABD9991F28F} 會識別 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案。

## <a name="environments-initialization-of-project-subtypes"></a>環境對專案子類型的初始化
 下列程式詳細說明由多個專案子類型所匯總之專案系統的初始化順序。

1. 環境會呼叫基底專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> ，而當專案剖析其專案檔時，它會發現匯總專案類型 guid 清單不是 `null` 。 專案會中止直接建立其專案。

2. 專案會 `QueryService` 在服務上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> ，以使用環境的方法執行來建立專案子類型 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 。 在這個方法中，環境會在從專案類型 Guid 清單開始時，將遞迴函式呼叫用於您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 方法，從最外層的專案子類型開始。

     下列詳述初始化步驟。

    1. 環境的方法執行會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> `HrCreateInnerProj` 使用下列函式宣告呼叫方法：

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         第一次呼叫此函式時（也就是最外層的專案子類型），參數 `pOuter` 和 `pOwner` 會傳入做為，且函式會 `null` 將最外層的專案子類型設定 `IUnknown` 為 `pOuter` 。

    2. 接下來，環境會 `HrCreateInnerProj` 使用清單中的第二個專案類型 GUID 來呼叫函數。 此 GUID 對應至逐步執行匯總序列中基底專案的第二個內部專案子類型。

    3. `pOuter`現在指向 `IUnknown` 最外層專案子類型的，然後 `HrCreateInnerProj` 呼叫您的實執行，然後 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 呼叫您的實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 方法中，您會傳入 `IUnknown` 最外層專案子類型的控制 `pOuter` 。 所擁有的專案 (內部專案子類型) 需要在此處建立其匯總專案物件。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 方法執行中，您會將指標傳遞至 `IUnknown` 正在匯總之內部專案的。 這兩種方法會建立匯總物件，而您的執行必須遵循 COM 匯總規則，以確保專案子類型最後不會將參考計數保留給本身。

    4. `HrCreateInnerProj` 呼叫您的執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 。 在這個方法中，專案子類型會執行其初始化工作。 例如，您可以在中註冊方案事件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 。

    5. `HrCreateInnerProj` 會以遞迴方式呼叫，直到到達清單中的最後一個 GUID (基底專案) 為止。 針對每個呼叫，步驟（c 到 d）都會重複。 `pOuter` 指向 `IUnknown` 每個匯總層級的最外層專案子類型。

## <a name="example"></a>範例

下列範例會詳細說明程式設計程式在此 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 方法由環境執行時的近似標記法。 程式碼只是一個範例;這並不是要進行編譯，而且為了清楚起見，已移除所有錯誤檢查。

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [專案子類型](../../extensibility/internals/project-subtypes.md)
