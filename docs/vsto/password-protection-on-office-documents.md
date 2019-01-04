---
title: Office 文件上的密碼保護
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4603a6f5722279ccdaf057d30d3bc6e911c4c47e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856997"
---
# <a name="password-protection-on-office-documents"></a>Office 文件上的密碼保護
  您可在您的 Microsoft Office Word 文件和 Microsoft Office Excel 活頁簿設定密碼，以便他們不知道密碼的其他人無法開啟。 此選項稱為**密碼開啟**。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以建立使用現有的文件和擁有的活頁簿的文件層級專案**密碼開啟**啟用。 在 Visual Studio 中的行為是不同的 Word 和 Excel 文件是否**密碼開啟**啟用。  
  
 如需啟用資訊**密碼開啟**，請參閱 Word 或 Excel 中的說明。  
  
## <a name="behavior-of-excel-and-word"></a>Excel 和 Word 的行為  
 每當您在具有 Visual Studio 中開啟 Excel 活頁簿**密碼開啟**啟用，Excel 會提示您輸入密碼。 當您建置方案時您將會提示輸入密碼同樣地，因為在建置期間開啟文件。  
  
 第一次您開啟 Word 文件中有的 Visual Studio**密碼開啟**啟用，Word 會提示您輸入密碼。 在您成功輸入密碼之後,**密碼開啟**從文件中移除並開啟文件將不再會要求輸入密碼。 如果您想在您的方案中的文件可以開啟要求密碼前的，您必須啟用**密碼開啟**您最終建置和部署解決方案之前。  
  
## <a name="see-also"></a>另請參閱  
 [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [資訊版權管理和 managed 程式碼延伸模組概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [如何：允許程式碼的文件背後執行以限制權限](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
