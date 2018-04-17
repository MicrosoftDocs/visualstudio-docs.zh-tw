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
ms.openlocfilehash: 830dcdb9e42472aa712c86ddb117b3b8003ac4d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>將 Office 方案移轉至 .NET Framework 4 或更新版本
  如果 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，可能需要一些額外的步驟，才能繼續在開發和使用者電腦上執行解決方案。 如需詳細資訊，請參閱[需要變更執行 Office 專案，您要移轉至.NET Framework 4 或.NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。  
  
 此外，專案可能不會再編譯。 Office 專案的某些功能，針對不同版本的 .NET Framework 會有不同的程式設計模型。 當 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您就必須變更專案的下列程式碼：  
  
-   [更新 Excel 和 Word 專案，您要移轉至.NET Framework 4 或.NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新您要移轉至.NET Framework 4 或.NET Framework 4.5 的 Office 專案中的功能區自訂](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新您要移轉至.NET Framework 4 或.NET Framework 4.5 之 Outlook 專案中的表單區域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 當您從舊版的 Visual Studio 升級專案時，該 Office 專案的目標 Framework 就會變更。 如需詳細資訊，請參閱 [Upgrading and Migrating Office Solutions](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
 如需有關為什麼 Office 專案中的某些功能有不同程式設計模型為目標時[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本中，請參閱[設計 Office 專案的目標.NET Framework 4 或.NET Framework 4.5變更](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)和[Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [疑難排解 Office 方案中的錯誤](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office 方案錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  