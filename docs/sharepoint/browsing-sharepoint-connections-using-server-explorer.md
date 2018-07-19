---
title: 瀏覽 SharePoint 連線，使用 伺服器總管 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: e897469eee33a1e4ee48b9096714b4213c099a8f
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325991"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>使用伺服器總管瀏覽 SharePoint 連線
  您現在可以瀏覽本機 SharePoint 連接中的**伺服器總管**。 使用這項技術就可以巡覽系統中的 SharePoint 網站元件。 SharePoint 站台元件，例如清單定義和內容類型，會顯示在名為節點**SharePoint 連線**在樹狀檢視中的**伺服器總管**。 若要顯示**伺服器總管**，在功能表列上選擇 **檢視** > **伺服器總管**。 除了顯示 SharePoint 網站元件之外，您還可以使用捷徑功能表的命令移除項目、檢閱其屬性或重新整理樹狀檢閱。  
  
> [!IMPORTANT]  
>  若要瀏覽 SharePoint 網站，您必須是 SharePoint 網站集合的系統管理員，同時必須以本機電腦的系統管理員身分執行 Visual Studio。 否則，網站會出現在**伺服器總管**，但是您無法展開其節點。 若要確認您是否是網站集合管理員，開啟 在網頁瀏覽器，開啟 站台**網站動作**功能表上，選擇**網站的權限**，然後在**權限： 小組站台**頁面上，選擇**Site Collection Administrators**命令**管理**功能區上的群組。 您的名稱會出現在文字方塊中，如果您是網站集合管理員。 如果**Site Collection Administrators**命令未出現在功能區上的管理群組中，您不是系統管理員針對網站集合，您必須從站台系統管理員取得適當的權限。  
  
## <a name="server-explorer-nodes"></a>伺服器總管 節點
 表示 SharePoint 網站的每個元件中的節點**伺服器總管**樹狀檢視下的**SharePoint 連線**。 例如，預設的 SharePoint 網站包含一個名為討論中，這表示在顯示的討論區類型的內容類型**討論**SharePoint 網站的頁面。 討論內容類型包含數個欄位。 若要檢視中的這些欄位**伺服器總管**，展開**ContentTypes**節點，然後**討論**節點。 下，它會有數個欄位節點，例如內文，討論主題和 Title。  
  
## <a name="node-shortcut-menu-commands"></a>節點的捷徑功能表命令
 每個節點有您存取滑鼠右鍵按一下節點或選擇它，然後選擇捷徑功能表**Shift**+**F10**索引鍵。 Node 命令可能包括下列各項：  
  
|命令名稱：|描述|  
|------------------|-----------------|  
|重新整理|更新樹狀檢視中的節點所顯示的上一次之後所發生的任何變更。|  
|刪除|從 [樹狀] 檢視中移除選取的節點。 **注意︰** 此命令只會啟用底下所列的 SharePoint 連線**SharePoint 連線**節點。|  
|屬性|顯示選取之節點中可用的屬性**屬性**視窗。 屬性是所有唯讀，而不是每個節點有與其相關聯的屬性。|  
|加入連接|可讓您指定您想要瀏覽 SharePoint 網站。 用於**SharePoint 連線**節點和子網站節點。|  
|在瀏覽器中檢視|在 Web 瀏覽器中顯示所選取的清單。 此命令可用於某些 底下列出**列出**節點中包含**清單和程式庫**。|  
  
## <a name="related-topics"></a>相關主題
  
|標題|描述|  
|-----------|-----------------|  
|[如何： 新增或移除 SharePoint 連線](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|描述會新增至新的 SharePoint 網站需要的步驟**SharePoint 連線**中的節點**伺服器總管**。|  
  
## <a name="see-also"></a>另請參閱
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
 
