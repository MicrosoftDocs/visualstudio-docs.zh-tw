---
title: 將專案物件公開 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4eaa2a5e8c5c153698069084b9f0cfe406cad7db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130449"
---
# <a name="exposing-project-objects"></a>公開專案物件
自訂專案類型可以提供 automation 物件，以便讓專案使用 automation 介面的存取權。 每個專案類型必須為提供標準<xref:EnvDTE.Project>自動化物件，存取從<xref:EnvDTE.Solution>，其中包含已經在 IDE 中開啟的所有專案的集合。 在專案中的每個項目必須由公開<xref:EnvDTE.ProjectItem>物件存取具有`Project.ProjectItems`。 除了這些標準 automation 物件，可以選擇專案的方案專案特定自動化物件。  
  
 您可以建立自訂根層級的自動化物件可以存取晚期繫結從根 DTE 物件使用`DTE.<customeObjectName>`或`DTE.GetObject("<customObjectName>")`。 例如，Visual c + + 會建立稱為 「 VCProjects 」，您可以使用 DTE 存取 c + + 專案特定專案集合。VCProjects 或 DTE。GetObject("VCProjects")。 您也可以建立 Project.Object，這是唯一的專案類型、 Project.CodeModel，可針對其最具衍生性的物件，而公開 ProjectItem.Object 和 ProjectItem.FileCodeModel 專案，項目查詢。  
  
 它是公開自訂的特定專案的專案集合的專案的常見慣例。 例如，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]建立 c + + 特定的專案集合，然後您可以存取使用`DTE.VCProjects`或`DTE.GetObject("VCProjects")`。 您也可以建立`Project.Object`，這是唯一的專案類型， `Project.CodeModel`，其最具衍生性的物件，其中可以查詢`ProjectItem`，哪一個公開`ProjectItem.Object`，和`ProjectItem.FileCodeModel`。  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>參與專案的 VSPackage 特定物件  
  
1.  將適當的索引鍵加入至.pkgdef 檔的 VSPackage。  
  
     例如，以下是 c + + 語言專案的.pkgdef 設定：  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  實作中的程式碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法，如下列範例所示。  
  
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
  
     在程式碼的`g_wszAutomationProjects`是您的專案集合的名稱。 `GetAutomationProjects`方法會建立該物件會實作`Projects`介面，並傳回`IDispatch`指標呼叫的物件，如下列程式碼範例所示。  
  
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
  
     您應該選擇 automation 物件的唯一名稱。 會產生無法預測，名稱衝突，衝突會導致衝突的物件名稱任意擲回多個專案類型使用相同的名稱。 您應該包含您的公司名稱或唯一的某種程度的 automation 物件的名稱及其產品名稱。  
  
     自訂`Projects`集合物件是您專案的 automation 模型的其餘部分方便進入點。 您的專案物件也是從存取<xref:EnvDTE.Solution>專案集合。 建立適當的程式碼和登錄項目可提供與取用者之後`Projects`物件集合，您的實作必須提供剩餘專案模型標準的物件。 如需詳細資訊，請參閱[專案模型](../../extensibility/internals/project-modeling.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>