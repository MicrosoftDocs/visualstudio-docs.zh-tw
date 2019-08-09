---
title: 資訊版權管理 & managed 程式碼擴充
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 753f3d2da201c67cd86c697eccf7580596a40d6e
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872056"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>資訊版權管理和 managed 程式碼延伸模組總覽
  Microsoft Office Word 和 Microsoft Office Excel 提供資訊 Rights Management (IRM), 這項功能可協助您防止未經授權的人員查看或改變機密資訊。 如需資訊 Rights Management 運作方式的詳細資訊, 請參閱特定 Office 應用程式中的說明。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>以受限制的許可權執行程式碼後置檔
 如果您的方案包含使用 IRM 的檔或活頁簿, 則 Word 和 Excel 預設不允許執行任何程式碼。 如果您是檔的作者或具有完整控制存取權, 您可以變更預設值, 讓您的方案能夠運作。 如需詳細資訊，請參閱[如何：允許程式碼在具有限制許可權](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)的檔背後執行。

 IRM 會防止使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>來取出或操作檔中快取的資料。

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>終端使用者限制使用 managed 程式碼擴充之檔的許可權
 對於您解決方案中的檔或活頁簿具有完整控制存取權的任何人, 都可以使用 IRM 來限制許可權。 例如, 如果會計部門的使用者所使用的解決方案會自動將資料庫中的資料填入工作表, 則該使用者可能只想要允許其部門中的人員進行變更存取, 並讀取其他人的存取權。 當使用者加入限制的許可權時, 工作表的後置程式碼預設無法執行, 而且工作表不會填入資料。

 若要修正此問題, 具有檔或活頁簿之完整控制存取權的人, 必須變更預設許可權設定, 以允許以程式設計方式存取物件模型。 如需詳細資訊，請參閱[如何：允許程式碼在具有限制許可權](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)的檔背後執行。

## <a name="see-also"></a>另請參閱
- [檔層級方案中的檔案保護](../vsto/document-protection-in-document-level-solutions.md)
- [Office 檔上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
