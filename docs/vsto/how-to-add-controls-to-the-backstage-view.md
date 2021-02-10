---
title: '如何：將控制項加入至 Backstage 檢視 '
description: 瞭解如何使用功能區設計工具，將控制項加入在您按一下 [檔案] 索引標籤時開啟的功能表中。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 830ecea036ee972321d98994ab36924e0c61a09b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954263"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>如何：將控制項加入至 Backstage 檢視
  您可以使用功能區設計工具，將控制項加入至按一下 [檔案] 索引標籤時 **開啟的功能表** 。當您執行應用程式時，您新增 **至 [檔案** ] 索引標籤的控制項會出現一個名為 [ **增益集**] 的群組。

 您無法使用 Visual Studio 中的功能區設計工具，將控制項放在內建控制項之前或之後。 內建控制項是在 Backstage view 中已顯示的控制項。 如果您想要在內建控制項之前或之後放置控制項，您必須使用功能區 XML。 如需 **功能區 (XML)** 的詳細資訊，請參閱 [功能區 xml](../vsto/ribbon-xml.md)。 如需自訂 Backstage 檢視的詳細資訊，請參閱 [適用于開發人員的 office 2010 Backstage 檢視簡介](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) 和 [自訂開發人員適用的 office 2010 backstage 視圖](/previous-versions/office/developer/office-2010/ee815851(v=office.14))。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>將控制項加入至 Backstage 檢視

1. 在設計檢視中開啟功能區專案。

     如需如何將 **功能區 (視覺化設計工具)** 專案加入至專案的詳細資訊，請參閱 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。

2. 在功能區設計工具中，按一下 [ **檔案] 索引** 標籤。

     功能表設計工具隨即出現。 這個設計介面不包含任何控制項。

3. 從 [工具箱] 的 [ **Office 功能區控制項** ] 索引標籤，將下列任何控制項拖曳至功能表設計 **工具**：

    - 按鈕

    - 核取方塊

    - 主機庫

    - 功能表

    - Separator

    - SplitButton

    - ToggleButton

4. 拖曳控制項，將它們移至功能表上的新位置。

## <a name="see-also"></a>另請參閱
- [功能區總覽](../vsto/ribbon-overview.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
