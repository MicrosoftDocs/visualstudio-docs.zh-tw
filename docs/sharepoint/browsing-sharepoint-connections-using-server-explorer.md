---
title: 使用伺服器總管流覽 SharePoint 連接 |Microsoft Docs
description: 使用伺服器總管流覽 SharePoint 連接。 瞭解伺服器總管節點和節點的快捷方式功能表命令。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b188d95e6478e488fc896b0622fb8d145ef2a741
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851604"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>使用伺服器總管流覽 SharePoint 連接
  您現在可以流覽 **伺服器總管** 中的本機 SharePoint 連接。 使用這項技術就可以巡覽系統中的 SharePoint 網站元件。 SharePoint 網站元件（例如清單定義和內容類型）會出現在 **伺服器總管** 樹狀檢視中名為 [ **SharePoint 連接**] 的節點中。 若要顯示 **伺服器總管**，請在功能表列上選擇 [ **View**  >  **伺服器總管**]。 除了顯示 SharePoint 網站元件之外，您還可以使用捷徑功能表的命令移除項目、檢視其屬性或重新整理樹狀檢視。

> [!IMPORTANT]
> 若要瀏覽 SharePoint 網站，您必須是 SharePoint 網站集合的系統管理員，同時必須以本機電腦的系統管理員身分執行 Visual Studio。 否則，網站會出現在 **伺服器總管** 中，但是您無法展開其節點。 若要確認您是否為網站集合的系統管理員，請在網頁瀏覽器中開啟網站，開啟 [**網站動作**] 功能表，選擇 [**網站許可權**]，然後在 [**許可權：小組網站**] 頁面上，從功能區上的 [**管理**] 群組中選擇 [**網站集合管理員**] 命令。 如果您是網站集合管理員，則您的名稱會出現在文字方塊中。 如果 [ **網站集合管理員** ] 命令未出現在功能區的 [管理] 群組中，則您不是網站集合的系統管理員，而且必須從網站管理員取得適當的許可權。

## <a name="server-explorer-nodes"></a>伺服器總管節點
 SharePoint 網站的每個元件都是以 **Sharepoint 連接** 下 **伺服器總管** 樹狀檢視中的節點來表示。 例如，預設的 SharePoint 網站包含一個稱為「討論」的內容類型，這代表在 SharePoint 網站的 [ **討論** ] 頁面中顯示的討論型別。 討論內容類型包含數個欄位。 若要在 **伺服器總管** 中查看這些欄位，請展開 [ **ContentTypes** ] 節點，然後展開 [ **討論** ] 節點。 其中有數個欄位節點，例如內文、討論主體和標題。

## <a name="node-shortcut-menu-commands"></a>節點快捷方式功能表命令
 每個節點都有快捷方式功能表，您可以用滑鼠右鍵按一下節點或選擇它，然後選擇 **Shift** + **F10** 鍵來存取。 節點命令可能包含下列各項：

|命令名稱：|Description|
|------------------|-----------------|
|重新整理|更新樹狀檢視，以反映自從上一次顯示節點之後可能發生的任何變更。|
|刪除|從樹狀檢視中移除選取的節點。 **注意：**  此命令只會在 [ **Sharepoint 連接** ] 節點下所列的 sharepoint 連接上啟用。|
|屬性|在 [ **屬性** ] 視窗中顯示所選取節點的可用屬性。 這些屬性都是唯讀的，而且並非每個節點都有相關聯的屬性。|
|加入連接|可讓您指定想要流覽的 SharePoint 網站。 可在 [ **SharePoint 連接** ] 節點和子網站節點上取得。|
|在瀏覽器中檢視|在網頁瀏覽器中顯示選取的清單。 此命令可在清單 **和程式庫** 所包含的 [**清單**] 節點下的某些清單中使用。|

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[如何：加入或移除 SharePoint 連接](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|描述將新的 SharePoint 網站加入至 **伺服器總管** 中 [ **sharepoint 連接**] 節點所需的步驟。|

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
