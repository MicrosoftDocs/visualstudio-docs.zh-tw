---
title: 將 Office 方案遷移至 .NET Framework 4 或更新版本
description: 瞭解如何將 Office 方案遷移至 .NET Framework 4 或更新版本，讓您的專案可以繼續運作。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8c11b2f107414ac5ffb048d7c5e49609ba0b17b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946133"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>將 Office 方案遷移至 .NET Framework 4 或更新版本
  如果 Office 專案的目標 framework [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 從舊版 .NET Framework 變更為或更新版本，可能需要一些額外的步驟，才能繼續在開發和終端使用者電腦上執行解決方案。 如需詳細資訊，請參閱 [執行您遷移至 .NET Framework 4 或 .NET Framework 4.5 之 Office 專案的必要變更](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。

 此外，專案可能不會再編譯。 Office 專案的某些功能，針對不同版本的 .NET Framework 會有不同的程式設計模型。 當 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您就必須變更專案的下列程式碼：

- [更新您遷移至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [更新 Office 專案中您遷移至 .NET Framework 4 或 .NET Framework 4.5 的功能區自訂](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [更新 Outlook 專案中您遷移至 .NET Framework 4 或 .NET Framework 4.5 的表單區域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  當您從舊版的 Visual Studio 升級專案時，該 Office 專案的目標 Framework 就會變更。 如需詳細資訊，請參閱 [升級和遷移 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)。

  如需 Office 專案中某些功能在以或更新版本為目標時有不同程式設計模型之原因的詳細資訊 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，請參閱 [以 .NET Framework 4 或 .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) 和 [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)為目標的 office 專案設計變更。

## <a name="see-also"></a>另請參閱
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [如何：將 .NET Framework 的某個版本設定為目標](../ide/visual-studio-multi-targeting-overview.md)
- [針對 Office 方案中的錯誤進行疑難排解](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Office 方案中錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)
