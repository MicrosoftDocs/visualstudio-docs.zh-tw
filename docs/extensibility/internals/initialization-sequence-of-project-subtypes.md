---
title: 專案子類型的初始化順序 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 678f704c73a39cdf2130d36fcfb1a74925dd89d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726882"
---
# <a name="initialization-sequence-of-project-subtypes"></a>專案子類型的初始化順序
環境會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 的基底專案 factory 來建立專案。 當環境判斷專案檔延伸模組的專案類型 GUID 清單不是空白時，就會啟動專案子類型的結構。 專案檔副檔名和專案 GUID 會指定專案為 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案類型。 例如，vbproj 副檔名和 {F184B08F-C81C-45F6-A57F-5ABD9991F28F} 可識別 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案。

## <a name="environments-initialization-of-project-subtypes"></a>環境的專案子類型初始化
 下列程式詳述由多個專案子類型所匯總之專案系統的初始化順序。

1. 環境會呼叫基底專案的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>，而當專案剖析其專案檔時，會發現匯總專案類型 Guid 清單未 `null`。 專案會中止直接建立其專案。

2. 專案會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> 服務上的 `QueryService`，以使用環境的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 方法執行來建立專案子類型。 在此方法中，環境會在流覽專案類型 Guid 的清單（從最外層的專案子類型開始）時，對您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 方法執行遞迴函式呼叫。

     以下詳細說明初始化步驟。

    1. 環境的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 方法的執行會使用下列函式宣告來呼叫 `HrCreateInnerProj` 方法：

         \<CodeContentPlaceHolder > 0 </CodeContentPlaceHolder>

         第一次呼叫此函式時（也就是最外層的專案子類型），`pOuter` 和 `pOwner` 的參數會以 `null` 的形式傳入，而函式會將最外層的專案子類型 `IUnknown` 設定為 `pOuter`。

    2. 接下來，環境會使用清單中的第二個專案類型 GUID 來呼叫 `HrCreateInnerProj` 函式。 此 GUID 對應至匯總序列中的基底專案逐步執行的第二個內部專案子類型。

    3. @No__t_0 現在指向最外層專案子類型的 `IUnknown`，`HrCreateInnerProj` 會呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 的執行，然後再呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 執行。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 方法中，您會傳入最外層專案子類型的控制 `IUnknown`，`pOuter`。 擁有的專案（內部專案子類型）必須在這裡建立其匯總專案物件。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 方法執行中，您會將指標傳入要匯總之內部專案的 `IUnknown`。 這兩種方法會建立匯總物件，而您的程式必須遵循 COM 匯總規則，以確保專案子類型不會最終將參考計數保存至其本身。

    4. `HrCreateInnerProj` 會呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 的執行。 在這個方法中，專案子類型會執行其初始化工作。 例如，您可以在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 中註冊方案事件。

    5. `HrCreateInnerProj` 會以遞迴方式呼叫，直到到達清單中的最後一個 GUID （基底專案）為止。 針對每個呼叫，會重複執行 c 到 d 的步驟。 `pOuter` 指向每個匯總層級的最外層專案子類型 `IUnknown`。

## <a name="example"></a>範例

下列範例會詳細說明環境中所執行之 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 方法的近似標記法中的程式設計進程。 程式碼只是一個範例，它不適合進行編譯，而且為了清楚起見，所有錯誤檢查都已移除。

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