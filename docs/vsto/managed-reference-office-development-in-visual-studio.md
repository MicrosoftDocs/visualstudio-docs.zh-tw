---
title: 在 Visual Studio) 中 (Office 開發的受控參考
description: 深入瞭解以 .NET Framework 為目標的 Office 專案中所使用之命名空間和類型的 API 參考檔。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9364b191886408e509aa09a83bde70ce8240707e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958748"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>在 Visual Studio) 中 (Office 開發的受控參考
  本節包含命名空間的應用程式開發介面參考文件，和用在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](includes/net-v45-md.md)]之 Office 專案中的類型。 如需有關以 .NET Framework 3.5 為目標的 Office 專案所使用之命名空間和類型的 API 參考檔，請參閱 Visual Studio 檔中的下列參考章節： [Visual Studio) 中 (Office 開發的 Managed 參考 ](managed-reference-office-development-in-visual-studio.md)。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>本節內容
 <xref:Microsoft.Office.Tools>

 包含程式設計 Office 解決方案的常見類別。 包括 VSTO 增益集的基底類別、在 VSTO 增益集中建立自訂工作窗格的類別、在 Excel 和 Word 解決方案中建立智慧標籤的類別，以及在文件層級自訂中建立執行窗格的類別。

 <xref:Microsoft.Office.Tools.Excel>

 包含可用於 Excel 解決方案的主控制項和主項目。

 <xref:Microsoft.Office.Tools.Excel.Controls>

 包含可用於 Excel 解決方案的 Excel 控制項和 Windows Form 控制項。

 <xref:Microsoft.Office.Tools.Outlook>

 包含 Outlook VSTO 增益集使用的類別，包括用來建立自訂表單區域的類別。

 <xref:Microsoft.Office.Tools.Ribbon>

 包含用於以程式設計方式修改功能區自訂項目的類別，這些功能區自訂項目是使用功能區設計工具所建立。

 <xref:Microsoft.Office.Tools.Word>

 包含可用於 Word 解決方案的主控制項和主項目。

 <xref:Microsoft.Office.Tools.Word.Controls>

 包含可用於 Word 解決方案的 Word 控制項和 Windows Forms 控制項。

 <xref:Microsoft.VisualStudio.Tools.Applications>

 包含 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別和一組相關的快取資料類別。 在沒有安裝 Microsoft Office 的電腦上，這些類別可以用來修改文件層級自訂的某些層面。

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 包含 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 介面 (可實作來建立 Office 解決方案的 *部署後動作* )、在安裝 Office 解決方案時可能會擲回的例外狀況，以及其他屬於 Visual Studio 基礎結構的應用程式開發介面。

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 包含可由 [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)]擲回的大部分例外狀況，可以用來快取文件層級自訂項目資料的數種類別，以及其他屬於 Visual Studio 基礎結構的應用程式開發介面。

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 包含用於建置 Office 專案的 MSBuild 工作類別。

## <a name="see-also"></a>另請參閱
- [適用于 Office 執行時間的 Visual Studio 工具總覽](visual-studio-tools-for-office-runtime-overview.md)
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](getting-started-office-development-in-visual-studio.md)
- [Office 開發範例和逐步解說](office-development-samples-and-walkthroughs.md)
- [設計和建立 Office 方案](designing-and-creating-office-solutions.md)
