---
title: 如何：加入、更新或移除 WCF 資料服務參考 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670011"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>如何：加入、更新或移除 WCF 資料服務參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*服務參考*可讓專案存取一或多個專案 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 。 使用 [ **加入服務參考** ] 對話方塊 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] ，即可在目前的解決方案、本機、區域網路或網際網路上搜尋。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>加入服務參考

#### <a name="to-add-a-reference-to-an-external-service"></a>若要加入外部服務的參考

1. 在 **方案總管**中，以滑鼠右鍵按一下您要新增服務的專案名稱，然後按一下 [ **加入服務參考**]。

     即會出現 [新增服務參考]**** 對話方塊。

2. 在 [ **位址** ] 方塊中，輸入服務的 URL，然後按一下 [ **移** 至] 以搜尋服務。 如果服務會執行使用者名稱和密碼安全性，系統可能會提示您輸入使用者名稱和密碼。

    > [!NOTE]
    > 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

     您也可以選取 [ **位址** ] 清單中的 URL，該 url 會儲存先前的15個 url，以找到有效的服務中繼資料。

     執行搜尋時，會顯示進度列。 您隨時都可以按一下 [ **停止**] 來停止搜尋。

3. 在 [ **服務** ] 清單中，展開您要使用之服務的節點，然後選取實體集。

4. 在 [命名空間]**** 方塊中，輸入要針對參考使用的命名空間。

5. 按一下 [確定]****，將參考新增至專案中。

     服務用戶端會 (proxy) 產生，而描述服務的中繼資料會新增至 app.config 檔。

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>若要在目前的方案中加入服務的參考

1. 在 **方案總管**中，以滑鼠右鍵按一下您要新增服務的專案名稱，然後按一下 [ **加入服務參考**]。

     即會出現 [新增服務參考]**** 對話方塊。

2. 按一下 [ **探索**]。

     [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]目前方案中)  (和 WCF 服務的所有服務都會新增至 [**服務**] 清單中。

3. 在 [ **服務** ] 清單中，展開您要使用之服務的節點，然後選取實體集。

4. 在 [命名空間]**** 方塊中，輸入要針對參考使用的命名空間。

5. 按一下 [確定]****，將參考新增至專案中。

     服務用戶端會 (proxy) 產生，而描述服務的中繼資料會新增至 app.config 檔。

## <a name="updating-a-service-reference"></a>更新服務參考
 的實體資料模型 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 有時會變更。 發生這種情況時，必須更新服務參考。

#### <a name="to-update-a-service-reference"></a>若要更新服務參考

- 在 **方案總管**中，以滑鼠右鍵按一下 [服務參考]，然後按一下 [ **更新服務參考**]。

     當參考從其原始位置更新時，會顯示 [進度] 對話方塊，並重新產生服務用戶端，以反映中繼資料中的任何變更。

## <a name="removing-a-service-reference"></a>移除服務參考
 如果不再使用服務參考，您可以將它從方案中移除。

#### <a name="to-remove-a-service-reference"></a>移除服務參考

- 在 **方案總管**中，以滑鼠右鍵按一下 [服務參考]，然後按一下 [ **刪除**]。

     服務用戶端將會從方案中移除，而描述服務的中繼資料將會從 app.config 檔案中移除。

    > [!NOTE]
    > 任何參考服務參考的程式碼都必須手動移除。

## <a name="see-also"></a>另請參閱
 [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
