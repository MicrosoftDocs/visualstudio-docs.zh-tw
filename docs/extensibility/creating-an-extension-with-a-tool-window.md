---
title: 使用工具視窗建立延伸 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739548"
---
# <a name="create-an-extension-with-a-tool-window"></a>使用工具視窗建立延伸

在此過程中,您將瞭解如何使用 VSIX 專案範本和**自訂工具視窗**項樣本使用工具視窗創建擴展。

## <a name="prerequisites"></a>Prerequisites

 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-tool-window"></a>建立工具視窗

1. 創建名為**FirstWindow 的**VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 打開專案時,添加名為**MyWindow**的工具視窗項範本。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在 **「新增新項目」** 對話方塊中,轉到**視覺化 C#** > **可擴充性**並選擇 **「自訂工具視窗**」 。。 在視窗底部的 **「 名稱」** 欄位中,將工具視窗檔名變更為*MyWindow.cs*。

3. 建置此專案並開始偵錯。

   視覺工作室的實驗實例出現。 有關實驗實例的詳細資訊,請參閱[實驗實例](../extensibility/the-experimental-instance.md)。

4. 在實驗例中,轉到**檢視** > **其他 Windows**。

   您應該會看到 **「我的視窗」** 的功能表項。 按一下此按鈕。

   您應該會看到一個工具視窗,標題為 **"我的視窗",** 並顯示一個按鈕,上面寫著 **"按下我!"**
