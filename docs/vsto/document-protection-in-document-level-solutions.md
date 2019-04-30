---
title: 在文件層級方案中的文件保護
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
ms.openlocfilehash: b6cc01c6506c4a3fca85029a8dcaf08607427ea4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956201"
---
# <a name="document-protection-in-document-level-solutions"></a>在文件層級方案中的文件保護
  您可以使用文件層級專案中的 Microsoft Office Word 和 Microsoft Office Excel 的保護功能。 這些功能會封鎖未經授權的使用者對受保護的文件的組件中的變更。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 使用 Excel，您可以開啟保護開啟和關閉設計工具中開啟活頁簿時。 使用 Word，您可以開啟保護只能在設計工具之外。 在執行階段，您可以啟用或停用保護，以程式設計方式針對 Word 和 Excel。

 從設計工具中開啟的文件上啟用文件保護時，會移除所有的控制項**工具箱**進行無法使用，或您無法將任何項目從**Zdroje dat**文件視窗。

## <a name="serverdocument-and-protected-documents"></a>ServerDocument 和受保護的文件
 如果文件受到保護，無法存取的資料快取從外部文件。 您無法使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別來擷取或操作中受保護的文件中，快取的資料，或使用其他方法<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>類別。

## <a name="word-document-protection-in-the-designer"></a>在設計工具中的 Word 文件保護
 如果在 Visual Studio 中開啟時，您可以新增至 Word 文件或範本的保護，您無法啟動強制執行設計工具中的保護。 文件處於設計模式，而是開啟在 Visual Studio 中，且必須在執行模式才能開始強制執行保護。

 不過，如果您建立使用已啟用保護的現有 Word 文件的專案，文件受到在設計工具中開啟。 您無法編輯文件中，受保護的部分，但您仍然可以撰寫程式碼來自動化文件中的程式碼編輯器。 您也無法建置專案如果 Visual Studio 中開啟文件時，會啟用保護。

 您可以關閉保護文件時在設計工具中開啟，以便您可以編輯文件，並建置專案。 您無法關閉設計工具中複製的保護時進行偵錯;在偵錯期間開啟的文件是從設計工具中開啟另一個複本 (輸出複本會儲存在*\bin* Visual Basic 中，目錄並*\bin\debug*目錄C#).

 您可以啟用保護複本會在設計工具中開啟關閉 Visual Studio 中的專案，開啟位於專案目錄中，文件的複本，然後開啟保護的文件。

## <a name="enforce-word-document-protection-on-build"></a>強制執行組建的 Word 文件保護
 Visual Studio 會啟動強制執行保護的 Word 文件與範本建置過程中，以便進行偵錯的文件開啟時，會啟用保護。 空白的密碼保護文件。

 保護已啟用在建置期間因此，如果文件中的程式碼<xref:Microsoft.Office.Tools.Word.Document.Startup>可能造成例外狀況，或變更應用程式行為的事件，此程式碼能夠偵錯正確。 如果在開啟文件之後，您就會啟用保護，就無法偵錯或測試初始化程式碼。

## <a name="setting-the-password"></a>設定密碼
 Visual Studio 會自動啟用保護，但預設會提供任何密碼。 如果您想要有密碼保護文件時，您必須新增它，然後再部署您的解決方案。 新增密碼可讓您可讓授權的使用者從 文件; 移除保護沒有使用密碼，無法輕鬆地移除保護。 如需設定密碼的詳細資訊，請參閱特定 Office 應用程式中的說明。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式保護文件和文件的部分](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [資訊版權管理和 managed 程式碼延伸模組概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [如何：允許程式碼的文件背後執行以限制權限](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
