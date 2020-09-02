---
title: SharePoint 方案：建立自訂功能、封裝驗證規則
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f731b6af2ada8caddb84be5561d7f6dc304e7bbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016915"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>如何：建立 SharePoint 方案的自訂功能和套件驗證規則
  您可以建立自訂驗證規則，以確認 Visual Studio 所產生的解決方案套件。 您可以從**PackagingExplorer**中封裝或功能的內容功能表中選取 [**驗證**]，對整個功能或封裝執行完整驗證。 當您將新的 SharePoint 專案專案或功能加入至專案時，會執行部分驗證，以判斷封裝或功能是否處於有效的狀態。

### <a name="to-create-a-custom-package-validation-rule"></a>若要建立自訂套件驗證規則

1. 建立類別庫 (Class Library) 專案。

2. 加入下列組件的參考：

    - VisualStudio SharePoint

    - System.ComponentModel.Composition

3. 建立可執行下列其中一個介面的類別：

    - 若要建立封裝驗證規則，請執行 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 介面。

    - 若要建立功能驗證規則，請執行 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 介面。

4. 將加入 <xref:System.ComponentModel.Composition.ExportAttribute> 至類別。 這個屬性可讓 Visual Studio 探索和載入您的驗證規則。 將 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 或型別傳遞 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 至屬性（attribute）的函式。

## <a name="example"></a>範例
 下列程式碼範例示範如何建立自訂功能驗證規則。

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio。

- ComponentModel 組合。

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
