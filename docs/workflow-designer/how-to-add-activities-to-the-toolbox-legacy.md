---
title: 工作流程設計工具-如何： 將活動新增至工具箱 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969423"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>HOW TO：將活動新增至工具箱 (舊版)

當建置在工作流程方案中使用舊版 Windows 工作流程設計工具的目標.NET Framework 3.5 版或 WinFX，可以自訂活動新增至工作流程專案，並在其設計工具放置於**工具箱**的輕鬆存取。 您也可以直接將活動新增**工具箱**從動態連結程式庫 (DLL)。

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>若要將活動從 DLL 新增至工具箱

1.  以滑鼠右鍵按一下底下的 工具箱 視窗介面**Windows 工作流程**，然後按一下 **選擇項目**。

2.  在**選擇工具箱項目**對話方塊中，按一下  **System.Activities 元件**索引標籤，然後再按一下**瀏覽**從視窗的右下角。

3.  檔案目錄，包含要加入的自訂活動的實作，從選取的 DLL**工具箱**，然後按一下 **開啟**。

4.  按一下**確定**完成新增活動至工具箱。

## <a name="see-also"></a>另請參閱

- [使用舊版活動設計工具](../workflow-designer/using-the-legacy-activity-designer.md)
- [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)