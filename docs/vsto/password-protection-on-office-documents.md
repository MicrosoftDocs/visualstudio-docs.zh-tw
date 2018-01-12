---
title: "Office 文件上的密碼保護 |Microsoft 文件"
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
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 52cadcec85580a9214da844bf887323227490f22
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="password-protection-on-office-documents"></a>Office 文件上的密碼保護
  很可能您的 Microsoft Office Word 文件和 Microsoft Office Excel 活頁簿上設定密碼，使其無法開啟不知道密碼的人。 此選項會稱為**密碼開啟**。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以建立文件層級專案中使用現有的文件和活頁簿包含**密碼開啟**啟用。 Visual Studio 中的行為是不同的 Word 和 Excel 文件有**密碼開啟**啟用。  
  
 如需啟用資訊**密碼開啟**，請參閱 Word 或 Excel 中的說明。  
  
## <a name="behavior-of-excel-and-word"></a>Excel 和 Word 的行為  
 每當您在具有 Visual Studio 中開啟 Excel 活頁簿**密碼開啟**啟用，Excel 會提示您輸入密碼。 當您建置方案時您會提示輸入密碼一次，因為在建置期間開啟文件。  
  
 第一次您開啟 Word 文件在具有 Visual Studio**密碼開啟**啟用，Word 會提示您輸入密碼。 在您成功輸入密碼之後,**密碼開啟**從文件中移除並開啟文件並不會再將要求輸入密碼。 如果您要在方案中的文件可以開啟要求密碼前的，您必須啟用**密碼開啟**在最後一個組建之後和您部署方案。  
  
## <a name="see-also"></a>請參閱  
 [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [如何： 允許程式碼在具有限制權限的文件背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  