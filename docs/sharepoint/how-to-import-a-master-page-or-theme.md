---
title: 如何：匯入主版頁面或主題 |Microsoft Docs
description: 在 SharePoint Designer 中建立主版頁面和主題的範本，然後匯入 Visual Studio，以一致的外觀提供 SharePoint 網站上的頁面。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 331ae3964de40e6590345aadae59776fe37f467a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913679"
---
# <a name="how-to-import-a-master-page-or-theme"></a>如何：匯入主版頁面或主題
  您可以建立和使用主版頁面和主題，讓 SharePoint 網站上的頁面保持一致的外觀。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不提供這些專案的範本，但是您可以在 SharePoint Designer 中建立它們，然後將它們匯入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 Microsoft 網站上的 [建立區塊：頁面和消費者介面](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) 。

### <a name="to-import-a-master-page-or-theme"></a>匯入主版頁面或主題

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，建立或開啟 SharePoint 專案。

     如需有關如何建立 SharePoint 專案的詳細資訊，請參閱 [sharepoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

3. 在 [ **加入新專案** ] 對話方塊中，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 SharePoint 範本清單中，選擇 [ **模組** ] 範本，然後指定模組的名稱。

     模組包含檔案 (例如，主版頁面或主題檔案) 部署至您在 SharePoint 中指定的位置。

5. 在模組中，刪除名為 *Sample.txt* 的預設檔案。

6. 選擇模組節點。

7. 在功能表列上，選擇 [**專案**  >  **加入現有專案**]，然後選擇主版頁面或主題檔案。

     主版頁面檔案的副檔名為 thmx，而主題檔案的副檔名為.。

8. 如果您已新增主版頁面，請在模組的屬性中將其 **部署衝突解決** 設定變更為 [ **自動** ]。

    > [!NOTE]
    > 如果主版頁面的名稱與標示為預設主版頁面或自訂主版頁面的現有主版頁面名稱相同，就會發生錯誤。 如需如何解決此問題的詳細資訊，請參閱 [逐步解說：使用影像匯入自訂主版頁面和網站頁面](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)。

9. 在模組中，開啟 *Elements.xml*]。

     您必須更新 *Elements.xml* 檔案，以參考您所新增的主版頁面或主題。

10. 針對主版頁面，將現有的模組標記取代為下列標記。

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     針對主題，以下列標記取代現有的模組標記。

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     請務必將預留位置值取代為模組的實際名稱，以及主版頁面或主題。

     屬性 `Type="GhostableInLibrary"` （attribute）表示專案已加入至內容資料庫，而模組的 `Url` 屬性（attribute）會指定在 SharePoint 內容資料庫中儲存檔案的位置。

11. 若要變更主版頁面的部署範圍，請在 **方案總管** 中，開啟功能設計工具中的功能檔案，然後從 [ **範圍** ] 清單中選擇新的部署範圍。

     **Web** 的值表示主版頁面只適用于目前在專案中指定的網站。 [ **網站** ] 值表示主版頁面會套用至目前的網站集合，其中包含所有子網站和根網站。 其他值則不適用。

    > [!NOTE]
    > 由於主題僅適用于網站集合層級，因此建議您不要將主題的範圍設定為 [ **網站**] 以外的任何值。 如果子網站中使用主題，就會發生錯誤。

12. 在功能表列上，選擇 [**建立**  >  **部署方案**]。

13. 若要確認是否已正確部署檔案，請開啟 SharePoint 網站，選擇 [ **網站動作** ] 功能表，選擇 [ **網站設定** ] 命令，然後選擇 [ **主版頁面** ] 連結或 [ **主題** ] 連結。

     主版頁面或主題的清單隨即出現，其中包含主版頁面或您匯入的主題。

## <a name="see-also"></a>另請參閱
- [主版頁面](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [建立 SharePoint 的頁面](../sharepoint/creating-pages-for-sharepoint.md)
- [使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)
