---
title: "如何： 允許程式碼在具有限制權限的文件背後執行 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09336e72cc9e1e1bc0a407314d4fa9fd6bc2a2c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>如何：允許程式碼在具有限制使用權限的文件背後執行
  若要限制的文件或活頁簿的權限，您可以使用 Microsoft Office 的資訊版權管理 (IRM) 功能。 根據預設，受限制的 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿背後的程式碼不允許執行。 您可以變更預設值，使您的 managed 程式碼擴充功能可以存取的物件模型，您的方案可以。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您必須是文件或活頁簿的作者，或具有完整控制存取權可以變更權限設定。  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>若要允許程式碼以有限權限的文件背後執行  
  
1.  在 Word 或 Excel 中開啟的文件或活頁簿。  
  
2.  按一下**檔案**索引標籤上，指向 **準備**，指向 **限制權限**，然後按一下 **限制存取**。  
  
    > [!NOTE]  
    >  在第一次使用時，系統會提示您安裝 Windows 的 Rights Management 用戶端。 安裝用戶端之後，您可能需要重複步驟。  
  
3.  在**權限**對話方塊中，選取**限制此文件的權限**，然後按一下 **更多選項**。  
  
4.  在下**其他使用者的權限**，選取**以程式設計方式存取內容**。  
  
 Word 或 Excel 會允許以程式設計方式存取物件模型。  
  
## <a name="see-also"></a>請參閱  
 [資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  