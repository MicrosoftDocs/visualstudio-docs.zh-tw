---
title: HOW TO：當地語系化程式碼 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbcf07b462e280f522741b8329d34c2907f5b454
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066282"
---
# <a name="how-to-localize-code"></a>HOW TO：當地語系化程式碼
  未當地語系化的程式碼使用硬式編碼的字串值。 若要當地語系化字串，取代呼叫<xref:System.Web.HttpContext.GetGlobalResourceObject%2A>，這是參考當地語系化的資源的方法。

## <a name="localize-code"></a>當地語系化程式碼

#### <a name="to-localize-code"></a>若要當地語系化程式碼

1. 在 **方案總管**，開啟專案項目的捷徑功能表，然後選擇**新增** > **模組**。

     選擇**資源檔**範本。

    > [!NOTE]
    >  請務必將資源檔新增至 SharePoint 專案項目，以便提供的部署類型屬性。 在此程序稍後需要此屬性。

2. 提供的預設語言資源檔案加上您所選擇的名稱 *.resx*擴充功能，例如*MyAppResources.resx*。

3. 重複步驟 1 和 2，將個別資源檔加入至 SharePoint 專案項目：每個當地語系化語言擁有一個資源檔。

     使用相同的基底名稱，每個當地語系化的資源檔案，但新增文化特性 id。 例如，名稱在德文當地語系化資源*為 MyAppResources.de-DE.resx*。

4. 開啟每個資源檔並加入當地語系化的字串。 在每個檔案中使用相同的字串 ID。

5. 值變更**部署類型**屬性的每個資源檔**AppGlobalResource** ，讓每個檔案部署至伺服器的 App_GlobalResources 資料夾。

6. 保留值**建置動作**屬性為每個檔案**內嵌資源**。

     將內嵌資源編譯為專案的 DLL。

7. 建置專案，以建立資源附屬 Dll。

8. 在  **Package Designer**，選擇**進階**索引標籤，然後再加入附屬組件。

9. 在 **位置**方塊中，前面加上文化特性 ID 資料夾位置路徑，例如*DE-DE\\\<專案項目名稱 >.resources.dll*。

10. 如果您的方案已經參考 System.Web 組件，將參考加入它，並在程式碼中加入指示詞<xref:System.Web>。

11. 找出程式碼中所有使用者可見的硬式編碼字串，例如 UI 文字、錯誤和訊息文字。 使用下列語法呼叫 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法取代這些字串：

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. 選擇**F5**鍵，建置並執行應用程式。

13. 在 SharePoint 中，變更預設的顯示語言。

     當地語系化的字串會出現在應用程式。 若要顯示當地語系化的資源，請在 SharePoint 伺服器必須符合資源檔的文化特性的語言套件安裝。

## <a name="see-also"></a>另請參閱
- [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)
- [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)
- [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)
- [如何：加入資源檔](../sharepoint/how-to-add-a-resource-file.md)
