---
title: 將 Office 方案遷移至 .NET Framework 4 或更新版本
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
ms.openlocfilehash: b9531f0495bd0dc0a9f095ff71fdfd84fc8d1380
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189773"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>將 Office 方案遷移至 .NET Framework 4 或更新版本
  如果 Office 專案的目標 framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，可能需要一些額外的步驟，才能繼續在開發和終端使用者電腦上執行解決方案。 如需詳細資訊，請參閱[執行您遷移至 .NET Framework 4 或 .NET Framework 4.5 之 Office 專案的必要變更](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。

 此外，專案可能不會再編譯。 Office 專案的某些功能，針對不同版本的 .NET Framework 會有不同的程式設計模型。 當 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您就必須變更專案的下列程式碼：

- [更新您遷移至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [更新您遷移至 .NET Framework 4 或 .NET Framework 4.5 之 Office 專案中的功能區自訂](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [更新您遷移至 .NET Framework 4 或 .NET Framework 4.5 的 Outlook 專案中的表單區域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  當您從舊版的 Visual Studio 升級專案時，該 Office 專案的目標 Framework 就會變更。 如需詳細資訊，請參閱[升級和遷移 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)。

  如需當您以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標時，Office 專案中某些功能有不同程式設計模型的詳細資訊，請參閱[以 .NET Framework 4 或 .NET Framework 4.5 和視覺效果為目標之 office 專案的設計變更](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) [Studio Tools for Office runtime 總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

## <a name="see-also"></a>請參閱
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [如何：以 .NET Framework 的版本為目標](../ide/visual-studio-multi-targeting-overview.md)
- [針對 Office 方案中的錯誤進行疑難排解](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Office 方案中錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)
