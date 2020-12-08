---
title: 如何：變更功能區上的索引標籤位置
description: 您可以使用 [索引標籤集合編輯器]，變更功能區上的自訂索引標籤順序，以及在功能區的內建索引標籤前後定位自訂索引標籤。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21fd7f17f7a990f95ce5c8b781e85807a10608c4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846762"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>如何：變更功能區上的索引標籤位置
  您可以使用 [索引標籤 **集合編輯器]** 來變更功能區上的自訂索引標籤順序。 您可以在功能區上的內建索引標籤之前或之後放置自訂索引標籤。 內建索引標籤是已在 Microsoft Office 應用程式功能區上的索引標籤。 例如，[ **資料** ] 索引標籤是 Excel 中的內建索引標籤。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>變更功能區上的索引標籤順序

1. 在 **方案總管** 中選取 [功能區程式碼檔] (*.vb* 或 *.cs* 檔案) 。

2. 在 [ **View** ] 功能表上，按一下 [ **設計** 工具]。

3. 以滑鼠右鍵按一下 [功能區設計工具]，然後按一下 [ **屬性**]。

4. 在 [ **屬性** ] 視窗中， **選取 [索引** 標籤] 屬性，然後按一下省略號按鈕 (![ASP.NET mobile designer 橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 。

     [索引標籤 **集合編輯器]** 隨即出現。

5. 在 [索引標籤 **集合編輯器]** 的 [ **成員** ] 清單中，選取您要移動的索引標籤，然後按一下 [向上] 或 [向下] 箭號來變更定位順序。

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>在功能區上的內建索引標籤前後定位索引標籤

1. 在功能區設計工具中，選取 [自訂] 索引標籤。

2. 在 [ **屬性** ] 視窗中，展開 [ **ControlId** ] 屬性，然後確認 [ **ControlIdType** ] 屬性的值已設定為 [ **自訂**]。

3. 在 [ **屬性** ] 視窗中，展開 [ **Position** ] 屬性。

4. 將 **positiontype]** 屬性設定為適當的值：

    - **BeforeOfficeId** 會在指定的內建索引標籤之前放置群組。

    - **AfterOfficeId** 會將群組放置在指定的內建索引標籤之後。

5. 將 [ **OfficeId** ] 屬性設定為內建索引標籤的控制項識別碼。

     如需控制項識別碼清單，請參閱 [office 2010 說明檔： office 流暢的使用者介面控制項識別碼](https://www.microsoft.com/download/details.aspx?id=6627)。

## <a name="see-also"></a>另請參閱
- [功能區總覽](../vsto/ribbon-overview.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
