---
title: 建立 SharePoint 方案的功能和套件驗證
titleSuffix: ''
description: 建立自訂驗證規則，以驗證 Visual Studio 所產生的方案套件，或確認整個功能。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee6b27b92f1c79bfda95ba3d6dce7dbdce4a6fac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216562"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>建立 SharePoint 方案的功能和套件驗證

  您可以建立自訂驗證規則，以確認 Visual Studio 所產生的解決方案套件。 您可以從 **PackagingExplorer** 中封裝或功能的內容功能表中選取 [**驗證**]，對整個功能或封裝執行完整驗證。 當您將新的 SharePoint 專案專案或功能加入至專案時，會執行部分驗證，以判斷封裝或功能是否處於有效的狀態。

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

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio。

- ComponentModel 組合。

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
