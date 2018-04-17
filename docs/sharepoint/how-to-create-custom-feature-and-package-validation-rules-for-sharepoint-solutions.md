---
title: 如何： 建立 SharePoint 方案的自訂功能和封裝驗證規則 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c68df756e24fc45603d34dd6982a09889bd5203
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>如何：建立 SharePoint 方案的自訂功能和封裝驗證規則
  您可以建立自訂驗證規則來驗證由 Visual Studio 產生的方案套件。 您也可以選取 整個功能或封裝上執行完整驗證**驗證**從內容功能表的套件或在功能**PackagingExplorer**。 當您將新功能或 SharePonit 專案項目加入至專案，以判斷封裝或功能是否會處於有效狀態，則會執行部分驗證。  
  
### <a name="to-create-a-custom-package-validation-rule"></a>若要建立自訂封裝驗證規則  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立會實作下列介面的其中一個類別：  
  
    -   若要建立封裝驗證規則，請實作<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>介面。  
  
    -   若要建立功能驗證規則，請實作<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>介面。  
  
4.  新增<xref:System.ComponentModel.Composition.ExportAttribute>至類別。 此屬性可讓 Visual Studio 來探索和載入您的驗證規則。 傳遞<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>或<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>屬性建構函式的類型。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立自訂功能驗證規則。  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint。  
  
-   System.ComponentModel.Composition。  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  