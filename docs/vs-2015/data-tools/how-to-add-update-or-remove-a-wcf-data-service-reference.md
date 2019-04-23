---
title: HOW TO：新增、 更新或移除 WCF 資料服務參考 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e7f70808ff91ec32ef52deedc05724f9bac3f7d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079134"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>HOW TO：新增、更新或移除 WCF 資料服務參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A*服務參考*允許存取一或多個專案[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]。 使用**加入服務參考**對話方塊，即可搜尋[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]在目前方案中，區域網路上，在本機，或在網際網路上。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>加入服務參考  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>將參考加入至外部服務  
  
1. 在 **方案總管**，以滑鼠右鍵按一下您要加入服務，然後按一下 專案名稱**加入服務參考**。  
  
     **加入服務參考** 對話方塊隨即出現。  
  
2. 在 **地址**方塊，輸入服務的 URL，然後按一下**移**搜尋服務。 如果服務實作使用者名稱和密碼的安全性，您可能會提示輸入使用者名稱和密碼。  
  
    > [!NOTE]
    >  您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。  
  
     您也可以選取從 URL**地址**清單中，它會儲存先前的 15 個 Url 處找到有效的服務中繼資料。  
  
     執行搜尋時，會顯示進度列。 您可以按一下即可停止搜尋隨時**停止**。  
  
3. 在  **Services**清單中，展開您想要使用選取的實體集服務的節點。  
  
4. 在 **命名空間**方塊中，輸入您想要針對參考使用的命名空間。  
  
5. 按一下 **確定**加入至專案參考。  
  
     產生服務用戶端 (proxy)，並描述服務的中繼資料新增至 app.config 檔案。  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>若要加入服務參考目前方案中  
  
1. 在 **方案總管**，以滑鼠右鍵按一下您要加入服務，然後按一下 專案名稱**加入服務參考**。  
  
     **加入服務參考** 對話方塊隨即出現。  
  
2. 按一下 **探索**。  
  
     所有服務 (同時[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]和 WCF 服務) 在目前的方案會加入至**Services**清單。  
  
3. 在  **Services**清單中，展開您想要使用選取的實體集服務的節點。  
  
4. 在 **命名空間**方塊中，輸入您想要針對參考使用的命名空間。  
  
5. 按一下 **確定**加入至專案參考。  
  
     產生服務用戶端 (proxy)，並描述服務的中繼資料新增至 app.config 檔案。  
  
## <a name="updating-a-service-reference"></a>更新服務參考  
 實體資料模型[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]有時候會將變更。 當發生這種情況時，就必須更新服務參考。  
  
#### <a name="to-update-a-service-reference"></a>若要更新服務參考  
  
- 在 **方案總管**，以滑鼠右鍵按一下 服務參考，然後按一下**更新服務參考**。  
  
     參考會從其原始位置，更新和服務用戶端會重新產生以反映在中繼資料中的任何變更時，會顯示進度對話方塊。  
  
## <a name="removing-a-service-reference"></a>移除服務參考  
 如果不再使用的服務參考，您可以從您的方案中移除它。  
  
#### <a name="to-remove-a-service-reference"></a>若要移除服務參考  
  
- 在 **方案總管**，以滑鼠右鍵按一下 服務參考，然後按一下**刪除**。  
  
     服務用戶端將會從方案中移除，並描述服務的中繼資料將會從 app.config 檔案中移除。  
  
    > [!NOTE]
    >  參考的服務參考的任何程式碼，就必須手動移除。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
