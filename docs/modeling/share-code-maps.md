---
title: 匯出並儲存程式碼對應
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: abfe8d6160d023a99e9a49480baada9acb0c8243
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268373"
---
# <a name="share-code-maps"></a>共用 Code Map

Visual Studio 專案中做為映像，或為 XPS 檔案，您可以儲存程式碼對應。

## <a name="share-a-code-map-with-other-visual-studio-users"></a>與其他 Visual Studio 使用者共用的程式碼對應

使用 [檔案]  功能表以儲存對應。

-或-

若要為特定的專案的一部分儲存對應，對應圖工具列上，選擇 **共用** > **移動\<CodeMapName >.dgml 到**，然後選擇您要儲存專案對應。

![將對應移至其他專案](../modeling/media/codemapsmovemapmenu.png)

Visual Studio 會儲存為地圖 *.dgml*可以與其他 Visual Studio Enterprise 和 Visual Studio Professional 的使用者共用的檔案。

> [!NOTE]
> 在您與 Visual Studio Professional 使用者共用對應之前，請展開所有群組，顯示隱藏的節點和跨群組連結，並擷取任何您希望其他人在對應看到的已刪除節點。 否則，其他使用者就無法看到這些項目。
>
> 若您儲存的對應是位於模型專案中，或此對應是從模型專案複製到另一個位置，就會發生下列錯誤：
>
> 「無法將 *fileName* 儲存在專案目錄外。 不支援連結項目。」
>
> Visual Studio 顯示錯誤，不過還是會建立儲存的版本。 若要避免此錯誤，請將對應建立在模型專案之外。 然後您可以將它儲存到您想要的位置。 只將檔案複製到方案中的另一個位置然後再嘗試儲存，這種做法不會有用。

## <a name="export-a-code-map-as-an-image"></a>匯出為影像的 code map

當您匯出為影像的 code map 時，您可以將它複製到其他應用程式，例如 Microsoft Word 或 PowerPoint。

1. 在 code map 工具列上，選擇 **共用** > **以影像傳送電子郵件**或**複製影像**。

2. 將影像貼入另一個應用程式中。

## <a name="export-the-map-as-an-xps-file"></a>將對應匯出為 XPS 檔案

當您匯出為 XPS 檔案的 code map 時，您可以在像是 Internet Explorer 的 XML 或 XAML 檢視器中看到它。

1. 在 code map 工具列上，選擇 **共用** > **可攜式 XPS 做為傳送電子郵件**或**另存為可攜式 XPS**。

2. 瀏覽至儲存檔案的位置。

3. 為 Code Map 命名。 請確定**存檔類型**方塊會設為**XPS 檔 (\*.xps)**。 選擇 [儲存] 。

## <a name="see-also"></a>另請參閱

- [使用 code map 中對應的相依性](../modeling/map-dependencies-across-your-solutions.md)