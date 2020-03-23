---
title: 建置和清除專案與方案
description: 本文說明如何在 Visual Studio for Mac 中建置專案
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128448"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>建置和清除專案與方案

請按照本文中的步驟瞭解如何構建、重建或清理解決方案中的所有或某些專案。

> [!NOTE]
> 本主題適用於 Visual Studio for Mac。 有關 Windows 上的視覺化工作室，請參閱[在視覺化工作室中構建和清理專案和解決方案](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)。

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>建置、重建或清除整個方案

1. 在**解決方案墊中選擇解決方案**節點：

    ![選取方案節點](media/compiling-and-building-image1.png)

2. 選擇功能表列中的 **"生成**"功能表，然後選擇以下選項之一：

    ![選取建置所有功能表項目](media/compiling-and-building-image2.png)

    * 選擇 **"全部生成"** 可編譯專案中自最近生成以來已更改的檔和元件。

    * 選擇 **"全部重建**"以"清理"解決方案，然後生成所有專案檔案和元件。

    * 選擇 **"全部清潔"** 可刪除任何中間檔和輸出檔案。 只留下專案和元件檔案，即可建立新的中繼檔和輸出檔執行個體。

## <a name="to-build-or-rebuild-a-single-project"></a>建立或重建單一專案

1. 在**解決方案墊**中選擇專案。

2. 從功能表列中選擇 **"生成**"功能表。

3. 選擇生成[專案名稱]、重建[專案名稱]或"清理[專案名稱]"。

## <a name="to-stop-a-build"></a>停止建置

要停止生成，請使用以下選項之一：

* 按狀態區域中的紅色方塊：

    ![按紅色方塊以停止建置](media/compiling-and-building-image3.png)

* 使用 **"生成**"功能表中的 **"停止"** 項。

* 按**Cmd_Shift_返回**。

## <a name="see-also"></a>另請參閱

- [建置和清除專案與方案 (Windows 上的 Visual Studio)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)