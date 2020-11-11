---
title: 建立新的專案和方案
description: 本文描述如何在 Visual Studio for Mac 中建立專案和方案
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 7ee9b23f9ede12a353f6c6fdc0f578d7f78a772c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493290"
---
# <a name="create-a-new-project"></a>建立新的專案

## <a name="opening-the-project-creation-dialog"></a>開啟專案建立對話方塊

有幾種方式可在 Visual Studio for Mac 中建立新的專案。 當您第一次開啟 Visual Studio for Mac 時，會顯示 [開始] 視窗。 您可以從這裡選擇 [ **新增** ]，這會帶您前往專案建立畫面。

> [!TIP]
> 此外，在 [開始] 視窗中，您也可以開啟和搜尋最近使用的專案和方案。 您也可以移至功能表列並選擇 [檔案] > [最近使用的解決方案]

![具有建立新專案的 [開始] 視窗](media/first-run-project.png)

如果 Visual Studio for Mac 已經開啟並載入解決方案，您可以移至功能表列並選擇 [檔案] > [新增解決方案] 來建立新的解決方案。 以此方式建立新的解決方案會關閉已載入的方案。

## <a name="creating-a-new-project"></a>建立新專案

[新增專案] 對話方塊預設會顯示您最近使用的範本，並依「最近用過的順序」排序。

如果您不想要使用最近用過的範本，您可以從對話方塊左側的類別中選擇。 每個類別都包含數個專案範本供您選擇。 按一下專案類型可讓您在畫面右側查看描述。

![新增專案畫面](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>設定您的新專案

在您選擇專案範本之後，後續畫面將會引導您完成設定該專案所需的任何設定步驟；這些步驟可能會因專案類型而有所不同。

所有專案都需要新的專案，以及儲存檔案的位置。 如果該專案是新解決方案的一部分，而不是要將它加入至現有的解決方案，則也會需要提供解決方案名稱。

在此階段您也可以選擇設定 Git 原始檔控制選項。 下圖是某個 .NET Core 專案最終設定步驟的範例：

![設定新專案](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>將其他專案新增至解決方案

您可以用滑鼠右鍵按一下 [ **方案] 視窗** 中的方案，然後選擇 [ **> 加入新專案** ] 或 [加入 **> 加入現有專案** ]，將其他專案新增至方案。

加入新專案將會引導您完成專案建立程序，如[設定您的新專案](#configuring-your-new-project)中所示。

選擇加入現有專案將可讓您瀏覽電腦上的現有專案，並將它加入至解決方案。

## <a name="see-also"></a>請參閱

- [建立方案和專案 (Windows 上的 Visual Studio)](/visualstudio/ide/creating-solutions-and-projects)
