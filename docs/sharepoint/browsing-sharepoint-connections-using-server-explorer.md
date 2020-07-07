---
title: 使用伺服器總管流覽 SharePoint 連接 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016349"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>使用伺服器總管流覽 SharePoint 連接
  您現在可以在**伺服器總管**中流覽本機 SharePoint 連接。 使用這項技術就可以巡覽系統中的 SharePoint 網站元件。 SharePoint 網站元件（例如清單定義和內容類型）會出現在**伺服器總管**樹狀檢視中名為 [ **SharePoint 連接**] 的節點中。 若要顯示**伺服器總管**，請在功能表列上選擇 [ **View**  >  **伺服器總管**]。 除了顯示 SharePoint 網站元件之外，您還可以使用捷徑功能表的命令移除項目、檢視其屬性或重新整理樹狀檢視。

> [!IMPORTANT]
> 若要瀏覽 SharePoint 網站，您必須是 SharePoint 網站集合的系統管理員，同時必須以本機電腦的系統管理員身分執行 Visual Studio。 否則，網站會出現在**伺服器總管**中，但是您無法展開其節點。 若要確認您是否為網站集合的系統管理員，請在網頁瀏覽器中開啟網站，開啟 [**網站動作**] 功能表，選擇 [**網站許可權**]，然後在 [**許可權：小組網站**] 頁面上，從功能區上的 [**管理**] 群組中選擇 [**網站集合管理員**] 命令。 如果您是網站集合管理員，您的名稱就會出現在文字方塊中。 如果 [**網站集合管理員**] 命令未出現在功能區上的 [管理] 群組中，您就不是網站集合的系統管理員，而且必須從網站管理員取得適當的許可權。

## <a name="server-explorer-nodes"></a>伺服器總管節點
 SharePoint 網站的每個元件都會以 [ **Sharepoint 連接**] 底下 [**伺服器總管**樹狀檢視] 中的節點表示。 例如，預設 SharePoint 網站包含稱為「討論」的內容類型，其代表在 SharePoint 網站的 [**討論**] 頁面中顯示的討論類型。 討論內容類型包含幾個欄位。 若要在**伺服器總管**中查看這些欄位，請依序展開 [ **ContentTypes** ] 節點和 [**討論**] 節點。 其底下有數個欄位節點，例如 [內文]、[討論主體] 和 [標題]。

## <a name="node-shortcut-menu-commands"></a>節點快捷方式功能表命令
 每個節點都有快捷方式功能表，您可以用滑鼠右鍵按一下節點，或選擇它，然後選擇 [ **Shift** + **F10** ] 鍵來存取。 Node 命令可能包括下列各項：

|命令名稱：|描述|
|------------------|-----------------|
|重新整理|更新樹狀檢視，以反映自上一次顯示節點之後可能發生的任何變更。|
|刪除|從樹狀檢視中移除選取的節點。 **注意：** 此命令只會在**sharepoint**連接節點底下列出的 sharepoint 連接上啟用。|
|屬性|在 [**屬性**] 視窗中顯示所選取節點的可用屬性。 這些屬性都是唯讀的，而不是每個節點都有相關聯的屬性。|
|加入連接|可讓您指定要流覽的 SharePoint 網站。 可在 [ **SharePoint 連接**] 節點和子網站節點上取得。|
|在瀏覽器中檢視|在網頁瀏覽器中顯示選取的清單。 在清單**和程式庫**所包含的 [**清單**] 節點底下的部分清單中，可使用此命令。|

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[如何：加入或移除 SharePoint 連接](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|說明在**伺服器總管**中，將新的 sharepoint 網站加入 [ **sharepoint 連接**] 節點所需的步驟。|

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
