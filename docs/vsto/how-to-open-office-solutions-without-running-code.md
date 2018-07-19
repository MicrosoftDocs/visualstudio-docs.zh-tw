---
title: 如何： 開啟的 Office 方案，而不需執行的程式碼
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
ms.openlocfilehash: f7ced7b38a4f32d96b397e7f9eebb1d40be03ae3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254984"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>如何： 開啟的 Office 方案，而不需執行的程式碼
  即使使用者的 Office 應用程式中的安全性設定設為 「 高 」，就會執行使用 managed 程式碼擴充功能所建立的 Microsoft Office 方案。 這是因為.NET 組件程式碼安全性由 Microsoft.NET Framework 中，不是由 Microsoft Office。  
  
 不過，有一些您可能的想来開啟的文件，而不需執行的程式碼。 例如，文件開啟時執行程式碼可能修改的內容中，但您想要更新的文件的外觀之前的程式碼變更它的方式。 或要在其中的特定資訊的文件傳送給某個成員，並不想讓程式碼以執行，並可能修改的內容。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有幾種方式開啟文件或活頁簿，其中包含 managed 程式碼擴充功能，而不需執行的組譯碼。  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>若要使用 Shift 鍵，以略過組件  
  
-   開啟文件和活頁簿**檔案**按住功能表**Shift**防止 Word 和 Excel 文件開啟時，引發初始化事件的索引鍵。  
  
    > [!NOTE]  
    >  如果您開啟的文件或活頁簿**快速入門**工作窗格中，按住**Shift**不略過程式碼。 此外，按住 shift 鍵無法防止事件引發之後已開啟的文件。  
  
     這個方法很有用，如果您想要開啟的文件，而不需要執行，而且第一次修改文件的程式碼進行變更。  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>略過組件，重新命名或移除方法  
  
-   如果您有必要的權限的組件所在的電腦上時，您可以重新命名或移除組件，文件或活頁簿無法找到它。 這會導致每次開啟 Office 文件時引發錯誤。  
  
     如果方案由多人，這個方法會防止對其執行方案。 如果問題位於程式碼或參考的伺服器，而且您想要停止執行中的所有使用者，這可以是很有用。  
  
## <a name="see-also"></a>另請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [在 Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  