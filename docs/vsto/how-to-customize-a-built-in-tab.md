---
title: 如何：自訂內建索引標籤
description: 瞭解如何將群組和控制項新增至內建索引標籤。內建索引標籤是已在 Microsoft Office 應用程式功能區上的索引標籤。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94cf4d256cafa03ee4604138f7233ff9fd3cf6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953990"
---
# <a name="how-to-customize-a-built-in-tab"></a>如何：自訂內建索引標籤
  您可以將群組和控制項加入至內建索引標籤。內建索引標籤是已在 Microsoft Office 應用程式功能區上的索引標籤。 例如，[ **資料** ] 索引標籤是 Excel 中的內建索引標籤。 當您建立自訂群組時，它會出現在索引標籤的最末端，但是您可以在索引標籤上任意移動群組。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> 您可以在內建索引標籤加入群組，但無法從內建索引標籤移除內建群組。

### <a name="to-add-groups-to-a-built-in-tab"></a>在內建索引標籤加入群組

1. 以滑鼠右鍵按一下 **方案總管** 中的功能區程式碼檔案，然後按一下 [ **視圖設計** 工具]。

    > [!NOTE]
    > 如果功能區程式碼檔案未出現在 **方案總管** 中，您就必須將 **功能區專案** 加入至您的專案。 請參閱 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。

2. 以滑鼠右鍵按一下功能區設計工具中的任何索引標籤，然後按一下 [ **屬性**]。

3. 在 [ **屬性** ] 視窗中，展開 [ **ControlId** ] 屬性，然後將 [ **ControlIdType** ] 屬性設定為 [ **Office**]。

4. 將 **OfficeId** 屬性設定為您想要自訂之內建索引標籤的 *控制項識別碼* 。

     控制項 ID 是唯一識別 Microsoft Office 應用程式內建索引標籤、群組和控制項的名稱。

     如需控制項識別碼清單，請參閱 [office 2010 說明檔： office 流暢的使用者介面控制項識別碼](https://www.microsoft.com/download/details.aspx?id=6627)。

5. 從 [**工具箱**] 的 [ **Office 功能區控制項**] 索引標籤，將 [群組] 拖曳到索引標籤。

    > [!NOTE]
    > 內建群組不會顯示在設計工具中。 因此，判斷您是否正在使用內建索引標籤的唯一方式，就是檢查索引標籤的 [ **ControlId** ] 屬性。

### <a name="to-position-groups-on-a-built-in-tab"></a>將群組放置在內建索引標籤

1. 在功能區設計工具中，選取自訂群組。

2. 在 [ **屬性** ] 視窗中，展開 [ **Position** ] 屬性。

3. 將 **positiontype]** 屬性設定為適當的值：

    - **BeforeOfficeId** 會將群組放置在指定的內建組之前。

    - **AfterOfficeId** 會將群組放置在指定的內建組之後。

4. 將 **OfficeId** 屬性設定為內建組的控制項識別碼。

     如需控制項識別碼清單，請參閱 [office 2010 說明檔： office 流暢的使用者介面控制項識別碼](https://www.microsoft.com/download/details.aspx?id=6627)。

## <a name="see-also"></a>另請參閱
- [功能區總覽](../vsto/ribbon-overview.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [如何：變更功能區上的索引標籤位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)
