---
title: 如何：當地語系化 ASPX 標記 |Microsoft Docs
description: 瞭解如何將硬式編碼的字串值取代為參考當地語系化資源的運算式，以當地語系化 SharePoint 中的 ASPX 標記。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1876e06348d60f8a960b352525fd72ad06795101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931730"
---
# <a name="how-to-localize-aspx-markup"></a>如何：當地語系化 ASPX 標記
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ( .aspx) 頁面通常會使用硬式編碼的字串值。 若要將這些字串當地語系化，請將它們取代為參考當地語系化資源的運算式。

## <a name="localize-aspx-markup"></a>將 ASPX 標記當地語系化

#### <a name="to-localize-aspx-markup"></a>當地語系化 ASPX 標記

1. 新增個別的資源檔：一個用於預設語言，另一個用於每個當地語系化的語言。

     如果您只是要當地語系化標記而非程式碼，請加入全域資源檔專案專案。 如果您要當地語系化程式碼和標記，請新增資源檔專案專案。

    1. 若要加入全域資源檔，請在 **方案總管** 中開啟 SharePoint 專案專案的快捷方式功能表，然後選擇 [**加入**  >  **新專案**]。 在 [SharePoint **2010** ] 節點下，選擇 [ **全域資源檔** ] 範本。

    2. 若要加入資源檔，請在 **方案總管** 中開啟 SharePoint 專案專案的快捷方式功能表，然後選擇 [**加入**  >  **新專案**]。 在 [ **Visual Basic** ] 或 [ **Visual c #** ] 節點下，選擇 [ **資源檔** ] 範本。

    > [!NOTE]
    > 請務必將資源檔新增至 SharePoint 專案專案，以啟用 [部署類型] 屬性。 稍後在此程式中需要這個屬性。 如果您的方案沒有 SharePoint 專案專案，您可以加入空白的 SharePoint 專案，並移除其預設的 *Elements.xml* 檔案。

2. 為預設語言資源檔提供您選擇的名稱，並附加 *.resx* 副檔名，例如 MyAppResources .resx。 針對每個當地語系化的資源檔使用相同的基底名稱，但是會加上文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，將德國當地語系化的資源命名為 *MyAppResources.de-de .resx*。

3. 將每個資源檔的 [ **部署類型** ] 屬性值變更為 [ **[appglobalresource** ]，使其部署到伺服器的 App_GlobalResources 資料夾。

4. 如果您使用資源來當地語系化除了 ASPX 標記之外的程式碼，請將每個檔案的 [ **組建動作** ] 屬性值保留為 [ **內嵌資源**]。 如果您只使用資源檔來當地語系化標記，您可以選擇性地將檔案的屬性值變更為 **Content**。 如需詳細資訊，請參閱 [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。

5. 開啟每個資源檔並新增當地語系化的字串，並在每個檔案中使用相同的字串識別碼。

6. 在 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ASPX 頁面或控制項的標記中，將硬式編碼的字串取代為使用下列格式的值：

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     例如，若要將應用程式頁面上標籤控制項的文字當地語系化，您可以變更：

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     to

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. 選擇 **F5** 鍵來建立和執行應用程式。

8. 在 SharePoint 中，從預設值變更顯示語言。

     當地語系化的字串會出現在應用程式中。 若要顯示當地語系化的資源，SharePoint 伺服器必須安裝符合資源檔文化特性的語言套件。

## <a name="see-also"></a>另請參閱
- [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)
- [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)
- [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)
- [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)
