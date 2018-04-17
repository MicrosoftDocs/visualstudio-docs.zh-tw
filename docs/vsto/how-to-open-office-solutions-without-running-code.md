---
title: 如何： 開啟 Office 方案，但不執行程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86a44d2a6c82f65d91c558c76743a8fbbd2fa1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-open-office-solutions-without-running-code"></a>如何：以不執行程式碼的方式開啟 Office 方案
  建立具有 managed 程式碼擴充的 Microsoft Office 方案時仍會執行使用者的 Office 應用程式中的安全性設定設定為高。 這是因為.NET 組件程式碼安全性由 Microsoft.NET Framework 中，不是由 Microsoft Office 管理。  
  
 不過，但有些的時候您可能想要開啟的文件，但不執行程式碼。 例如，文件開啟時執行的程式碼可能修改的內容中，但您想要更新的文件之前的程式碼變更並尋找的方式。 您可能想要接收文件的特定資訊的某人，或不想讓程式碼來執行和可能修改的內容。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有幾種方式開啟文件或不執行組件程式碼中包含 managed 程式碼擴充的活頁簿。  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>若要使用 SHIFT 鍵，以略過組件  
  
-   開啟文件和活頁簿**檔案**功能表上，按住 SHIFT 鍵可防止 Word 和 Excel 文件開啟時引發的事件初始化。  
  
    > [!NOTE]  
    >  如果您開啟文件或活頁簿**入門**工作窗格中，按住 shift 鍵不略過程式碼。 此外，按住 shift 鍵不會阻止事件後的文件開啟時引發。  
  
     這個方法很有用，如果您想要開啟的文件不會執行，而且第一次修改文件的程式碼進行變更。  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>若要重新命名或移除它略過組件  
  
-   如果您有必要的權限的組件所在的電腦上，您可以重新命名或移除組件，因此文件或活頁簿將無法找到它。 這會導致每次開啟 Office 文件時都會引發錯誤。  
  
     如果方案由多人使用，這個方法會防止執行所有這些方案。 如果問題位於程式碼或參考的伺服器，而且您想要停止執行它的所有使用者，這可能會很有用。  
  
## <a name="see-also"></a>另請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  