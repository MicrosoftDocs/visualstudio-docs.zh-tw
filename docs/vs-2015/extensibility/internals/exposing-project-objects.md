---
title: 公開專案物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196648"
---
# <a name="exposing-project-objects"></a>公開專案物件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

自訂專案類型可提供 automation 物件，以便使用自動化介面專案的存取權。 預期每個專案類型提供的標準<xref:EnvDTE.Project>自動化物件，從存取<xref:EnvDTE.Solution>，其中包含已經在 IDE 中開啟的所有專案集合。 在專案中的每個項目應該由<xref:EnvDTE.ProjectItem>物件使用存取<xref:EnvDTE.Project.ProjectItems>。 除了這些標準 automation 物件，可以選擇專案的方案專案特定的自動化物件。  
  
 您可以建立自訂的根層級自動化物件，您可以存取晚期繫結從根 DTE 物件使用`DTE.<customeObjectName>`或`DTE.GetObject(“<customObjectName>”)`。 例如，視覺效果C++建立C++名為"VCProjects 」，您可以使用 DTE 存取特定專案的專案集合。VCProjects 或 DTE。GetObject("VCProjects")。 您也可以建立 Project.Object，也就是唯一的專案類型中 Project.CodeModel，可以查詢其最高衍生性的物件，而會公開 ProjectItem.Object 和 ProjectItem.FileCodeModel 專案，項目。  
  
 它是常見的慣例來公開為自訂的特定專案的專案集合的專案。 例如，[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]建立C++，然後您可以存取使用特定的專案集合`DTE.VCProjects`或是`DTE.GetObject("VCProjects")`。 您也可以建立`Project.Object`，這是唯一的專案類型中`Project.CodeModel`，其最高衍生性的物件，可查詢`ProjectItem`，以公開`ProjectItem.Object`，和`ProjectItem.FileCodeModel`。  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>若要參與專案的 VSPackage 特定物件  
  
1. VSPackage 的.pkgdef 檔中加入適當的索引鍵。  
  
     例如，以下是.pkgdef 設定C++語言專案：  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. 實作中的程式碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法，如下列範例所示。  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     在程式碼的`g_wszAutomationProjects`是您的專案集合的名稱。 `GetAutomationProjects`方法會建立該物件會實作`Projects`介面，並傳回`IDispatch`呼叫物件，如下列程式碼範例所示的指標。  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     您應該選擇您的 automation 物件的唯一名稱。 會無法預期，名稱衝突，衝突會造成衝突的物件名稱任意時擲多個專案類型使用相同的名稱。 您應該包含您公司的名稱或唯一的某種程度的 automation 物件的名稱及其產品名稱。  
  
     自訂`Projects`集合物件是您專案的自動化模型的其餘部分的便利性進入點。 您的專案物件也是從可存取<xref:EnvDTE.Solution>專案集合。 建立提供取用者使用適當的程式碼和登錄項目之後`Projects`物件集合，您的實作必須提供其餘專案模型的標準物件。 如需詳細資訊，請參閱 <<c0> [ 專案模型化](../../extensibility/internals/project-modeling.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
