---
title: 如何： 設定 Office 方案的組態資訊
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 87f50856439158d6d931b519fb35e98970ef7d58
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35670855"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>如何： 設定 Office 方案的組態資訊
  您可以使用組態檔來設定 Office 方案特有的設定。 您可以指定組件繫結原則、 遠端處理物件、 偵錯和追蹤設定等設定。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>若要新增至您的 Office 專案的組態檔  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
2.  在 **分類**窗格中，按一下**一般**。  
  
3.  在 **範本**窗格中，選取**應用程式組態檔**。  
  
4.  在 **名稱**方塊中，輸入相同的名稱做為組件，再加上副檔名 *.config*。例如，呼叫 Excel 專案的組件的組態檔*ExcelWorkbook1.dll*就會命名為*ExcelWorkbook1.dll.config*。  
  
5.  按一下 [加入] 。  
  
6.  建立您的組態檔，根據應用程式組態檔結構描述。 如需詳細資訊，請參閱 <<c0> [ 適用於.NET Framework 的組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)。  
  
 沒有任何特殊的考量，如 Office 專案中使用組態檔。  
  
## <a name="see-also"></a>另請參閱  
 [適用於.NET Framework 的組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  