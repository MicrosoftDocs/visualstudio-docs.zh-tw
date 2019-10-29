---
title: 如何：匯入主版頁面或主題 |Microsoft Docs
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
ms.openlocfilehash: 2c5078d31e2dcb7f11e5c19e0f8cb228e2f75d50
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984193"
---
# <a name="how-to-import-a-master-page-or-theme"></a>如何：匯入主版頁面或主題
  您可以建立和使用主版頁面和主題，讓 SharePoint 網站上的頁面具有一致的外觀。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不會提供這些專案的範本，但是您可以在 SharePoint Designer 中建立這些專案，然後將它們匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱 Microsoft 網站上的[建立區塊：頁面和使用者介面](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))。

### <a name="to-import-a-master-page-or-theme"></a>若要匯入主版頁面或主題

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，建立或開啟 SharePoint 專案。

     如需如何建立 SharePoint 專案的詳細資訊，請參閱[sharepoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在功能表列中，選擇 [專案] > [加入新項目]。

3. 在 [**加入新專案**] 對話方塊中，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 SharePoint 範本清單中，選擇 [**模組**] 範本，然後指定模組的名稱。

     模組包含檔案（例如，主版頁面或主題檔案），用於部署至您在 SharePoint 中指定的位置。

5. 在模組中，刪除名為*Sample .txt*的預設檔案。

6. 選擇 [模組] 節點。

7. 在功能表列上，選擇 [**專案**] > [**加入現有專案**]，然後選擇主版頁面或主題檔案。

     主版分頁檔案的副檔名為 master，而主題檔案的副檔名為 thmx。

8. 如果您已新增主版頁面，請在模組的屬性中將其 [**部署衝突解決**方式] 設定變更為 [**自動**]。

    > [!NOTE]
    > 如果主版頁面的名稱與已標示為 [預設主版頁面] 或 [自訂主版頁面] 的現有主版頁面名稱相同，則可能會發生錯誤。 如需如何解決此問題的詳細資訊，請參閱[逐步解說：使用影像匯入自訂主版頁面和網站頁面](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)。

9. 在模組中，開啟*Elements. xml*。

     您必須更新*元素 .xml*檔案，以參考您新增的主版頁面或主題。

10. 若為主版頁面，請將現有的模組標記取代為下列標記。

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     針對主題，將現有的模組標記取代為下列標記。

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     請務必以模組的實際名稱和主版頁面或主題取代預留位置值。

     屬性 `Type="GhostableInLibrary"` 指出專案已加入至內容資料庫，而模組的 `Url` 屬性會指定要將檔案儲存在 SharePoint 內容資料庫中的位置。

11. 若要變更主版頁面的部署範圍，請在 **方案總管**中，開啟功能設計工具中的功能檔案，然後從 **範圍** 清單中選擇新的部署範圍。

     **Web**值表示主版頁面僅適用于目前在專案中指定的網站。 [**網站**] 值表示主版頁面會套用至目前的網站集合，其中包含所有的子網站和根網站。 其他值則不適用。

    > [!NOTE]
    > 因為主題僅適用于網站集合層級，所以我們建議您不要將主題的範圍設定為 [**網站**] 以外的任何專案。 如果子網站中使用主題，可能會發生錯誤。

12. 在功能表列上，選擇 [**組建**] > [**部署方案**]。

13. 若要確認是否已正確部署檔案，請開啟 SharePoint 網站，選擇 [**網站動作**] 功能表，選擇 [**網站設定**] 命令，然後選擇 [**主版頁面**] 連結或 [**主題**] 連結。

     主版頁面或主題的清單隨即出現，其中包含您匯入的主版頁面或主題。

## <a name="see-also"></a>請參閱
- [主版頁面](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [建立 SharePoint 的頁面](../sharepoint/creating-pages-for-sharepoint.md)
- [使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)
