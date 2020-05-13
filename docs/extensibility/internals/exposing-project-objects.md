---
title: 公開項目物件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708476"
---
# <a name="expose-project-objects"></a>公開項目物件

自定義項目類型可以提供自動化物件,以便允許使用自動化介面訪問專案。 每個項目類型都應提供從<xref:EnvDTE.Project><xref:EnvDTE.Solution>訪問的標準自動化物件,該物件包含 IDE 中打開的所有專案的集合。 專案中的每個項都應被訪問<xref:EnvDTE.ProjectItem>`Project.ProjectItems`的物件公開。 除了這些標準自動化物件之外,專案還可以選擇提供特定於專案的自動化物件。

您可以創建自定義根級自動化物件,可以使用`DTE.<customObjectName>``DTE.GetObject("<customObjectName>")`或從根 DTE 物件訪問後期綁定物件。 例如,Visual C++創建一個名為*VCProjects*的專案C++專案集合,`DTE.VCProjects`您`DTE.GetObject("VCProjects")`可以使用 或進行訪問。 還可以建立一個`Project.Object`對於項目類型是唯一`Project.CodeModel`的 ,可以查詢其最派生的物件`ProjectItem``ProjectItem.Object`,`ProjectItem.FileCodeModel`以及 公開 和 的 。

它是專案公開自定義、特定於專案的專案集合的常見約定。 例如,[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]創建C++特定的專案集合,然後可以`DTE.VCProjects`使用`DTE.GetObject("VCProjects")`或進行訪問。 還可以建立一個`Project.Object`對於項目類型是唯一`Project.CodeModel`的 ,可以查詢其最派生的物件`ProjectItem``ProjectItem.Object`,`ProjectItem.FileCodeModel`公開 的和 。

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>為項目貢獻特定於 VSPackage 的物件

1. 將適當的鍵添加到 VSPackage 的 *.pkgdef*檔。

     例如,以下是C++語言專案的 *.pkgdef*設置:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. 在方法中實現代碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>,如以下範例所示。

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

     在代碼中,`g_wszAutomationProjects`是專案集合的名稱。 該方法`GetAutomationProjects`創建一個`Projects`實現 介面並返回指向調用`IDispatch`對象的指標的物件,如下代碼示例所示。

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

     為自動化物件選擇唯一名稱。 名稱衝突不可預測,如果多個項目類型使用相同的名稱,衝突會導致任意拋出衝突的物件名稱。 您應該在自動化物件的名稱中包括公司名稱或其產品名稱的某些獨特方面。

     自定義`Projects`集合對像是專案自動化模型其餘部分的方便入口點。 項目物件還可以從<xref:EnvDTE.Solution>專案集合訪問。 創建向消費者提供`Projects`集合物件的相應代碼和註冊表項後,實現必須為專案模型提供剩餘的標準物件。 有關詳細資訊,請參閱[專案建模](../../extensibility/internals/project-modeling.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
