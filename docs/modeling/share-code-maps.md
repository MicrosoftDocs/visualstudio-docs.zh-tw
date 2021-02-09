---
title: 匯出和儲存 code map
description: 瞭解如何將 code map 儲存為 Visual Studio 專案的一部分、映射或 XPS 檔案。
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 324f8fe7ee34f469d31ad1ce6cf6bd25ab97f225
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899822"
---
# <a name="share-code-maps"></a>共用 Code Map

您可以將 code map 儲存為 Visual Studio 專案的一部分、映射或 XPS 檔案。

## <a name="share-a-code-map-with-other-visual-studio-users"></a>與其他 Visual Studio 使用者共用 code map

使用 [檔案]  功能表以儲存對應。

-或-

若要將地圖儲存為特定專案的一部分，請在 [對應] 工具列上選擇 [**共用** Move]，然後  >  **\<CodeMapName>** 選擇您要儲存對應的專案。

![將對應移至其他專案](../modeling/media/codemapsmovemapmenu.png)

Visual Studio 會將對應儲存為 *.dgml* 檔案，您可以與 Visual Studio Enterprise 和 Visual Studio Professional 的其他使用者共用該檔案。

> [!NOTE]
> 在您與 Visual Studio Professional 使用者共用對應之前，請展開所有群組，顯示隱藏的節點和跨群組連結，並擷取任何您希望其他人在對應看到的已刪除節點。 否則，其他使用者就無法看到這些項目。
>
> 若您儲存的對應是位於模型專案中，或此對應是從模型專案複製到另一個位置，就會發生下列錯誤：
>
> 「無法將 *fileName* 儲存在專案目錄外。 不支援連結項目。」
>
> Visual Studio 顯示錯誤，不過還是會建立儲存的版本。 若要避免此錯誤，請將對應建立在模型專案之外。 然後您可以將它儲存到您想要的位置。 只將檔案複製到方案中的另一個位置然後再嘗試儲存，這種做法不會有用。

## <a name="export-a-code-map-as-an-image"></a>將 code map 匯出為影像

當您將 code map 匯出為影像時，您可以將它複製到其他應用程式，例如 Microsoft Word 或 PowerPoint。

1. 在 code map 工具列上，選擇[  >  **以影像形式共用電子郵件**] 或 [**複製影像**]。

2. 將影像貼入另一個應用程式中。

## <a name="export-the-map-as-an-xps-file"></a>將對應匯出為 XPS 檔案

當您將 code map 匯出為 XPS 檔案時，您可以在 XML 或 XAML 檢視器（例如 Internet Explorer）中看到它。

1. 在 code map 工具列上，選擇[  >  **以便攜 xps 形式共用電子郵件**] 或 [**另存為便攜 xps**]。

2. 瀏覽至儲存檔案的位置。

3. 為 Code Map 命名。 確定 [檔 **類型** ] 方塊設定為 [xps 檔案 **(.xps \*)**。 選擇 [儲存]。

## <a name="see-also"></a>另請參閱

- [使用 code map 對應相依性](../modeling/map-dependencies-across-your-solutions.md)
