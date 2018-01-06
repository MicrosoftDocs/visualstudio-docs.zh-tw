---
title: "文件保護文件層級方案中的 |Microsoft 文件"
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
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cb0ccb9369c3430cf04e7e7c6b62335721e8005f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="document-protection-in-document-level-solutions"></a>文件層級方案的文件保護
  您可以使用文件層級專案中的 Microsoft Office Word 和 Microsoft Office Excel 的保護功能。 這些功能會封鎖未經授權的使用者變更受保護的文件部分。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 使用 Excel，您可以開啟保護開啟和關閉設計工具中開啟活頁簿時。 使用 Word，您可以開啟保護只在設計工具外。 在執行階段，您可以啟用或停用保護，以程式設計方式針對 Word 和 Excel。  
  
 所有控制項設計工具中開啟文件上啟用文件保護時，會都移除從**工具箱**或會變成無法使用，您無法將任何項目從**資料來源**文件視窗。  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument 和受保護的文件  
 如果文件受到保護，無法存取資料快取從外部文件。 您無法使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別來擷取或操作資料快取的受保護的文件，或使用其他方法的<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>類別。  
  
## <a name="word-document-protection-in-the-designer"></a>在設計工具中的 Word 文件保護  
 如果在 Visual Studio 中開啟時，您可以加入至 Word 文件或範本的保護，您無法開始強制執行在設計工具中的保護。 文件是設計模式，但它是在 Visual Studio 中，開啟且必須在執行模式之前，您可以開始強制執行保護。  
  
 不過，如果您建立使用現有的 Word 文件已啟用保護的專案，文件會受到保護，同時設計工具中開啟。 您無法編輯受保護的文件中，部分，但您仍然可以撰寫程式碼在程式碼編輯器來自動化文件。 您也無法建置專案時如果在 Visual Studio 中開啟文件時，會啟用保護。  
  
 您可以關閉保護文件開啟時在設計工具，讓您能夠編輯文件，並建置專案。 您無法關閉設計工具中複製的保護時進行偵錯。在偵錯期間開啟的文件是從設計工具 （輸出複本會儲存在 \bin 目錄，適用於 Visual Basic 和 C# 的 \bin\debug 目錄） 中開啟單一另一份複本。  
  
 您可以啟用保護在複本上的關閉 Visual Studio 中的專案、 開啟位於專案目錄中，文件的複本和保護開啟在設計工具中開啟的文件。  
  
## <a name="enforcing-word-document-protection-on-build"></a>強制執行組建的 Word 文件保護  
 Visual Studio 啟動強制執行保護的 Word 文件和範本建置程序期間，讓文件開啟時進行偵錯時，會啟用保護。 文件受到使用空白的密碼。  
  
 保護已啟用在建置期間，如果文件中的程式碼<xref:Microsoft.Office.Tools.Word.Document.Startup>可能造成例外狀況，或變更應用程式行為的事件，此程式碼能夠偵錯正確。 如果文件開啟之後，您可以啟用保護，無法偵錯或測試初始化程式碼。  
  
## <a name="setting-the-password"></a>設定密碼  
 Visual Studio 會自動啟用保護，但根據預設會提供任何密碼。 如果您想要有密碼保護文件時，您必須新增它，才能在您部署方案。 新增密碼可讓授權的使用者文件; 移除保護沒有密碼便無法輕易移除保護。 如需設定密碼的詳細資訊，請參閱特定 Office 應用程式中的說明。  
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式保護文件及部分的文件](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [如何： 允許程式碼在具有限制權限的文件背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  