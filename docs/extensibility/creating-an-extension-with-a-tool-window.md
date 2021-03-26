---
title: 使用工具視窗建立延伸模組 |Microsoft Docs
description: 瞭解如何使用 VSIX 專案範本和自訂工具視窗專案範本，建立具有工具視窗的延伸模組。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f956aa520bca79a84fe203093c225cfeb8389ba1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089195"
---
# <a name="create-an-extension-with-a-tool-window"></a>使用工具視窗建立擴充功能

在此程式中，您將瞭解如何使用 VSIX 專案範本和 **自訂工具視窗** 專案範本，以使用工具視窗建立延伸模組。

## <a name="prerequisites"></a>必要條件

 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-tool-window"></a>建立工具視窗

1. 建立名為 **FirstWindow** 的 VSIX 專案。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中找到 VSIX 專案範本。

2. 當專案開啟時，加入名為 **MyWindow** 的工具視窗專案範本。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 **Visual c #** 擴充性，  >  然後選取 [**自訂工具視窗]**。 在視窗底部的 [ **名稱** ] 欄位中，將工具視窗的 [檔案名] 變更為 *MyWindow .cs*。

3. 建置此專案並開始偵錯。

   Visual Studio 的實驗實例隨即出現。 如需實驗實例的詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。

4. 在實驗性實例中，移至 [**查看**  >  **其他視窗**]。

   您應該會看到 **MyWindow** 的功能表項目。 按一下此按鈕。

   您應該會看到一個具有標題 **MyWindow** 的工具視窗，以及一個指出 **Click Me！** 的按鈕。
