---
title: "瀏覽 SharePoint 連線使用伺服器總管 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 5ea474f2439b6da519563f08ffe4ddc2f6dcef30
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="browsing-sharepoint-connections-using-server-explorer"></a>使用伺服器總管瀏覽 SharePoint 連線
  您現在可以瀏覽本機 SharePoint 連接中的**伺服器總管**。 使用這項技術就可以巡覽系統中的 SharePoint 網站元件。 SharePoint 網站元件，例如清單定義和內容類型，會出現在節點名為**SharePoint 連接**的樹狀檢視中**伺服器總管**。 若要顯示**伺服器總管**，在功能表列上選擇 **檢視**，**伺服器總管**。 除了顯示 SharePoint 網站元件之外，您還可以使用捷徑功能表的命令移除項目、檢閱其屬性或重新整理樹狀檢閱。  
  
> [!IMPORTANT]  
>  若要瀏覽 SharePoint 網站，您必須是 SharePoint 網站集合的系統管理員，同時必須以本機電腦的系統管理員身分執行 Visual Studio。 否則，網站會出現在**伺服器總管**，但是您無法展開其節點。 若要確認您是網站集合的系統管理員，請開啟站台在 web 瀏覽器中開啟**網站動作**功能表上，選擇**網站權限**，然後在**權限： 小組站台**頁面上，選擇**網站集合管理員**命令**管理**功能區上的群組。 如果您是網站集合管理員，您的名稱會出現在文字方塊中。 如果**網站集合管理員**命令未出現功能區上的管理群組中，您不是管理員網站集合，您必須向網站管理員取得適當的權限。  
  
## <a name="server-explorer-nodes"></a>伺服器總管 節點  
 每個元件的 SharePoint 網站中的節點所表示**伺服器總管**樹狀檢視下的**SharePoint 連接**。 預設的 SharePoint 網站，例如包含稱為討論，代表顯示中的討論區類型的內容類型**討論**SharePoint 網站的網頁。 討論的內容型別包含數個欄位。 若要檢視中的這些欄位**伺服器總管**，展開**ContentTypes**  節點，然後**討論**節點。 下，它會有數個欄位節點，例如主體、 討論主題和標題。  
  
## <a name="node-shortcut-menu-commands"></a>節點的捷徑功能表命令  
 每個節點都有捷徑功能表，用滑鼠右鍵按一下節點，或是選擇它再選擇 Shift+F10 鍵即可存取捷徑功能表。 節點命令可能包括下列各項：  
  
|命令名稱：|描述|  
|------------------|-----------------|  
|重新整理|會更新樹狀檢視，以反映最後一次出現的節點可能會發生任何變更。|  
|刪除|從樹狀檢視中移除選取的節點。 **注意：**這個命令才會啟用 SharePoint 連接底下所列**SharePoint 連接**節點。|  
|屬性|顯示可用的內容中選取的節點**屬性**視窗。 屬性是唯讀，而且並非每個節點都有與其相關聯的屬性。|  
|加入連接|可讓您指定您想要瀏覽 SharePoint 網站。 用於**SharePoint 連接**節點和子網站節點。|  
|在瀏覽器中檢視|在 Web 瀏覽器中顯示所選取的清單。 下的某些清單上使用此命令，**列出**才包含此節點**清單和文件庫**。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[如何：新增或移除 SharePoint 連線](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|描述會新增至新的 SharePoint 網站需要的步驟**SharePoint 連接**節點**伺服器總管**。|  
  
## <a name="see-also"></a>請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  