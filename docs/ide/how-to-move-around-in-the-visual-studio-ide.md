---
title: 如何在 IDE 中四處移動
description: 瞭解如何以數種不同的方式，將 Visual Studio IDE 中的視窗移至視窗，以及將檔案移至檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 384a6252ef17709970f6e902dfdf83a157b0460a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968043"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>如何：在 Visual Studio IDE 中四處移動

整合式開發環境 (IDE) 經過設計，可讓您使用數種不同方式，執行視窗至視窗以及檔案至檔案之間的移動 (根據您的喜好或專案需求而定)。 您可選擇在編輯器中循環瀏覽開啟的檔案，或是在 IDE 中循環瀏覽所有使用中的工具視窗。 您亦可在編輯器中直接切換至任何開啟的檔案，而忽略上次存取檔案的順序。 這些功能可協助您提升使用 IDE 工作時的生產力。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與本文中描述的有所不同。 撰寫本文時會考慮到 [一般] 設定。 若要變更您的設定 (例如變更為 [一般] 或 [Visual C++] 設定)，請選擇 [工具] > [匯入和匯出設定]，然後選擇 [重設所有設定]。

## <a name="keyboard-shortcuts"></a>鍵盤快速鍵

在 Visual Studio 中幾乎所有功能表命令皆具有鍵盤快速鍵。 您亦可建立專屬的自訂快速鍵。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

## <a name="navigate-among-files-in-the-editor"></a>在編輯器中的檔案之間巡覽

您可以使用數種方法，在編輯器中開啟的檔案之間移動。 您可根據存取的順序來移動所有檔案，使用「IDE 瀏覽器」快速尋找任何目前開啟的檔案，或是將我的最愛檔案鎖定至索引標籤以一律顯示該檔案。

根據存取順序，在編輯器中使用「向後巡覽」與「向前巡覽」方式來循環巡覽開啟的檔案，其與在 Microsoft Internet Explorer 中使用 [上一頁] 和 [下一頁] 檢視記錄非常近似。

### <a name="to-move-through-open-files-in-order-of-use"></a>依使用順序移動開啟的檔案

- 若要以最近觸及的順序啟動開啟的檔，請按下 **Ctrl** + **-** (連字號) 。

- 若要以相反順序啟動開啟的檔，請按下 **Ctrl** + **Shift** + **-** (連字號) 。

    > [!NOTE]
    > [向後巡覽] 和 [向前巡覽] 位於 [檢視] 功能表中。

您亦可使用 [IDE 瀏覽器]、編輯器的 [使用中的檔案] 清單或 [Windows] 對話方塊，切換至編輯器中已開啟的特定檔案而忽略上次存取檔案的時間。

[IDE 瀏覽器] 運作方式十分類似 Windows 應用程式切換器。 其僅可使用快速鍵來存取，而無法透過功能表使用。 您可使用兩個命令存取 [IDE 瀏覽器]\(如下所示)，以依據所需的循環瀏覽順序，循環瀏覽檔案。

![Visual Studio IDE 導覽器](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` 可讓您移至最近存取的檔案，並`Window.NextDocumentWindowNav`可讓您依相反順序移動。 [一般開發設定] 會將 **Shift**+**Alt**+**F7** 指派至 `Window.PreviousDocumentWindowNav`，並將 **Alt**+**F7** 指派至 `Window.NextDocumentWindowNav`。

> [!NOTE]
> 若您使用的設定組合尚未將快速鍵組合指派至此命令，您可使用 [選項] 對話方塊的 [鍵盤] 頁面，指派專屬的自訂命令。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

### <a name="to-switch-to-specific-files-in-the-editor"></a>切換至編輯器中的特定檔案

- 按下 **Ctrl** + **tab** 以顯示 **IDE 導覽器**。 按住 **Ctrl** 鍵並重複按下 **tab** 鍵，直到您選取想要切換的檔案為止。

    > [!TIP]
    > 若要反轉瀏覽 [使用中的檔案] 清單的順序，請按住 **Ctrl**+**Shift** 鍵並按 **Tab**。

    \- 或 -

- 在編輯器的右上角，選擇 [使用中的檔案] 按鈕，然後從清單中選取要切換的檔案。

    \- 或 -

- 在功能表列上，選擇 [**視窗視窗]**  >  ****。

- 在清單中，選取您想要檢視的檔案，然後選擇 [啟動]。

## <a name="navigate-among-tool-windows-in-the-ide"></a>在 IDE 中的各個工具視窗之間巡覽

[IDE 瀏覽器] 可讓您循環瀏覽已在 IDE 中開啟的工具視窗。 您可使用兩個命令存取 [IDE 瀏覽器]，以依據所需的循環瀏覽順序，循環瀏覽檔案。 `Window.PreviousToolWindowNav` 可讓您移至最近存取的檔案，並`Window.NextToolWindowNav`可讓您依相反順序移動。 [一般開發設定] 會將 **Shift**+**Alt**+**F7** 指派至 `Window.PreviousDocumentWindowNav`，並將 **Alt**+**F7** 指派至 `Window.NextDocumentWindowNav`。

> [!NOTE]
> 若您使用的設定組合尚未將快速鍵組合指派至此命令，您可使用 [選項] 對話方塊的 [鍵盤] 頁面，指派專屬的自訂命令。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>切換至 IDE 中的特定工具視窗

- 按 **Alt** + **F7** 以顯示 **IDE 導覽器**。 按住 **Alt** 鍵並重複按下 **F7** 鍵，直到您選取想要切換的視窗為止。

    > [!TIP]
    > 若要反轉瀏覽 [使用中工具視窗] 清單的順序，請按住 **Shift**+**Alt** 鍵並按 **F7**。

## <a name="see-also"></a>另請參閱

- [自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)
- [預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md)
