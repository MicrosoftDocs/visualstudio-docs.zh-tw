---
title: "專案子類型的初始化順序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: db259b7bc5f9935b229f4f6522ae14a4496f0e15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-sequence-of-project-subtypes"></a>專案子類型的初始化順序
環境呼叫的基底的 project factory 實作以建構專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>。 當環境決定專案檔案的副檔名的專案類型的 GUID 清單不是空白時，就會啟動專案子類型的建構。 專案副檔名和專案 GUID 指定專案是否[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案類型。 例如，.vbproj 擴充功能和 {F184B08F-C81C-45F6-A57F-5ABD9991F28F} 識別[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案。  
  
## <a name="environments-initialization-of-project-subtypes"></a>環境的初始設定的專案子類型  
 下列程序詳述彙總多個專案子類型的專案系統的初始化順序。  
  
1.  環境呼叫基底的專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>，專案會剖析其專案檔時探索彙總的專案類型清單的 Guid 不是`null`。 專案中止直接建立它的專案。  
  
2.  專案呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>服務來建立專案子類型使用的環境實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法。 這個方法內的環境可讓您實作的遞迴函式呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>，`M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>方法時，它查核專案的清單型別從最外層的專案子類型的 Guid。  
  
     下列詳細資料的初始化步驟。  
  
    1.  環境的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法呼叫 'HrCreateInnerProj' ' 與下列函式宣告的方法：  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         當呼叫此函式是第一次，也就是最外層的專案子類型的參數`pOuter`和`pOwner`當做傳入`null`函式會將最外層的專案子類型和`IUnknown`至`pOuter`。  
  
    2.  接下來環境呼叫`HrCreateInnerProj`函式與清單中的第二個專案類型的 GUID。 此 GUID 對應於朝基底的專案中的彙總順序逐步執行的第二個內部專案子類型。  
  
    3.  `pOuter`現在指向`IUnknown`最外層的專案子類型的和`HrCreateInnerProj`的實作會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>後面的實作呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>方法您傳入控制`IUnknown`最外層的專案子類型的`pOuter`。 擁有的專案 （內部專案子類型） 必須建立它的彙總的專案物件。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>方法實作您要傳入的指標`IUnknown`內部專案進行彙總。 這兩種方法建立彙總物件，並將您的實作必須遵循 COM 彙總規則，以確保專案子類型不結束設定保存至其本身的參考計數。  
  
    4.  `HrCreateInnerProj`實作會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>。 在此方法中，專案子類型會執行其初始設定工作。 例如，可以註冊方案中的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>。  
  
    5.  `HrCreateInnerProj`被稱為遞迴運作，直到清單中的最後一個 GUID （基底的專案） 為止。 針對每個這些呼叫中，會重複步驟 c 到 d。 `pOuter`最外層的專案子類型會指向`IUnknown`每個層級的彙總。  
  
 下列範例詳細資料以程式設計方式的程序中的近似表示<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法，因為它藉由環境。 程式碼只是一個範例。它不是在編譯和錯誤的所有檢查已移除為了清楚起見。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
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
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [專案子類型](../../extensibility/internals/project-subtypes.md)