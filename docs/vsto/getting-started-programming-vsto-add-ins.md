---
title: VSTO 增益集程式設計入門
description: 瞭解如何使用 VSTO 增益集來自動化 Microsoft Office 的應用程式、擴充應用程式的功能，以及自訂應用程式的使用者介面。
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848288"
---
# <a name="get-started-programming-vsto-add-ins"></a>VSTO 增益集程式設計入門
> [!IMPORTANT]
> VSTO 相依于 [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview)。 您也可以使用 .NET Framework 來寫入 COM 增益集。 Office 增益集無法使用 [.Net Core 和 .net 5 +](https://docs.microsoft.com/dotnet/core/dotnet-five)（最新版本的 .net）建立。 這是因為 .NET Core/.NET 5 + 無法在相同的程式中與 .NET Framework 一起運作，而且可能會導致增益集載入失敗。 您可以繼續使用 .NET Framework 撰寫適用于 Office 的 VSTO 和 COM 增益集。 Microsoft 將不會更新 VSTO 或 COM 增益集平臺，以使用 .NET Core 或 .NET 5 +。 您可以利用 .NET Core 和 .NET 5 + （包括 ASP.NET Core）來建立 [Office Web 增益集](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)的伺服器端。

  您可以使用 VSTO 增益集來自動化 Microsoft Office 應用程式、擴充應用程式的功能，以及自訂應用程式的使用者介面 (UI)。 如需 VSTO 增益集與您可以使用 Visual Studio 建立之其他類型 Office 方案相較之下的詳細資訊，請參閱 [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>建立 VSTO 增益集專案
 使用 [ **新增專案** ] 對話方塊中的其中一個 vsto 增益集專案範本，建立 vsto 增益集專案。 這些範本包含必要的組件參考和專案檔。 Visual Studio 為 Office 中的大部分應用程式，提供 VSTO 增益集專案範本。

 如需如何建立 VSTO 增益集專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需專案範本的詳細資訊，請參閱 [Office 專案範本總覽](../vsto/office-project-templates-overview.md)。

## <a name="develop-vsto-add-in-projects"></a>開發 VSTO 增益集專案
 當您建立 VSTO 增益集專案時，Visual Studio 會在 c #  ) 程式碼檔案的 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) 或 *ThisAddIn* (中自動建立 ThisAddIn .vb (。 這個檔案包含 `ThisAddIn` 類別，該類別會提供 VSTO 增益集的基礎。 載入或卸載 VSTO 增益集時，您可以使用這個類別的成員來執行程式碼，以存取主應用程式的物件模型及擴充應用程式的功能。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

## <a name="automate-applications-by-using-the-object-models"></a>使用物件模型將應用程式自動化
 Microsoft Office 應用程式的物件模型公開許多您可以在 VSTO 增益集中進行程式設計的類型。 您可以使用這些類型將應用程式自動化。 例如，您可以在 Outlook 中以程式設計的方式建立和傳送電子郵件訊息，也可以在 Word 中開啟文件和加入內容。 如需如何在程式碼中存取主應用程式物件模型的詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

 如需特定的 Microsoft Office 應用程式之物件模型的詳細資訊，請參閱下列主題：

- [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)

- [Word 物件模型總覽](../vsto/word-object-model-overview.md)

- [Outlook 物件模型總覽](../vsto/outlook-object-model-overview.md)

- [InfoPath 解決方案](../vsto/infopath-solutions.md)

- [PowerPoint 方案](../vsto/powerpoint-solutions.md)

- [專案解決方案](../vsto/project-solutions.md)

- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>自訂應用程式的使用者介面
 有幾種不同的方式可使用 VSTO 增益集來自訂主應用程式的 UI：

- 對於 Excel 和 Word，您可以將 Managed 控制項加入文件。 如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

- 如果應用程式支援的話，您可以自訂功能區。 如需詳細資訊，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

- 如果應用程式支援的話，您可以建立自訂工作窗格。 如需詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)。

- 針對 Outlook，您可以建立自訂表單區域。 如需詳細資訊，請參閱 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

- 對於所有 Microsoft Office 應用程式，您可以在 VSTO 增益集中顯示 Windows Form。

  如需如何自訂 Microsoft Office 應用程式 UI 的詳細資訊，請參閱 [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

## <a name="next-steps"></a>後續步驟
 若要了解如何建立 VSTO 增益集，請參閱下面的逐步解說：

- [逐步解說：建立 Excel 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [逐步解說：建立 Outlook 的第一個 VSTO Add-In](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [逐步解說：建立 PowerPoint 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [逐步解說：建立 Project 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [逐步解說：建立 Word 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  這些逐步解說會為您介紹 Visual Studio 中的 Office Developer Tools，以及 VSTO 增益集的程式撰寫模型。

  如需引導您完成 Office 專案中一些常見工作的主題清單，請參閱 Office 程式 [設計的一般](../vsto/common-tasks-in-office-programming.md)工作。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
