---
title: Office 方案移轉至.NET Framework 4 或更新版本 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac244bebb1a625c7858a62399ee79126e309cf2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571795"
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Office 方案移轉至.NET Framework 4 或更新版本
  如果 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，可能需要一些額外的步驟，才能繼續在開發和使用者電腦上執行解決方案。 如需詳細資訊，請參閱[所需的變更就可以執行您要移轉至.NET Framework 4 或.NET Framework 4.5 的 Office 專案](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。  
  
 此外，專案可能不會再編譯。 Office 專案的某些功能，針對不同版本的 .NET Framework 會有不同的程式設計模型。 當 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您就必須變更專案的下列程式碼：  
  
-   [更新您要移轉至.NET Framework 4 或.NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新您要移轉至.NET Framework 4 或.NET Framework 4.5 的 Office 專案中的功能區自訂](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新您要移轉至.NET Framework 4 或.NET Framework 4.5 之 Outlook 專案中的表單區域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 當您從舊版的 Visual Studio 升級專案時，該 Office 專案的目標 Framework 就會變更。 如需詳細資訊，請參閱[升級和移轉 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
 如需有關為什麼 Office 專案中的某些功能有不同程式設計模型為目標時[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本中，請參閱[變更為目標的.NET Framework 4 或.NET Framework 4.5Office專案的設計](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)和[Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [如何： 以.NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [針對在 Office 方案中的錯誤進行疑難排解](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office 方案錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  