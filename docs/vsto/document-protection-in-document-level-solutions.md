---
title: 檔層級方案中的檔案保護
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a894f1e0fb9d5e9d55f46c442bc975de0bd900d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872076"
---
# <a name="document-protection-in-document-level-solutions"></a>檔層級方案中的檔案保護
  您可以在檔層級專案中使用 Microsoft Office Word 和 Microsoft Office Excel 的保護功能。 這些功能會封鎖未經授權的使用者對檔的受保護部分進行變更。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 使用 Excel, 您可以在設計工具中開啟活頁簿時開啟和關閉保護功能。 使用 Word, 您只能在設計工具外部開啟保護功能。 在執行時間, 您可以為 Word 和 Excel 以程式設計方式啟用或停用保護。

 在設計工具中開啟的檔上啟用檔案保護時, 會從 [**工具箱**] 移除所有控制項或使其無法使用, 而且您無法將任何專案從 [**資料來源**] 視窗拖曳至檔。

## <a name="serverdocument-and-protected-documents"></a>ServerDocument 和受保護的檔
 如果檔受到保護, 就無法從檔外部存取資料快取。 您無法使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別來抓取或操作受保護檔中快取的資料, 或使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別的其他方法。

## <a name="word-document-protection-in-the-designer"></a>設計工具中的 Word 檔案保護
 如果您在 Visual Studio 中開啟 Word 檔或範本的保護, 就無法開始在設計工具中強制執行保護。 當檔在 Visual Studio 中開啟時處於設計模式, 而且必須處於執行模式, 才能開始強制保護。

 不過, 如果您建立的專案使用已啟用保護的現有 Word 檔, 則在設計工具中開啟時, 檔會受到保護。 您無法編輯檔的受保護部分, 但您仍然可以在程式碼編輯器中撰寫程式碼, 以將檔自動化。 如果在 Visual Studio 中開啟檔時啟用保護, 您也無法建立專案。

 當檔在設計工具中開啟時, 您可以關閉保護功能, 讓您可以編輯檔並建立專案。 您無法在進行偵錯工具時, 關閉設計工具中的禁止複製;在偵錯工具期間開啟的檔與設計工具中開啟的複本不同 (輸出複本會儲存在 Visual Basic 的 *\bin*目錄中, 以及的 *\bin\debug*目錄C#)。

 您可以在 Visual Studio 中關閉專案、開啟專案目錄中的檔複本, 然後開啟 保護, 以在設計工具中開啟的檔複本上啟用保護。

## <a name="enforce-word-document-protection-on-build"></a>在組建上強制執行 Word 檔案保護
 Visual Studio 開始在建立程式期間強制執行 Word 檔和範本的保護, 以便在檔開啟以進行偵錯工具時啟用保護。 使用空白密碼來保護檔。

 在組建期間啟用保護, 如此一來, 如果檔<xref:Microsoft.Office.Tools.Word.Document.Startup>事件中的程式碼可能會造成例外狀況或變更應用程式的行為, 則可以正確地調試此程式碼。 如果您在開啟檔後啟用保護, 則無法對初始化程式碼進行調試或測試。

## <a name="setting-the-password"></a>設定密碼
 Visual Studio 會自動啟用保護, 但預設不會提供密碼。 如果您想要檔案保護具有密碼, 您必須先將它加入, 然後再部署您的方案。 新增密碼可讓您允許授權的使用者移除檔的保護;如果沒有密碼, 就無法輕易地移除保護。 如需設定密碼的詳細資訊, 請參閱特定 Office 應用程式中的說明。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式保護檔和檔的部分](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [資訊版權管理和 managed 程式碼延伸模組總覽](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 檔上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [如何：允許程式碼在具有限制許可權的檔背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
