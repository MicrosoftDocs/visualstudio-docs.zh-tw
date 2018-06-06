---
title: 在 Visual Studio 內使用 Office 功能
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a1db785b4758236c4a50e694d868cecc269324a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767503"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>在 Visual Studio 內使用 Office 功能
  當您建立的文件層級專案時，文件和相關聯的應用程式被裝載於 Visual Studio 供您設計並直接使用文件。 當您在 Microsoft Office，Visual Studio 中開啟應用程式時，它通常如預期般運作。 不過，某些應用程式是功能的不同或無法存取。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>文件保護  
 Microsoft Office Word 和 Microsoft Office Excel 提供文件保護功能，可讓您在專案中。 不過，如果文件保護已啟用 Visual Studio 中開啟文件時，它可以防止您進行一些設計變更。 如需詳細資訊，請參閱[文件保護文件層級方案中的](../vsto/document-protection-in-document-level-solutions.md)。  
  
## <a name="information-rights-management"></a>資訊版權管理  
 Microsoft Office Word 和 Microsoft Office Excel 中使用資訊版權管理 (IRM)。 IRM 可以協助防止未經授權的人員檢視或變更敏感資訊。 不過，IRM 也可以讓您的程式碼無法執行。 如需詳細資訊，請參閱[資訊版權管理和 managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)。  
  
## <a name="password-protection"></a>密碼保護  
 可以設定 Microsoft Office Word 文件和 Microsoft Office Excel 活頁簿，使它們無法開啟不知道密碼的人。 密碼保護 Word 和 Excel 中以不同方式處理，而且可能影響您的開發程序。 如需詳細資訊，請參閱[Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [資訊版權管理和 managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [如何： 開啟 Office 方案，但不執行程式碼](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  