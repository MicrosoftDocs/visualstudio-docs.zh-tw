---
title: "如何： 當地語系化程式碼 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95c029a7a90283314bdded2a6beeb7f023d7e827
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-localize-code"></a>如何：當地語系化程式碼
  未當地語系化的程式碼會使用硬式編碼的字串值。 若要當地語系化程式碼的字串，它們取代成呼叫<xref:System.Web.HttpContext.GetGlobalResourceObject%2A>，這是參考的當地語系化的資源的方法。  
  
## <a name="localizing-code"></a>當地語系化程式碼  
  
#### <a name="to-localize-code"></a>若要當地語系化程式碼  
  
1.  在**方案總管 中**，開啟專案項目捷徑功能表，然後選擇**新增**，**模組**。  
  
     選擇**資源檔**範本。  
  
    > [!NOTE]  
    >  請務必將資源檔新增至 SharePoint 專案項目，以便部署類型屬性。 在此程序稍後需要這個屬性。  
  
2.  提供的預設語言資源檔案副檔名為.resx，例如 MyAppResources.resx 附加您選擇的名稱。  
  
3.  重複步驟 1 和 2，將個別資源檔加入至 SharePoint 專案項目：每個當地語系化語言擁有一個資源檔。  
  
     使用相同的基底名稱，針對每個當地語系化的資源檔，但是加入文化特性識別碼。 例如，命名為德文的當地語系化的資源 MyAppResources.de DE.resx。  
  
4.  開啟每個資源檔並加入當地語系化的字串。 在每個檔案中使用相同的字串 ID。  
  
5.  值變更**部署類型**屬性的每個資源檔**AppGlobalResource** ，讓每個檔案部署至伺服器的 App_GlobalResources 資料夾。  
  
6.  保留值**建置動作**屬性的每個檔案儲存為**內嵌資源**。  
  
     將內嵌資源編譯為專案的 DLL。  
  
7.  建置專案來建立資源的附屬 Dll。  
  
8.  在**封裝設計工具**，選擇**進階**索引標籤，然後再加入附屬組件。  
  
9. 在**位置**方塊中，在前面加上文化特性識別碼資料夾的位置路徑，例如 DE-DE\\*專案項目名稱*.resources.dll。  
  
10. 如果您的方案已經參考 System.Web 組件，加入的參考，並加入您的程式碼中的指示詞<xref:System.Web>。  
  
11. 找出程式碼中所有使用者可見的硬式編碼字串，例如 UI 文字、錯誤和訊息文字。 使用下列語法呼叫 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法取代這些字串：  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. 選擇 F5 鍵，建置並執行應用程式。  
  
13. 在 SharePoint 中，變更預設的顯示語言。  
  
     當地語系化的字串會出現在應用程式。 若要顯示當地語系化的資源，請在 SharePoint 伺服器必須符合資源檔的文化特性的語言套件安裝。  
  
## <a name="see-also"></a>請參閱  
 [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何： 當地語系化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何： 當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)  
  
  