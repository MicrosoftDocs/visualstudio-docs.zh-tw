---
title: 公開專案物件 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中公開自訂專案類型的物件，方法是提供允許使用自動化介面存取專案的自動化物件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0ad045cb2cc46577c06d65e3ac1236228c870a9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069682"
---
# <a name="expose-project-objects"></a>公開專案物件

自訂專案類型可以提供 automation 物件，以允許使用自動化介面存取專案。 每個專案類型都應提供 <xref:EnvDTE.Project> 從存取的標準 automation 物件 <xref:EnvDTE.Solution> ，其中包含在 IDE 中開啟的所有專案的集合。 專案中的每個專案都必須由 <xref:EnvDTE.ProjectItem> 使用存取的物件所公開 `Project.ProjectItems` 。 除了這些標準 automation 物件，專案也可以選擇提供專案特定的 automation 物件。

您可以建立自訂的根層級 automation 物件，您可以使用或從根 DTE 物件存取晚期 `DTE.<customObjectName>` 綁定 `DTE.GetObject("<customObjectName>")` 。 例如，Visual C++ 會建立名為 *VCProjects* 的 c + + 專案特定專案集合，而您可以使用或存取此集合 `DTE.VCProjects` `DTE.GetObject("VCProjects")` 。 您也可以建立 `Project.Object` 專案類型的唯一、 `Project.CodeModel` 可以查詢其最大衍生物件的，以及會 `ProjectItem` 公開 `ProjectItem.Object` 和的 `ProjectItem.FileCodeModel` 。

這是專案公開自訂、專案特定專案集合的常見慣例。 例如， [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 建立一個可供您使用或存取的 c + + 特定專案集合 `DTE.VCProjects` `DTE.GetObject("VCProjects")` 。 您也可以建立專案類型的唯一，也就是 `Project.Object` `Project.CodeModel` 可查詢其最大衍生物件的，也就是 `ProjectItem` 公開 `ProjectItem.Object` 和的 `ProjectItem.FileCodeModel` 。

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>提供專案的 VSPackage 特定物件

1. 將適當的金鑰新增至 VSPackage 的 *.pkgdef* 檔案。

     例如，以下是 c + + 語言專案的 *.pkgdef* 設定：

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. 在方法中執行程式碼 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> ，如下列範例所示。

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

     在程式碼中， `g_wszAutomationProjects` 是專案集合的名稱。 `GetAutomationProjects`方法會建立一個物件來執行 `Projects` 介面，並將指標傳回 `IDispatch` 給呼叫的物件，如下列程式碼範例所示。

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

     選擇 automation 物件的唯一名稱。 名稱衝突無法預期，而且如果有多個專案類型使用相同的名稱，衝突會造成衝突的物件名稱被隨機擲回。 您應在 automation 物件的名稱中包含公司名稱或其產品名稱的某些獨特層面。

     自訂 `Projects` 集合物件是專案自動化模型其餘部分的便利進入點。 專案集合也可以存取您的專案物件 <xref:EnvDTE.Solution> 。 在您建立適當的程式碼和登錄專案以提供取用者的 `Projects` 集合物件之後，您的執行必須為專案模型提供剩餘的標準物件。 如需詳細資訊，請參閱 [專案模型](../../extensibility/internals/project-modeling.md)化。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
