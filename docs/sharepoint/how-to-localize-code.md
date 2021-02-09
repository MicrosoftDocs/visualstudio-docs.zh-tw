---
title: 如何：當地語系化程式碼 |Microsoft Docs
description: 瞭解如何使用 GetGlobalResourceObject 的呼叫（參考當地語系化資源的方法）來取代硬式編碼字串，以當地語系化 SharePoint 中的程式碼。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e76b8cfb2e9fcb513905918bd4ae87524078f6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931639"
---
# <a name="how-to-localize-code"></a>如何：當地語系化程式碼
  未當地語系化程式碼會使用硬式編碼的字串值。 若要將程式碼字串當地語系化，請將它們取代為的呼叫 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> ，也就是參考當地語系化資源的方法。

## <a name="localize-code"></a>當地語系化程式碼

#### <a name="to-localize-code"></a>當地語系化程式碼

1. 在 **方案總管** 中，開啟專案專案的快捷方式功能表，然後選擇 [**加入**  >  **模組**]。

     選擇 [ **資源檔** ] 範本。

    > [!NOTE]
    > 請務必將資源檔新增至 SharePoint 專案專案，以便使用 [部署類型] 屬性。 稍後在此程式中需要這個屬性。

2. 為預設語言資源檔提供您選擇的名稱，並附加 *.resx* 副檔名，例如 *MyAppResources .resx*。

3. 重複步驟 1 和 2，將個別資源檔加入至 SharePoint 專案項目：每個當地語系化語言擁有一個資源檔。

     針對每個當地語系化的資源檔使用相同的基底名稱，但新增文化特性識別碼。 例如，將德國當地語系化的資源命名為 *MyAppResources.de-de .resx*。

4. 開啟每個資源檔並新增當地語系化的字串。 在每個檔案中使用相同的字串 ID。

5. 將每個資源檔的 [ **部署類型** ] 屬性值變更為 [ **[appglobalresource** ]，使每個檔案都部署到伺服器的 App_GlobalResources 資料夾。

6. 將每個檔案的 [ **組建動作** ] 屬性值保留為 [ **內嵌資源**]。

     將內嵌資源編譯為專案的 DLL。

7. 建立專案以建立資源附屬 Dll。

8. 在 **封裝設計** 工具中，選擇 [ **Advanced** ] 索引標籤，然後加入附屬元件。

9. 在 [**位置**] 方塊中，于位置路徑前面加上文化特性識別碼資料夾，例如 *de \\ \<Project Item Name>.resources.dll*。

10. 如果您的方案尚未參考 system.string 元件，請在其中加入參考，然後在您的程式碼中加入指示詞 <xref:System.Web> 。

11. 找出程式碼中所有使用者可見的硬式編碼字串，例如 UI 文字、錯誤和訊息文字。 使用下列語法呼叫 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法取代這些字串：

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. 選擇 **F5** 鍵來建立和執行應用程式。

13. 在 SharePoint 中，從預設值變更顯示語言。

     當地語系化的字串會出現在應用程式中。 若要顯示當地語系化的資源，SharePoint 伺服器必須安裝符合資源檔文化特性的語言套件。

## <a name="see-also"></a>另請參閱
- [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)
- [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)
- [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)
- [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)
