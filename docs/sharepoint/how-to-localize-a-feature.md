---
title: 如何：當地語系化功能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0d15654ba48b6c95cf2b2f7fa4f9cd665f0959a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016142"
---
# <a name="how-to-localize-a-feature"></a>如何：當地語系化功能
  根據預設，功能標題和描述會使用硬式編碼的字串值。 若要將功能標題和描述當地語系化，請將字串取代為參考當地語系化資源的運算式。

## <a name="localize-a-feature"></a>將功能當地語系化

#### <a name="to-localize-a-feature"></a>若要將功能當地語系化

1. 在**方案總管**中，開啟 [ **Feature1** ] 節點的快捷方式功能表，然後選擇 [**加入功能資源**]。

2. 在 [**加入資源**] 對話方塊中，從清單中選擇 [不因**語言**而異] 做為預設語言功能資源檔的文化特性。

3. 針對每種當地語系化的語言重複先前的步驟，並且針對當地語系化的功能資源檔選擇您所選擇的語言。

     這樣會建立不同的功能資源檔：一個用於預設語言，另一個用於要支援的每種當地語系化語言。

4. 在 [資源編輯器] 中開啟每個資源檔，然後輸入所有 ID 字串及其值。

     例如，在預設功能資源檔中，輸入具有 [**我的功能標題**] 值的**標題**字串識別碼，以及 [**描述**] 的第二個字串識別碼，其值為 [**我的功能描述**]。 針對每個當地語系化的資源檔，使用預設功能資源中所使用的相同字串 ID，但要輸入值的當地語系化字串。

5. 在您輸入所有資源值之後，請開啟功能的快捷方式功能表（例如， *Feature1*），然後選擇 [ **View designer** ]，以在功能設計工具中開啟此功能。

6. 若要將功能中的 [**標題**] 和 [**描述**] 欄位當地語系化，請使用下列格式來輸入其方塊中的值：

     `$Resources:` *字串識別碼*

     例如，在 [**功能標題**] 方塊中輸入 $Resources：**Title** ，並 $Resources： [**功能描述**] 方塊中的 [**描述**]。

     字串 ID 必須與資源檔中所使用的字串 ID 相符。

7. 選擇**F5**鍵以建立並執行應用程式。

8. 在 SharePoint 中，開啟 [**網站動作**] 功能表，選擇 [**網站設定**]，然後在 [**網站動作**] 區段中選擇 [**管理網站功能**] 連結。

9. 在 SharePoint 中，變更 [顯示語言] 的預設值。

     當地語系化的功能標題和描述會出現在應用程式中。 若要顯示當地語系化的資源，SharePoint 伺服器必須安裝符合資源檔文化特性的語言套件。

## <a name="see-also"></a>另請參閱
- [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)
- [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)
- [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)
- [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)
