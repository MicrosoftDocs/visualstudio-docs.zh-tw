---
title: HOW TO：當地語系化功能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 165eee357c001720af132236a8577f259efa4f24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887670"
---
# <a name="how-to-localize-a-feature"></a>HOW TO：當地語系化功能
  根據預設，功能標題和描述使用硬式編碼的字串值。 若要當地語系化的功能標題和描述，請將字串取代運算式參考當地語系化的資源。  
  
## <a name="localize-a-feature"></a>當地語系化功能  
  
#### <a name="to-localize-a-feature"></a>若要當地語系化功能  
  
1.  中**方案總管**，開啟捷徑功能表**Feature1**節點，然後選擇**加入功能資源**。  
  
2.  在 **加入資源**對話方塊方塊中，選擇**因語言而異**從做為預設語言功能資源檔的文化特性清單。  
  
3.  針對每種當地語系化的語言重複先前的步驟，並且針對當地語系化的功能資源檔選擇您所選擇的語言。  
  
     這樣會建立不同的功能資源檔：一個用於預設語言，另一個用於要支援的每種當地語系化語言。  
  
4.  在 [資源編輯器] 中開啟每個資源檔，然後輸入所有 ID 字串及其值。  
  
     例如，在預設功能資源檔中，輸入的字串識別碼**標題**值是**My 功能標題**，和第二個字串的 ID**描述**值是**我的功能描述**。 針對每個當地語系化的資源檔，使用預設功能資源中所使用的相同字串 ID，但要輸入值的當地語系化字串。  
  
5.  您輸入所有資源值之後，開啟此功能的捷徑功能表 (比方說， *Feature1.feature*)，然後選擇**檢視表設計工具**功能設計工具中開啟此功能。  
  
6.  若要當地語系化**標題**並**描述**欄位在功能中，使用下列格式的方塊中輸入值：  
  
     `$Resources:` *字串識別碼*  
  
     例如，輸入 [$Resources:**標題**中**功能標題**] 方塊中和 $Resources:**描述**中**功能描述**方塊.  
  
     字串 ID 必須與資源檔中所使用的字串 ID 相符。  
  
7.  選擇**F5**鍵，建置並執行應用程式。  
  
8.  在 SharePoint 中，開啟**站台動作** 功能表中，選擇**站台設定**，然後在**網站動作**區段中選擇**管理網站功能**連結。  
  
9. 在 SharePoint 中，變更預設的顯示語言。  
  
     當地語系化的功能標題和描述會出現在應用程式。 若要顯示當地語系化的資源，請在 SharePoint 伺服器必須符合資源檔的文化特性的語言套件安裝。  
  
## <a name="see-also"></a>另請參閱
 [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何：加入資源檔](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)  
