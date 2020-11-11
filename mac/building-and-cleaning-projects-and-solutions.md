---
title: 建置和清除專案與方案
description: 本文說明如何在 Visual Studio for Mac 中建置專案
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.topic: how-to
ms.openlocfilehash: de6be4b509eff8a013f7367614e0016f810b3657
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492694"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>建置和清除專案與方案

遵循本文中的步驟，以瞭解如何建立、重建或清除方案中的所有或部分專案。

> [!NOTE]
> 本主題適用於 Visual Studio for Mac。 針對 Windows 上的 Visual Studio，請參閱 [Visual Studio 中的組建和清除專案和方案](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)。

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>建置、重建或清除整個方案

1. 在 [ **方案] 視窗** 中選取方案節點：

    ![選取方案節點](media/compiling-and-building-image1.png)

2. 選取功能表列中的 [ **組建** ] 功能表，然後選擇下列其中一個選項：

    ![選取建置所有功能表項目](media/compiling-and-building-image2.png)

    * 選擇 [ **全部組建** ]，在專案中編譯自最新組建之後變更的檔案和元件。

    * 選擇 [ **全部重建** ] 以「清除」方案，然後建立所有專案檔和元件。

    * 選擇 [ **全部清除** ] 以刪除任何中繼和輸出檔案。 只留下專案和元件檔案，即可建立新的中繼檔和輸出檔執行個體。

## <a name="to-build-or-rebuild-a-single-project"></a>建立或重建單一專案

1. 在 [ **方案] 視窗** 中選取專案。

2. 從功能表列選取 [ **組建** ] 功能表。

3. 選擇 [專案名稱]、[建立]、[專案名稱] 或 [清除 [專案名稱]。

## <a name="to-stop-a-build"></a>停止建置

若要停止組建，請使用下列其中一個選項：

* 在 [狀態] 區域中按紅色方塊：

    ![按紅色方塊以停止建置](media/compiling-and-building-image3.png)

* 使用 [ **組建** ] 功能表中的 [ **停止** ] 專案。

* 按下 **Cmd + Shift + Return** 。

## <a name="see-also"></a>請參閱

- [建置和清除專案與方案 (Windows 上的 Visual Studio)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)