---
title: HOW TO：匯入的主版頁面或佈景主題 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1be553955abdc42c2a9b4d09ff857e9236b1a002
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081902"
---
# <a name="how-to-import-a-master-page-or-theme"></a>HOW TO：匯入的主版頁面或佈景主題
  您可以讓頁面在您的 SharePoint 網站上一致的外觀建立並使用主版頁面和主題。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 未提供範本，針對這些項目，但是您可以在 SharePoint Designer 中建立它們，並再將其匯入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱[建置組塊：頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095)Microsoft 網站上。

### <a name="to-import-a-master-page-or-theme"></a>若要匯入的主版頁面或佈景主題

1. 在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，建立或開啟 SharePoint 專案。

     如需有關如何建立 SharePoint 專案的資訊，請參閱 < [SharePoint 專案和專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在功能表列中，選擇 [專案] > [加入新項目]。

3. 在**加入新項目**對話方塊方塊中，展開**SharePoint**節點，然後選擇**2010年**節點。

4. 在 SharePoint 範本清單中，選擇**模組**範本，然後指定模組的名稱。

     模組包含檔案 （例如，主版頁面或佈景主題檔案），以部署至您在 SharePoint 中指定的位置。

5. 在模組中，刪除 預設的檔案，名為*Sample.txt*。

6. 選擇 [模組] 節點。

7. 在功能表列上選擇 **專案** > **加入現有項目**，然後選擇 主版頁面或佈景主題檔案。

     主版頁面檔案具有.master 副檔名，而且佈景主題檔案副檔名為.thmx。

8. 如果您加入主版頁面，變更其**部署衝突解決**設為**自動**中模組的屬性。

    > [!NOTE]
    >  主版頁面的名稱是否與現有的主版頁面標示為預設主版頁面或自訂主版頁面的名稱相同，則可能會發生錯誤。 如需有關如何解決此問題的資訊，請參閱[逐步解說：匯入自訂主版頁面和網站頁面的映像](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)。

9. 在模組中，開啟*Elements.xml*。

     您必須更新*Elements.xml*来參考的主版頁面或您加入的佈景主題檔案。

10. 主版頁面中，請以下列標記取代現有的模組標記。

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     佈景主題，請以下列標記取代現有的模組標記。

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     請務必使用模組的主版頁面或佈景主題的實際名稱取代預留位置值。

     屬性`Type="GhostableInLibrary"`表示的項目會加入至內容資料庫，而`Url`模組的屬性會指定如何將檔案儲存在 SharePoint 內容資料庫。

11. 若要變更在主版頁面中，部署範圍內**方案總管**，開啟功能設計工具中的功能檔案，然後選擇 新的部署範圍，從**範圍**清單。

     值為**Web**表示主版頁面只適用於目前專案中指定的網站。 值為**站台**表示主版頁面套用至目前網站集合，其中包括所有子網站和根網站。 不適用於其他值。

    > [!NOTE]
    >  佈景主題套用至網站集合層級，因為我們建議您不要設定佈景主題的範圍到任何項目以外**站台**。 如果在子站台會使用佈景主題，可能會發生錯誤。

12. 在功能表列上選擇 **建置** > **部署方案**。

13. 若要確認是否已正確部署檔案，開啟 SharePoint 網站中，選擇**站台動作**功能表上，選擇**站台設定**命令，然後再選擇 **主版頁面**連結或**佈景主題**連結。

     主版頁面或佈景主題的清單隨即出現，並包含的主版頁面或佈景主題，您匯入。

## <a name="see-also"></a>另請參閱
- [主版頁面](http://go.microsoft.com/fwlink/?LinkId=184955)
- [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [建立 SharePoint 頁面](../sharepoint/creating-pages-for-sharepoint.md)
- [使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)
