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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b6726b2c859143f5dbc9b264e67bb9bb91757de5
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089308"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>如何： 加入、 更新或移除 WCF 資料服務參考
A*服務參考*允許存取一或多個專案[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。 使用**加入服務參考**對話方塊，即可搜尋[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]在目前方案中，區域網路上，在本機，或在網際網路上。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>加入服務參考

### <a name="to-add-a-reference-to-an-external-service"></a>將參考加入至外部服務

1.  在 [**方案總管**，以滑鼠右鍵按一下您想要新增服務]，然後按一下專案名稱**加入服務參考**。

     **加入服務參考** 對話方塊隨即出現。

2.  在 **地址**方塊，輸入服務的 URL，然後按一下**移**搜尋服務。 如果服務實作使用者名稱和密碼的安全性，您可能會提示輸入使用者名稱和密碼。

    > [!NOTE]
    >  您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

     您也可以選取從 URL**地址**清單中，它會儲存先前的 15 個 Url 處找到有效的服務中繼資料。

     執行搜尋時，會顯示進度列。 您可以按一下即可停止搜尋隨時**停止**。

3.  在  **Services**清單中，展開您想要使用選取的實體集服務的節點。

4.  在 **命名空間**方塊中，輸入您想要針對參考使用的命名空間。

5.  按一下 **確定**加入至專案參考。

     產生服務用戶端 (proxy)，並描述服務的中繼資料加入至*app.config*檔案。

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>若要加入服務參考目前方案中

1.  在 [**方案總管**，以滑鼠右鍵按一下您想要新增服務]，然後按一下專案名稱**加入服務參考**。

     **加入服務參考** 對話方塊隨即出現。

2.  按一下 **探索**。

     所有服務 (同時[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]和 WCF 服務) 在目前的方案會加入至**Services**清單。

3.  在  **Services**清單中，展開您想要使用選取的實體集服務的節點。

4.  在 **命名空間**方塊中，輸入您想要針對參考使用的命名空間。

5.  按一下 **確定**加入至專案參考。

     產生服務用戶端 (proxy)，並描述服務的中繼資料加入至*app.config*檔案。

## <a name="update-a-service-reference"></a>更新服務參考
 實體資料模型[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]有時會變更。 當發生這種情況時，您必須更新服務參考。

### <a name="to-update-a-service-reference"></a>若要更新服務參考

-   在 **方案總管**，以滑鼠右鍵按一下 服務參考，然後按一下**更新服務參考**。

     參考會從其原始位置，更新和服務用戶端會重新產生以反映在中繼資料中的任何變更時，會顯示進度對話方塊。

## <a name="remove-a-service-reference"></a>移除服務參考
 如果不再使用的服務參考，您可以從您的方案中移除它。

### <a name="to-remove-a-service-reference"></a>若要移除服務參考

-   在 **方案總管**，以滑鼠右鍵按一下 服務參考，然後按一下**刪除**。

     服務用戶端將會從方案中移除，並描述服務的中繼資料會移除*app.config*檔案。

    > [!NOTE]
    >  您必須手動移除參考的服務參考的任何程式碼。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)