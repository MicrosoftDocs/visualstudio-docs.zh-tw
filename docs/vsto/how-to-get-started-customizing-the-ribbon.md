---
title: HOW TO：開始自訂功能區
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 14c4ff1e8bf443351f835d74d44b49bbb61e0321
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640112"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>HOW TO：開始自訂功能區
  若要自訂 Microsoft Office 應用程式的功能區，請新增**功能區 （視覺化設計工具）** 或是**功能區 (XML)** 在 Office 專案的項目。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>將功能區加入至專案

1. 在 **專案**功能表上，按一下**加入新項目**。

2. 在 **加入新項目**對話方塊中，選取**功能區 （視覺化設計工具）** 或是**功能區 (XML)**。 如需有關這些範本的詳細資訊，請參閱 <<c0> [ 功能區概觀](../vsto/ribbon-overview.md)。

3. 在 **名稱**方塊中，輸入 功能區項目的名稱。

    名稱不可包含下列字元：

   -   井字號 （#）

   -   百分比 （%）

   -   連字號 (&)

   -   星號 (*)

   -   分隔號 (|)

   -   反斜線 (\\)

   -   冒號 （:）

   -   雙引號 (")

   -   小於 (\<)

   -   大於 (>)

   -   問號 (?)

   -   反斜線 （/）

   -   開頭或尾端空格 (' ')

   -   保留給 Windows 或 DOS，例如 （「 nul 」、 「 aux 」、 「 con 」、 「 com1 」、 「 lpt1 」 等等） 的名稱

4. 按一下 [確定] 。

   功能區項目會出現在**方案總管 中**。 下一個步驟的詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。

## <a name="see-also"></a>另請參閱
- [在執行階段功能區的存取](../vsto/accessing-the-ribbon-at-run-time.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
