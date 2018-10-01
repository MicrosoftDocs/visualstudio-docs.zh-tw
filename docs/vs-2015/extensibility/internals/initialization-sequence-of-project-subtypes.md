---
title: 專案子類型的初始化順序 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b69dc5bea8ffc6e8248e777990653ed24097a30
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488871"
---
# <a name="initialization-sequence-of-project-subtypes"></a>專案子類型的初始化順序
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[初始設定順序的專案子類型](https://docs.microsoft.com/visualstudio/extensibility/internals/initialization-sequence-of-project-subtypes)。  
  
環境呼叫的基底的 project factory 實作以建構專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>。 環境可讓您決定專案檔案的副檔名的專案類型 GUID 清單不是空白時，就會啟動專案子類型的建構。 此專案副檔名和專案 GUID 指定專案是否[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]或[!INCLUDE[csprcs](../../includes/csprcs-md.md)]專案類型。 比方說，.vbproj 副檔名和 {F184B08F-C81C-45F6-A57F-5ABD9991F28F} 識別[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]專案。  
  
## <a name="environments-initialization-of-project-subtypes"></a>專案子類型的環境的初始設定  
 下列程序詳細資料的彙總多個專案子類型的專案系統的初始化順序。  
  
1.  環境呼叫基底的專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>，而專案剖析其專案檔探索彙總的專案類型 Guid 清單不是`null`。 在中止的專案中，執行直接建立它的專案。  
  
2.  此專案會呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>服務來建立專案子類型使用的環境實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法。 這個方法內的環境可讓您實作遞迴函式呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>，`M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>方法時，它會逐一查看清單中的專案類型 Guid，從最外層的專案子類型。  
  
     下列詳細資料的初始化步驟。  
  
    1.  環境的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法呼叫 'HrCreateInnerProj' ' 和下列函式宣告的方法：  
  
        ```  
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
            BOOL *pfCancelled  
        )  
        ```  
  
         當呼叫此函式是第一次，也就是最外層的專案子類型參數`pOuter`並`pOwner`會傳入`null`和函式會將最外層的專案子類型`IUnknown`來`pOuter`。  
  
    2.  接下來會呼叫環境`HrCreateInnerProj`函式清單中的第二個專案類型 GUID。 此 GUID 對應至朝基底的專案中的彙總順序逐步執行的第二個內部專案子類型。  
  
    3.  `pOuter`現在會指向`IUnknown`最外層的專案子類型的並`HrCreateInnerProj`呼叫您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>後面接著呼叫您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>您傳入的控制的方法`IUnknown`最外層的專案子類型的`pOuter`。 擁有的專案 （內部專案子類型），就必須建立它的彙總的專案物件。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>方法實作您所傳遞的指標`IUnknown`內部專案正在彙總。 這兩種方法建立彙總物件，並將您的實作必須遵循 COM 彙總規則，以確保專案子類型不結束設定保存至其本身的參考計數。  
  
    4.  `HrCreateInnerProj` 呼叫您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>。 在這種方法，專案子類型會會其初始化工作。 您可以比方說，註冊方案中的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>。  
  
    5.  `HrCreateInnerProj` 被稱為遞迴運作，直到清單中的最後一個 GUID （基底的專案） 為止。 針對每個這些呼叫中，會重複執行步驟，c 到 d。 `pOuter` 最外層的專案子類型會指向`IUnknown`彙總的每個層級。  
  
 下列範例詳細說明以程式設計方式的程序中的近似表示<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法，因為它藉由環境。 程式碼只是一個範例;它不是在編譯和錯誤的所有檢查已移除為了清楚起見。  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [專案子類型](../../extensibility/internals/project-subtypes.md)

