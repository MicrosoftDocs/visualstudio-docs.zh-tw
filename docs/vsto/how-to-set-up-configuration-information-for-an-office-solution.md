---
title: "如何： 設定 Office 方案的組態資訊 |Microsoft 文件"
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
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8c2e0a904ad3cdbef3e70072d263cc26274de52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>如何：設定 Office 方案的組態資訊
  您可以使用組態檔來設定 Office 方案特有的設定。 您可以指定組件繫結原則、 遠端處理物件、 偵錯和追蹤設定等設定。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>若要將組態檔加入至您的 Office 專案  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
2.  在**類別**] 窗格中，按一下 [**一般**。  
  
3.  在**範本**窗格中，選取**應用程式組態檔**。  
  
4.  在**名稱**方塊中，為組件加上副檔名.config 輸入相同的名稱。例如，呼叫 ExcelWorkbook1.dll Excel 專案組件的組態檔就會命名為 ExcelWorkbook1.dll.config。  
  
5.  按一下 [加入] 。  
  
6.  建立您根據應用程式組態檔結構描述的組態檔。 如需詳細資訊，請參閱[適用於.NET Framework 組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)。  
  
 沒有任何特殊考量的 Office 專案中使用組態檔。  
  
## <a name="see-also"></a>另請參閱  
 [適用於.NET Framework 組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  