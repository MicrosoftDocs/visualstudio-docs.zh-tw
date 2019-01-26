---
title: 公開專案物件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16a9c34d06cc94e3c9fb41fa3cc09b12b7349849
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992889"
---
# <a name="expose-project-objects"></a>公開專案物件

自訂專案類型可提供 automation 物件，以便使用自動化介面專案的存取權。 預期每個專案類型提供的標準<xref:EnvDTE.Project>自動化物件，從存取<xref:EnvDTE.Solution>，其中包含已經在 IDE 中開啟的所有專案集合。 在專案中的每個項目應該由<xref:EnvDTE.ProjectItem>物件使用存取`Project.ProjectItems`。 除了這些標準 automation 物件，可以選擇專案的方案專案特定的自動化物件。

您可以建立自訂的根層級自動化物件，您可以存取晚期繫結從根 DTE 物件使用`DTE.<customObjectName>`或`DTE.GetObject("<customObjectName>")`。 例如，Visual c + + 會建立名為 c + + 專案特定的專案集合*VCProjects*您可以使用來存取`DTE.VCProjects`或`DTE.GetObject("VCProjects")`。 您也可以建立`Project.Object`，這是唯一的專案類型中`Project.CodeModel`，可針對其最高衍生性的物件，查詢並`ProjectItem`，以公開`ProjectItem.Object`和`ProjectItem.FileCodeModel`。

它是常見的慣例來公開為自訂的特定專案的專案集合的專案。 例如，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]建立您接著可以存取使用的 c + + 特定的專案集合`DTE.VCProjects`或`DTE.GetObject("VCProjects")`。 您也可以建立`Project.Object`，這是唯一的專案類型中`Project.CodeModel`，其最高衍生性的物件，可查詢`ProjectItem`，以公開`ProjectItem.Object`，和`ProjectItem.FileCodeModel`。  
  
## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>若要參與專案的 VSPackage 特定物件  
  
1.  將適當的索引鍵，加入 *.pkgdef* VSPackage 的檔案。  
  
     例如，以下是 *.pkgdef* c + + 語言專案設定：  
  
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
  
     選擇您的 automation 物件的唯一名稱。 會無法預期，名稱衝突，衝突會造成衝突的物件名稱任意時擲多個專案類型使用相同的名稱。 您應該包含您公司的名稱或唯一的某種程度的 automation 物件的名稱及其產品名稱。  
  
     自訂`Projects`集合物件是您專案的自動化模型的其餘部分的便利性進入點。 您的專案物件也是從可存取<xref:EnvDTE.Solution>專案集合。 建立提供取用者使用適當的程式碼和登錄項目之後`Projects`物件集合，您的實作必須提供其餘專案模型的標準物件。 如需詳細資訊，請參閱 <<c0> [ 專案模型化](../../extensibility/internals/project-modeling.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
