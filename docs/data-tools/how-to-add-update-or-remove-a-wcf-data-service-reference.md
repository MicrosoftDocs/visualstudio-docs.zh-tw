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
ms.openlocfilehash: 9e39b28a3de5aa97ac7c0673cd16b71508ae4276
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925972"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>如何：加入、更新或移除 WCF 資料服務參考
A*服務參考*允許存取一或多個專案[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。 使用**加入服務參考**對話方塊來搜尋[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]在目前方案中，區域網路上，在本機，或在網際網路上。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-a-service-reference"></a>加入服務參考

#### <a name="to-add-a-reference-to-an-external-service"></a>若要加入到外部服務的參考

1.  在**方案總管] 中**，以滑鼠右鍵按一下您想要加入服務，然後按一下 [專案名稱**加入服務參考**。

     **加入服務參考** 對話方塊隨即出現。

2.  在**位址**方塊中，輸入服務的 URL，然後按一下**移**搜尋服務。 如果服務實作使用者名稱和密碼的安全性，您可能會提示輸入使用者名稱和密碼。

    > [!NOTE]
    >  您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

     您也可以選取從 URL**位址**清單，會儲存先前的 15 個 Url，找到有效的服務中繼資料的位置。

     執行搜尋時，會顯示進度列。 您可以按一下來停止隨時搜尋**停止**。

3.  在**服務**清單中，展開您想要使用選取的實體集之服務節點。

4.  在**命名空間**方塊中，輸入您想要針對參考使用的命名空間。

5.  按一下**確定**將參考加入至專案。

     服務用戶端 (proxy) 會產生，並描述服務的中繼資料新增至 app.config 檔案。

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>若要加入服務參考目前方案中

1.  在**方案總管] 中**，以滑鼠右鍵按一下您想要加入服務，然後按一下 [專案名稱**加入服務參考**。

     **加入服務參考** 對話方塊隨即出現。

2.  按一下**探索**。

     所有服務 (兩者[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]和 WCF 服務) 在目前的方案會加入至**服務**清單。

3.  在**服務**清單中，展開您想要使用選取的實體集之服務節點。

4.  在**命名空間**方塊中，輸入您想要針對參考使用的命名空間。

5.  按一下**確定**將參考加入至專案。

     服務用戶端 (proxy) 會產生，並描述服務的中繼資料新增至 app.config 檔案。

## <a name="updating-a-service-reference"></a>更新服務參考
 實體資料模型[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]有時候會將變更。 當發生這種情況時，就必須更新服務參考。

#### <a name="to-update-a-service-reference"></a>若要更新服務參考

-   在**方案總管] 中**，以滑鼠右鍵按一下 [服務參考，然後按一下**更新服務參考**。

     參考從其原始位置，更新和服務用戶端會重新產生以反映在中繼資料中的任何變更時，會顯示進度對話方塊。

## <a name="removing-a-service-reference"></a>移除服務參考
 如果不再使用的服務參考，您可以從您的方案中移除它。

#### <a name="to-remove-a-service-reference"></a>若要移除服務參考

-   在**方案總管] 中**，以滑鼠右鍵按一下 [服務參考，然後按一下**刪除**。

     服務用戶端將會從方案中移除，並描述服務的中繼資料將會從 app.config 檔案中移除。

    > [!NOTE]
    >  參考服務參考的任何程式碼必須以手動方式移除。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)