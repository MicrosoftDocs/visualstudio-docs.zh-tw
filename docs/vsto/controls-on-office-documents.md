---
title: Office 檔上的控制項
description: 瞭解如何使用 Visual Studio 中的 Office 開發工具，將 Windows Forms 控制項和主控制項加入 Word 檔和 Excel 工作表。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], about controls on Office documents
- Office documents [Office development in Visual Studio, controls
- document-level customizations [Office development in Visual Studio], controls
- controls [Office development in Visual Studio]
- documents [Office development in Visual Studio], controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 203edcf2b77cfff3fb557ce7c1c8fea7592e17ea
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847984"
---
# <a name="controls-on-office-documents"></a>Office 檔上的控制項
  您也可以在 Visual Studio 中使用 Office 開發工具，將 Windows Forms 控制項和「主控制項」 *appliesto_controls* (Host Control) 加入 Word 文件和 Excel 工作表。 主控制項是一種物件，在 Word 和 Excel 物件模型中擴充各種使用者介面 (UI) 物件。

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 當您為 Excel 或 Word 開發 VSTO 增益集專案時，您可以用程式設計方式在執行階段將這些控制項加入任何開啟的文件或活頁簿。

 當您開發 Excel 或 Word 文件層級專案時，您可以用程式設計方式在執行階段中加入這些控制項，或您可以使用 Visual Studio 設計工具，在設計階段中將這些控制項加入專案的文件或活頁簿。

## <a name="in-this-section"></a>本節內容
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)

 描述主項目和主控制項的功能，包含針對事件進行程式設計、將控制項繫結至資料，以及此控制項和原生物件的控制項有何不同。

- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

 描述當您在程式碼中使用主項目和主控制項時，可能會遇到的問題。

- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)

 提供使用 Excel 和 Word 文件上的 Windows Forms 控制項和 Windows Forms 上的控制項有何差異的詳細資訊。

- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)

 描述如何加入 Windows Forms 控制項和主控制項至 Word 和 Excel 文件，並描述這些控制項如何在文件中保存的限制。

## <a name="related-sections"></a>相關章節
- [Office UI 自訂](../vsto/office-ui-customization.md)

 提供以不同方式來使用 Visual Studio 自訂 Microsoft Office 應用程式 UI 的詳細資訊。

- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)

 描述如何將資料繫結至文件中的主控制項，藉此在 Word 和 Excel 文件中顯示資料。
