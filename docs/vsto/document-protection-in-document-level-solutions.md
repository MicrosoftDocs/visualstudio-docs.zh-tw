---
title: 檔層級方案的檔案保護
description: 瞭解如何在檔層級專案中使用 Microsoft Office Word 和 Microsoft Office Excel 的保護功能。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2898781a3603e7cb9582d246e4fa7edaaf6bddb9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846190"
---
# <a name="document-protection-in-document-level-solutions"></a>檔層級方案的檔案保護
  您可以在檔層級專案中，使用 Microsoft Office Word 和 Microsoft Office Excel 的保護功能。 這些功能會封鎖未經授權的使用者對檔的受保護部分進行變更。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 使用 Excel 時，您可以在設計工具中開啟活頁簿時開啟和關閉保護。 使用 Word，您只可以在設計工具外部開啟保護。 在執行時間，您可以針對 Word 和 Excel 以程式設計的方式啟用或停用保護。

 在設計工具中開啟的檔上啟用檔案保護時，會從 [ **工具箱** ] 中移除所有控制項或使其無法使用，而且您無法從 [ **資料來源** ] 視窗將任何內容拖曳至檔。

## <a name="serverdocument-and-protected-documents"></a>ServerDocument 和受保護的檔
 如果檔受到保護，就無法從檔外部存取資料快取。 您無法使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別來取出或操作受保護檔中快取的資料，或使用類別的其他方法 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 。

## <a name="word-document-protection-in-the-designer"></a>設計工具中的 Word 檔案保護
 如果您在 Visual Studio 中開啟 Word 檔或範本的保護，就無法在設計工具中開始強制執行保護。 當檔在 Visual Studio 中開啟時，它會處於設計模式，而且必須處於執行模式，才能開始強制執行保護。

 但是，如果您建立的專案會使用已啟用保護的現有 Word 檔，在設計工具中開啟檔時就會受到保護。 您無法編輯檔的受保護部分，但是您仍然可以在程式碼編輯器中撰寫程式碼，以自動化檔。 當您在 Visual Studio 中開啟檔時，如果已啟用保護，您也無法建立專案。

 當檔在設計工具中開啟時，您可以關閉保護，讓您可以編輯檔並建立專案。 在進行偵錯工具時，您無法在設計工具中關閉複本的保護;在偵錯工具中開啟的檔，與在設計工具中開啟的檔不同， (輸出複本儲存在 Visual Basic 的 *\bin* 目錄，以及 c # ) 的 *\bin\debug* 目錄。

 您可以藉由關閉 Visual Studio 中的專案、開啟專案目錄中檔的複本，以及開啟保護，在設計工具中開啟的檔複本上啟用保護。

## <a name="enforce-word-document-protection-on-build"></a>在組建上強制執行 Word 檔案保護
 Visual Studio 會在建立程式期間開始強制執行 Word 檔和範本的保護，因此當檔開啟以進行偵測時，便會啟用保護。 使用空白密碼保護檔。

 在組建期間啟用保護，如此一來，如果檔事件中的 <xref:Microsoft.Office.Tools.Word.Document.Startup> 程式碼可能會造成例外狀況或變更應用程式的行為，則可以正確地進行程式碼的偵錯工具。 如果您在檔開啟後啟用保護，就無法進行程式碼的調試或測試。

## <a name="setting-the-password"></a>設定密碼
 Visual Studio 會自動啟用保護，但預設不會提供密碼。 如果您想要讓檔案保護擁有密碼，您必須在部署方案之前先新增密碼。 新增密碼可讓您讓授權使用者從檔中移除保護;如果沒有密碼，就無法輕易地移除保護。 如需設定密碼的詳細資訊，請參閱特定 Office 應用程式中的說明。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式保護檔及部分的檔](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [資訊版權管理和 managed 程式碼延伸模組總覽](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 檔上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [如何：允許程式碼在具有限制許可權的檔背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
