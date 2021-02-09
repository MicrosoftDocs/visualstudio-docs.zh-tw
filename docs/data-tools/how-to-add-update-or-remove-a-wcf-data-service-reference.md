---
title: 新增、更新或移除 WCF 資料服務參考
description: 請參閱如何新增、更新或移除 Windows Communication Foundation (WCF) 資料服務參考。
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 8d728df5f8af5dff5a7ea2456e1d40d47ddc7f76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866888"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>如何：新增、更新或移除 WCF 資料服務參考

::: moniker range="vs-2017"
*服務參考* 可讓專案存取一或多個專案 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 。 使用 [ **加入服務參考** ] 對話方塊 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ，即可在目前的解決方案、本機、區域網路或網際網路上搜尋。
::: moniker-end
::: moniker range=">=vs-2019"
您可以使用 **方案總管** 中的 [**已連線的服務**] 節點來存取 **Microsoft WCF Web Service Reference 提供者**，這可讓您管理 Windows Communication Foundation (WCF) 資料服務參考。
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>新增 WCF 服務參考

### <a name="to-add-a-reference-to-an-external-service"></a>若要加入外部服務的參考

::: moniker range="vs-2017"

1. 在 **方案總管** 中，以滑鼠右鍵按一下您要新增服務的專案名稱，然後按一下 [ **加入服務參考**]。

   即會出現 [新增服務參考] 對話方塊。

1. 在 [ **位址** ] 方塊中，輸入服務的 URL，然後按一下 [ **移** 至] 以搜尋服務。 如果服務會執行使用者名稱和密碼安全性，系統可能會提示您輸入使用者名稱和密碼。

    > [!NOTE]
    > 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

     您也可以選取 [ **位址** ] 清單中的 URL，該 url 會儲存先前的15個 url，以找到有效的服務中繼資料。

     執行搜尋時，會顯示進度列。 您隨時都可以按一下 [ **停止**] 來停止搜尋。

1. 在 [ **服務** ] 清單中，展開您要使用之服務的節點，然後選取實體集。

1. 在 [命名空間] 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 [確定]，將參考新增至專案中。

     服務用戶端會 (proxy) 產生，而描述服務的中繼資料會新增至 *app.config* 檔。
::: moniker-end
::: moniker range=">=vs-2019"
1. 在 **方案總管** 中，按兩下或點擊 **已連線的服務** 節點。

   [ **設定服務** ] 索引標籤隨即開啟。

1. 選擇 [ **Microsoft WCF Web Service Reference 提供者**]。

   [ **設定 WCF Web Service Reference** ] 對話方塊隨即出現。

   ![[WCF Web 服務提供者] 對話方塊的螢幕擷取畫面](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. 在 [ **URI** ] 方塊中，輸入服務的 URL，然後按一下 [ **移** 至] 以搜尋服務。 如果服務會執行使用者名稱和密碼安全性，系統可能會提示您輸入使用者名稱和密碼。

    > [!NOTE]
    > 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

     您也可以從 **URI** 清單中選取 URL，這會儲存先前的15個 url，以找到有效的服務中繼資料。

     執行搜尋時，會顯示進度列。 您隨時都可以按一下 [ **停止**] 來停止搜尋。

1. 在 [ **服務** ] 清單中，展開您要使用之服務的節點，然後選取實體集。

1. 在 [命名空間] 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 **[完成]** 以加入專案的參考。

     服務用戶端會 (proxy) 產生，而描述服務的中繼資料會新增至 *app.config* 檔。

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>若要在目前的方案中加入服務的參考

::: moniker range="vs-2017"

1. 在 **方案總管** 中，以滑鼠右鍵按一下您要新增服務的專案名稱，然後按一下 [ **加入服務參考**]。

    即會出現 [新增服務參考] 對話方塊。

1. 按一下 [ **探索**]。

    [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]目前方案中)  (和 WCF 服務的所有服務都會新增至 [**服務**] 清單中。

1. 在 [ **服務** ] 清單中，展開您要使用之服務的節點，然後選取實體集。

1. 在 [命名空間] 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 [確定]，將參考新增至專案中。

    服務用戶端 (proxy) 產生，而描述服務的中繼資料會新增至 *app.config* 檔。
::: moniker-end
::: moniker range=">=vs-2019"
1. 在 **方案總管** 中，按兩下或點擊 **已連線的服務** 節點。 

   [ **設定服務** ] 索引標籤隨即開啟。

1. 選擇 [ **Microsoft WCF Web Service Reference 提供者**]。

   [ **設定 WCF Web Service Reference** ] 對話方塊隨即出現。

1. 按一下 [ **探索**]。

    [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]目前方案中)  (和 WCF 服務的所有服務都會新增至 [**服務**] 清單中。

1. 在 [ **服務** ] 清單中，展開您要使用之服務的節點，然後選取實體集。

1. 在 [命名空間] 方塊中，輸入要針對參考使用的命名空間。

1. 按一下 **[完成]** 以加入專案的參考。

    服務用戶端 (proxy) 產生，而描述服務的中繼資料會新增至 *app.config* 檔。

::: moniker-end

## <a name="update-a-service-reference"></a>更新服務參考

有時會變更的實體資料模型 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 。 發生這種情況時，您必須更新服務參考。

### <a name="to-update-a-service-reference"></a>若要更新服務參考

- 在 **方案總管** 中，以滑鼠右鍵按一下 [服務參考]，然後按一下 [ **更新服務參考**]。

     當參考從其原始位置更新時，[進度] 對話方塊隨即顯示，而且會重新產生服務用戶端，以反映中繼資料中的任何變更。

## <a name="remove-a-service-reference"></a>移除服務參考

如果不再使用服務參考，您可以將它從方案中移除。

### <a name="to-remove-a-service-reference"></a>移除服務參考

- 在 **方案總管** 中，以滑鼠右鍵按一下 [服務參考]，然後按一下 [ **刪除**]。

     服務用戶端將會從方案中移除，而描述服務的中繼資料將會從 *app.config* 檔案中移除。

    > [!NOTE]
    > 參考服務參考的任何程式碼都必須手動移除。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
