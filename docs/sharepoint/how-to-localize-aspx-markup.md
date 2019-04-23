---
title: HOW TO：當地語系化 ASPX 標記 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25768f44ee51ee94d456d0652ab7575def3a259d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057564"
---
# <a name="how-to-localize-aspx-markup"></a>HOW TO：當地語系化 ASPX 標記
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (.aspx) 網頁通常會使用硬式編碼的字串值。 若要當地語系化這些字串，請將它們取代參考當地語系化的資源的運算式中。

## <a name="localize-aspx-markup"></a>當地語系化 ASPX 標記

#### <a name="to-localize-aspx-markup"></a>若要當地語系化 ASPX 標記

1. 新增個別的資源檔： 一個預設語言，另一個針對每個當地語系化語言。

     如果您在進行當地語系化只有 「 標記 」 和 「 不是程式碼，加入全域資源檔案的專案項目。 如果您在進行當地語系化程式碼和標記，將資源檔的專案項目。

    1. 若要加入全域資源檔案，請在**方案總管**，開啟 SharePoint 專案項目捷徑功能表，然後選擇**新增** > **新項目**。 在 SharePoint **2010年**節點，選擇**全域資源檔案**範本。

    2. 若要加入資源檔中**方案總管**，開啟 SharePoint 專案項目捷徑功能表，然後選擇**新增** > **新項目**。 之下**Visual Basic**或是**Visual C#** 節點，選擇 **資源檔**範本。

    > [!NOTE]
    >  請務必將資源檔新增至 SharePoint 專案項目，若要啟用的部署類型屬性。 在此程序稍後需要此屬性。 如果您的解決方案並沒有 SharePoint 專案項目，您可以新增空白的 SharePoint 專案，並移除其預設值*Elements.xml*檔案。

2. 提供的預設語言資源檔案加上您所選擇的名稱 *.resx*擴充功能，例如 MyAppResources.resx。 針對每個當地語系化的資源檔使用相同的基底名稱，但是會加上文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，名稱在德文當地語系化資源*為 MyAppResources.de-DE.resx*。

3. 值變更**部署類型**屬性的每個資源檔**AppGlobalResource**將部署至伺服器的 App_GlobalResources 資料夾。

4. 如果您要使用的資源，來當地語系化 ASPX 標記除了程式碼，將保留值**建置動作**屬性為每個檔案**內嵌資源**。 如果您只當地語系化標記會使用資源檔，您可以選擇性地變更之檔案的屬性值**內容**。 如需詳細資訊，請參閱 <<c0> [ 當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。

5. 開啟每個資源檔並加入當地語系化的字串，每個檔案中使用的相同字串 Id。

6. 在 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]標記 ASPX 頁面或控制項，以使用下列格式的值取代的硬式編碼的字串：

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     例如，若要當地語系化的文字標籤控制項的應用程式頁面上，您會變更：

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     設為

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. 選擇**F5**鍵，建置並執行應用程式。

8. 在 SharePoint 中，變更預設的顯示語言。

     當地語系化的字串會出現在應用程式。 若要顯示當地語系化的資源，請在 SharePoint 伺服器必須符合資源檔的文化特性的語言套件安裝。

## <a name="see-also"></a>另請參閱
- [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)
- [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)
- [如何：加入資源檔](../sharepoint/how-to-add-a-resource-file.md)
- [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)
