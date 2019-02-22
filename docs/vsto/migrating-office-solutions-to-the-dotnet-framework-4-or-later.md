---
title: 移轉至.NET Framework 4 或更新版本的 Office 方案
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 501145cf923efa979a0dd6bace3ebf4798ad1ba2
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875455"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>移轉至.NET Framework 4 或更新版本的 Office 方案
  如果 Office 專案的目標 framework 變更為[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本從.NET Framework 較早版本，一些額外的步驟可能需要以繼續在開發和終端使用者電腦上執行方案。 如需詳細資訊，請參閱 <<c0> [ 需要變更執行您移轉至.NET Framework 4 或.NET Framework 4.5 的 Office 專案](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。  
  
 此外，專案可能不會再編譯。 Office 專案的某些功能，針對不同版本的 .NET Framework 會有不同的程式設計模型。 當 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您就必須變更專案的下列程式碼：  
  
- [更新您移轉至.NET Framework 4 或.NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
- [更新您移轉至.NET Framework 4 或.NET Framework 4.5 的 Office 專案中的功能區自訂](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)  
  
- [更新您移轉至.NET Framework 4 或.NET Framework 4.5 之 Outlook 專案中的表單區域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
  當您從舊版的 Visual Studio 升級專案時，該 Office 專案的目標 Framework 就會變更。 如需詳細資訊，請參閱 <<c0> [ 升級和移轉 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
  如需有關為什麼在 Office 專案中的部分功能不同的程式設計模型目標時會有[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本，請參閱[的目標.NET Framework 4 或.NET Framework 4.5Office專案的設計變更](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)並[Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [如何：.NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [針對 Office 方案中的錯誤進行疑難排解](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office 方案錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)  
