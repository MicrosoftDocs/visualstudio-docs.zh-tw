---
title: Creating an Extension with 工具視窗 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5a38c9912be87c94c79076675b5db25663fb5f0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345438"
---
# <a name="create-an-extension-with-a-tool-window"></a>建立工具視窗的延伸模組

在此程序中，了解如何使用 VSIX 專案範本並**自訂工具視窗**建立工具視窗的延伸模組的項目範本。

## <a name="prerequisites"></a>必要條件

 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-tool-window"></a>建立工具視窗

1. 建立 VSIX 專案，名為**FirstWindow**。 您可以找到在 VSIX 專案範本**新的專案**藉由搜尋 「 vsix 」 的對話方塊。

2. 當專案開啟時，新增名為的工具視窗項目範本**MyWindow**。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** > **新項目**。 在 **加入新項目**對話方塊中，移至**Visual C#**  > **擴充性**，然後選取**自訂工具視窗**。 在 **名稱**在視窗底部的欄位、 變更工具視窗的檔案名稱，以*MyWindow.cs*。

3. 建置此專案並開始偵錯。

   Visual Studio 的實驗執行個體隨即出現。 如需詳細的實驗執行個體的詳細資訊，請參閱[實驗的執行個體](../extensibility/the-experimental-instance.md)。

4. 在實驗執行個體中，移至**檢視** > **其他 Windows**。

   您應該會看到的功能表項目**MyWindow**。 按一下它。

   您應該會看到工具視窗的標題**MyWindow**和一個按鈕，指出**Click Me ！。**