---
title: 如何： 建立 SharePoint 方案的自訂功能和封裝驗證規則 |Microsoft Docs
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
ms.openlocfilehash: 1d36b049aefe9eb574809cfedf4aa1f2ebddbc4c
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118754"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>如何： 建立自訂的功能和封裝驗證規則，SharePoint 方案
  您可以建立自訂驗證規則，以確定 Visual Studio 所產生的方案套件。 您也可以選取整個功能或套件上執行完整驗證**Validate**從封裝或功能的操作功能表**PackagingExplorer**。 當您將新的功能或 SharePonit 專案項目加入專案，以判斷是否功能的封裝會處於有效狀態，則會執行部分驗證。  
  
### <a name="to-create-a-custom-package-validation-rule"></a>若要建立自訂封裝驗證規則  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立會實作下列介面的其中一個類別：  
  
    -   若要建立封裝驗證規則，請實作<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>介面。  
  
    -   若要建立功能驗證規則，請實作<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>介面。  
  
4.  新增<xref:System.ComponentModel.Composition.ExportAttribute>類別。 這個屬性可讓 Visual Studio 來探索及載入您的驗證規則。 傳遞<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>或<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>屬性建構函式的型別。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立自訂功能驗證規則。  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint。  
  
-   System.ComponentModel.Composition。  
  
## <a name="deploy-the-extension"></a>部署擴充功能  
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的 SharePoint 部署擴充功能工具](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
