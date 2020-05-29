---
title: 如何：加入、更新或移除 WCF 資料服務參考
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 494e85049a173749d418276340389ebe826a0b0b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184223"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>如何：新增、更新或移除 WCF 資料服務參考

::: moniker range="vs-2017"
*服務參考*可讓專案存取一或多個 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 。 使用 [**加入服務參考**] 對話方塊 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ，在本機、區域網路或網際網路上搜尋目前的解決方案。
::: moniker-end
::: moniker range=">=vs-2019"
您可以使用**方案總管**中的 [**已連線的服務**] 節點來存取**Microsoft WCF Web Service Reference Provider**，這可讓您管理 Windows Communication Foundation （WCF）資料服務參考。
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>新增 WCF 服務參考

### <a name="to-add-a-reference-to-an-external-service"></a>加入外部服務的參考

::: moniker range="vs-2017"

1. 在**方案總管**中，以滑鼠右鍵按一下您要新增服務的專案名稱，然後按一下 [**加入服務參考**]。

   即會出現 [新增服務參考]**** 對話方塊。

1. 在 [**位址**] 方塊中，輸入服務的 URL，然後按一下 [**移**至] 來搜尋服務。 如果服務會執行使用者名稱和密碼安全性，系統可能會提示您輸入使用者名稱和密碼。

    > [!NOTE]
    > 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

     您也可以從 [**通訊**] 清單中選取 URL，這會儲存先前的15個 url，也就是找到有效服務中繼資料的位置。

     執行搜尋時，會顯示進度列。 您隨時可以按一下 [**停止**] 來停止搜尋。

1. 在 [**服務**] 清單中，展開您想要使用之服務的節點，然後選取實體集。

1. 在 [命名空間]**** 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 [確定]****，將參考新增至專案中。

     會產生服務用戶端（proxy），並將描述服務的中繼資料新增*至 app.config 檔案*。
::: moniker-end
::: moniker range=">=vs-2019"
1. 在**方案總管**中，按兩下或點擊 [**已連線的服務**] 節點。

   [**設定服務**] 索引標籤隨即開啟。

1. 選擇 [ **Microsoft WCF Web Service Reference Provider**]。

   [**設定 WCF Web 服務參考**] 對話方塊隨即出現。

   ![[WCF Web 服務提供者] 對話方塊的螢幕擷取畫面](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. 在 [ **URI** ] 方塊中，輸入服務的 URL，然後按一下 [**移**至] 來搜尋服務。 如果服務會執行使用者名稱和密碼安全性，系統可能會提示您輸入使用者名稱和密碼。

    > [!NOTE]
    > 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

     您也可以從 [ **URI** ] 清單中選取 URL，它會儲存先前的15個 url，也就是找到有效的服務中繼資料。

     執行搜尋時，會顯示進度列。 您隨時可以按一下 [**停止**] 來停止搜尋。

1. 在 [**服務**] 清單中，展開您想要使用之服務的節點，然後選取實體集。

1. 在 [命名空間]**** 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 **[完成]** ，將參考加入至專案。

     會產生服務用戶端（proxy），並將描述服務的中繼資料新增*至 app.config 檔案*。

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>若要在目前的方案中加入服務的參考

::: moniker range="vs-2017"

1. 在**方案總管**中，以滑鼠右鍵按一下您要新增服務的專案名稱，然後按一下 [**加入服務參考**]。

    即會出現 [新增服務參考]**** 對話方塊。

1. 按一下 [**探索**]。

    目前解決方案中的所有服務（包括 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 和 WCF 服務）都會加入至**服務**清單中。

1. 在 [**服務**] 清單中，展開您想要使用之服務的節點，然後選取實體集。

1. 在 [命名空間]**** 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 [確定]****，將參考新增至專案中。

    服務用戶端（proxy）會產生，而描述服務的中繼資料則會新增*至 app.config 檔案*。
::: moniker-end
::: moniker range=">=vs-2019"
1. 在**方案總管**中，按兩下或點擊 [**已連線的服務**] 節點。 

   [**設定服務**] 索引標籤隨即開啟。

1. 選擇 [ **Microsoft WCF Web Service Reference Provider**]。

   [**設定 WCF Web 服務參考**] 對話方塊隨即出現。

1. 按一下 [**探索**]。

    目前解決方案中的所有服務（包括 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 和 WCF 服務）都會加入至**服務**清單中。

1. 在 [**服務**] 清單中，展開您想要使用之服務的節點，然後選取實體集。

1. 在 [命名空間]**** 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 **[完成]** ，將參考加入至專案。

    服務用戶端（proxy）會產生，而描述服務的中繼資料則會新增*至 app.config 檔案*。

::: moniker-end

## <a name="update-a-service-reference"></a>更新服務參考

有時候會變更的實體資料模型 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 。 發生這種情況時，您必須更新服務參考。

### <a name="to-update-a-service-reference"></a>若要更新服務參考

- 在**方案總管**中，以滑鼠右鍵按一下服務參考，然後按一下 [**更新服務參考**]。

     [進度] 對話方塊會在參考從其原始位置更新時顯示，而服務用戶端會重新產生以反映中繼資料中的任何變更。

## <a name="remove-a-service-reference"></a>移除服務參考

如果服務參考不再使用，您可以從方案中移除它。

### <a name="to-remove-a-service-reference"></a>若要移除服務參考

- 在**方案總管**中，以滑鼠右鍵按一下服務參考，然後按一下 [**刪除**]。

     服務用戶端將會從解決方案移除，而描述服務的中繼資料將會從*app.config*檔案中移除。

    > [!NOTE]
    > 任何參考服務參考的程式碼都必須手動移除。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
