---
title: 如何：開始自訂功能區
description: 瞭解若要自訂 Microsoft Office 應用程式的功能區，請將功能區 (視覺化設計工具) 或功能區 (XML) 專案加入 Office 專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d82d059166b9efbb80ed6ce4cffcbb973235b01b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953912"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>如何：開始自訂功能區
  若要自訂 Microsoft Office 應用程式的功能區，請將 **功能區 (視覺化設計工具)** 或 **功能區 (XML)** 專案加入 Office 專案。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>將功能區加入至專案

1. 在 [ **專案** ] 功能表上，按一下 [ **加入新專案**]。

2. 在 [ **加入新專案** ] 對話方塊中，選取 [ **功能區 (的視覺化設計工具)** 或 **功能區 (XML)**。 如需這些範本的詳細資訊，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

3. 在 [ **名稱** ] 方塊中，輸入功能區專案的名稱。

    名稱不可包含以下字元：

   - 井字號 (#)

   - 百分比 (%)

   - 連字號 (&)

   - 星號 (*)

   - 分隔號 (|)

   - 反斜線 (\\)

   - 冒號 (:)

   - 雙引號 (")

   - 小於 (\<)

   - 大於 (>)

   - 問號 (?)

   - 斜線 (/)

   - 開頭或尾端空白 (' ')

   - 保留給 Windows 或 DOS 的名稱，例如 ( "nul"、"aux"、"con"、"com1"、"lpt1" 等等) 

4. 按一下 [確定]  。

   功能區專案隨即出現在 **方案總管** 中。 如需後續步驟的詳細資訊，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

## <a name="see-also"></a>另請參閱
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
