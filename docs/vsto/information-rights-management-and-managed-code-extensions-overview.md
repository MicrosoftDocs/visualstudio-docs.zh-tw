---
title: 資訊版權管理和 managed 程式碼延伸模組概觀
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
ms.openlocfilehash: dbe61b1b9ca43b9c3e4e6d5bcdf82dd2b5e1438a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876040"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>資訊版權管理和 managed 程式碼延伸模組概觀
  Microsoft Office Word 和 Microsoft Office Excel 提供的資訊版權管理 (IRM)，可協助您防止未經授權的人員檢視或變更敏感資訊的功能。 如需資訊版權管理的運作方式的詳細資訊，請參閱特定 Office 應用程式中的說明。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>執行文件背後的程式碼，以限制權限  
 如果您的方案包含文件或活頁簿使用 IRM，根據預設，Word 和 Excel 不允許執行任何程式碼。 如果您是文件的作者，或具有完整控制存取，您可以變更預設值，讓您的方案運作。 如需詳細資訊，請參閱[＜How to：允許程式碼的文件背後執行以限制使用權限](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
 IRM 會防止使用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>擷取或操作文件中快取的資料。  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>限制使用 managed 程式碼擴充功能的文件的權限的使用者  
 在您的方案中有完整控制存取權的文件或活頁簿的任何人可以使用 IRM 限制的權限。 比方說，如果使用者在會計部門中使用會自動填入資料庫中的資料在工作表的解決方案，該使用者可能要允許僅變更中所屬的部門的人員存取權和讀取權限給其他人。 當使用者加入受限制的權限時，根據預設，工作表背後的程式碼無法執行，而且在工作表不會填入資料。  
  
 若要修正此問題，完全控制存取的文件或活頁簿的人必須變更預設權限設定，允許以程式設計方式存取物件模型。 如需詳細資訊，請參閱[＜How to：允許程式碼的文件背後執行以限制使用權限](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
