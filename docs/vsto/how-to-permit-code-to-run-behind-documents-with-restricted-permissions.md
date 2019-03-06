---
title: HOW TO：允許程式碼的文件背後執行以限制權限
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be5afe96af1baa615e5000a6c1a19b543f3c89c5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637655"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>HOW TO：允許程式碼的文件背後執行以限制權限
  您可以使用 Microsoft Office 的資訊版權管理 (IRM) 功能的文件或活頁簿限制權限。 根據預設，受限制的 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿背後的程式碼不允許執行。 您可以變更預設值，以便您的 managed 程式碼擴充功能可以存取物件模型中，而且您的解決方案會正常運作。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您必須是文件或活頁簿的作者，或具有完整控制存取權可以變更權限設定。

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>若要允許程式碼的文件背後執行以限制權限

1. 在 Word 或 Excel 中開啟的文件或活頁簿。

2. 按一下 **檔案**索引標籤上，指向**準備**，指向**限制權限**，然後按一下**限制存取**。

   > [!NOTE]
   >  在第一次使用時，系統會提示您安裝 Windows 的 Rights Management 用戶端。 在安裝用戶端之後，您可能需要重複這些步驟。

3. 在 **權限**對話方塊中，選取**限制此文件的權限**，然後按一下 **更多選項**。

4. 底下**額外的權限的使用者**，選取**以程式設計方式存取內容**。

   Word 或 Excel，將允許以程式設計方式存取物件模型。

## <a name="see-also"></a>另請參閱
- [資訊版權管理和 managed 程式碼延伸模組概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)
- [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
