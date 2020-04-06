---
title: 項目子型態的初始化序列 :微軟文件
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
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707624"
---
# <a name="initialization-sequence-of-project-subtypes"></a>專案子類型的初始化順序
環境通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>的基礎專案工廠實現來構造專案。 當環境確定專案檔副檔名的專案類型 GUID 清單不為空時,專案子類型的構造將開始。 專案檔副檔名和專案 GUID[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]指定[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案是 或專案類型。 例如,.vbproj 擴展和 [F184B08F-C81C-45F6-A57F-5ABD9991F28F] 標識[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案。

## <a name="environments-initialization-of-project-subtypes"></a>環境對專案子型態的初始化
 以下過程詳細介紹了由多個專案子類型聚合的專案系統的初始化序列。

1. 環境呼叫基礎項目的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>,當專案解析其項目檔時,它發現聚合項目類型 GUIDs`null`清單不是 。 專案停止直接創建其專案。

2. 專案調用`QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>服務使用環境<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>實現 的方法創建專案子類型。 在此方法中,環境在遍走專案類型 GUID 的清單<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>時<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>,<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>從最外層的專案子類型開始,對的實現和方法進行遞歸函數調用。

     下面詳細介紹了初始化步驟。

    1. 該方法的環境實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>呼叫具有以下函式`HrCreateInnerProj`聲明 的方法:

         \<代碼內容持有者>0</CodeContentPlaceHolder>

         設定`pOuter`此函數時,即對最外層的項目子類型`pOwner`,參數和 參數以 as 與`null`最外層項目子`IUnknown`類型設定`pOuter`為 。

    2. 接下來,環境調用`HrCreateInnerProj`函數,清單中的第二個項目類型 GUID。 此 GUID 對應於聚合序列中向基專案步進的第二個內部專案子類型。

    3. `pOuter`現在指向`IUnknown`最外層項目子型態的`HrCreateInnerProj`, 並<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>呼叫的, 然後<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>呼叫 您的 實作 。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>方法中,您可以控制`IUnknown`最外層的項目子型態`pOuter`。 擁有的專案(內部專案子類型)需要在此處創建其聚合專案物件。 在方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>實現中,您將指標傳遞給要聚合`IUnknown`的內部項目的指標。 這兩種方法創建聚合物件,您的實現需要遵循 COM 聚合規則,以確保專案子類型最終不會包含對自身的引用計數。

    4. `HrCreateInnerProj`呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>的實作的實作的 。 在此方法中,專案子類型執行其初始化工作。 例如,您可以在中<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>註冊解決方案事件。

    5. `HrCreateInnerProj`遞迴呼用,直到到達清單中的最後一個 GUID(基礎專案)。 對於每個調用,重複步驟(c 到 d)。 `pOuter`指向每個聚合級別的最外層專案`IUnknown`子類型。

## <a name="example"></a>範例

下面的示例詳細介紹了<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>由環境實現的方法的近似表示形式中的程式設計過程。 代碼只是一個示例;它不打算編譯,並且所有錯誤檢查都被刪除,以便清楚。

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

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [專案子類型](../../extensibility/internals/project-subtypes.md)
