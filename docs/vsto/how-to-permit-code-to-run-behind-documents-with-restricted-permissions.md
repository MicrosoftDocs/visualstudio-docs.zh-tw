---
title: 允許程式碼在具有限制許可權的檔背後執行
description: 瞭解如何使用 Visual Studio 中的 Office 程式開發工具，允許程式碼在具有限制許可權的檔後方執行。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1a65e99712658567996598d2190447ff09cf9b05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888884"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>如何：允許程式碼在具有限制許可權的檔背後執行
  您可以使用 Microsoft Office 的資訊 Rights Management (IRM) 功能來限制檔或活頁簿的許可權。 根據預設，不允許執行受限制 Microsoft Office Word 檔或 Microsoft Office Excel 活頁簿中的程式碼。 您可以變更預設值，讓您的 managed 程式碼延伸模組可以存取物件模型，而且您的解決方案將會運作。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您必須是檔或活頁簿的作者，或是具有「完全控制」存取權限，才能變更許可權設定。

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>允許程式碼在具有限制許可權的檔背後執行

1. 在 Word 或 Excel 中開啟檔或活頁簿。

2. 按一下 [ **檔案** ] 索引標籤，指向 [ **準備**]，指向 [ **限制許可權**]，然後按一下 [ **限制存取**]。

   > [!NOTE]
   > 第一次使用時，系統會提示您安裝 Windows Rights Management 用戶端。 安裝用戶端之後，您可能需要重複這些步驟。

3. 在 [ **許可權** ] 對話方塊中，選取 [ **限制此檔的許可權**]，然後按一下 [ **其他選項**]。

4. 在 [ **使用者的其他許可權**] 下，選取 [以程式設計 **方式存取內容**]。

   Word 或 Excel 將允許以程式設計方式存取物件模型。

## <a name="see-also"></a>另請參閱
- [資訊版權管理和 managed 程式碼延伸模組總覽](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [檔層級方案的檔案保護](../vsto/document-protection-in-document-level-solutions.md)
- [Office 檔上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
